SCB
===

File List
---------

* :file:`.\Game\Data\Levels\Level_01.scb`
* :file:`.\Game\Data\Levels\Level_02.scb`
* :file:`.\Game\Data\Levels\Level_03.scb`
* :file:`.\Game\Data\Levels\Level_04.scb`
* :file:`.\Game\Data\Levels\Level_05.scb`
* :file:`.\Game\Data\Levels\Level_06.scb`
* :file:`.\Game\Data\Levels\Level_07.scb`
* :file:`.\Game\Data\Levels\Level_08.scb`
* :file:`.\Game\Data\Levels\Level_09.scb`
* :file:`.\Game\Data\Levels\Level_10.scb`
* :file:`.\Game\Data\Levels\Level_11.scb`
* :file:`.\Game\Data\Levels\Level_12.scb`
* :file:`.\Game\Data\Levels\Level_13.scb`
* :file:`.\Game\Data\Levels\Level_14.scb`
* :file:`.\Game\Data\Levels\Level_15.scb`
* :file:`.\Game\Data\Levels\Level_16.scb`
* :file:`.\Game\Data\Levels\Level_17.scb`
* :file:`.\Game\Data\Levels\Level_18.scb`
* :file:`.\Game\Data\Levels\Level_19.scb`
* :file:`.\Game\Data\Levels\Level_20.scb`
* :file:`.\Game\Data\Levels\Level_21.scb`
* :file:`.\Game\Data\Levels\Level_22.scb`
* :file:`.\Game\Data\Levels\Level_23.scb`
* :file:`.\Game\Data\Levels\Level_24.scb`
* :file:`.\Game\Data\Levels\Level_25.scb`


Specifications
--------------

.. code-block:: text

    struct file_header
    for (file_header.nbOfClasses) {
        struct class_header
        for (class_header.nboffunctions {
            struct function_header
        }
        data bytecode
    }

sscanf format for parsing all header.

File Header
^^^^^^^^^^^

.. code-block:: text

    "version %f, debug %d\n"
    "nbOfClasses %d\n"

* Version must be 1.0
* debug are set to 0 (FALSE)

Class Header
^^^^^^^^^^^^

.. code-block:: text

    "fileName %1023s , className %1023s\n"
    "nbOfVariables %d, sizeOfVariables %d\n"
    "nbOfFunctions %d\n"
    // Here we have all the functions header
    "nbOfQuads %d\n"
    // Here we have all the bytecode of every function belonging to the class

Function Header
^^^^^^^^^^^^^^^

.. code-block:: text

    "functionName %1023s , address %d, nbOfParams %d, sizeOfRetVal %d, sizeOfParams %d\n"
    "functionParameters\n"
    "\n"
    " sizeOfVolatile %d, sizeOfTempor %d\n"

ByteCode
^^^^^^^^

In the game they call that "quad".

bytecode in file are stored in this way:

.. code-block:: text

    + 0x00:    OPCODE    [BYTE]
    + 0x01:    OPERANDS  [QWORD]
    + 0x09:    PADDING   [BYTE]

Virtual Machine
---------------

IDA func: sub_618050

Operand flag
^^^^^^^^^^^^

* 0x0000: UNKNOW ?
* 0x4000: CLASS ATTRIBUTES (class_var)
* 0x8000: VOLATILE VARIABLE (vol_var)
* 0xC000: TEMPORARY VARIABLE (temp_var)

ByteCode
^^^^^^^^

.. warning::

    /!\ bytecode in game memory are not stored in the same way as in the file /!\

.. code-block:: text

    + 0x00:    OPCODE    [DWORD]
    + 0x04:    OPERANDS  [QWORD]

Opcode
^^^^^^

Max Opcode: 0x2C (44)

0x00
""""

* Opcode: 0x00 (0)
* Nb of operands: 0

.. code-block:: text

    "VMCore::Empty: Operation not allowed.\n"

This opcode is not allowed and will set the VM PC to 0xFFFFFFFF

0x01
""""

* Opcode: 0x01 (1)
* Nb of operands: 0

This opcode do nothing, it will only increment VM PC by 1

0x02
""""

* Opcode: 0x02 (2)
* Nb of operands: 1
* Operand 0x01: Displacement (Size: WORD)

Copy variable from Function arguments / Volatile variable / temporary variable to field 0x0C of VM

0x03
""""

* Opcode: 0x03 (3)
* Nb of operands: 2
* Operand 0x01: SIZE OF VOLATILE VARIABLE (Size: WORD)
* Operand 0x02: SIZE OF TEMPORARY VARIABLE (Size: WORD)

Entry point for every function in order to allocate enough place for the different variables

0x04
""""

* Opcode: 0x04 (4)
* Nb of operands: 0

.. code-block:: text

    "VMCore::EndFunction: Operation not allowed (add a Return !!!).\n"

This opcode will increment VM PC by 1

0x05
""""

* Opcode: 0x05 (5)
* Nb of operands: 1
* Operand 0x01: Address function (Size: DWORD)

TODO: Looks like a CALL to another function of the current class

0x06
""""

* Opcode: 0x06 (6)

TODO

0x07
""""

* Opcode: 0x07 (7)

TODO

0x08
""""

* Opcode: 0x08 (8)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: DWORD)

.. code-block:: text

    MOV op1, op2

0x09
""""

* Opcode: 0x09 (9)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: DWORD)

.. code-block:: text

    MOV op2, op1


0x0A
""""

* Opcode: 0x0A (10)
* Nb of operands: 1
* Operand 0x01: Displacement (Size: WORD)

TODO

0x0B
""""

* Opcode: 0x0B (11)
* Nb of operands: 1
* Operand 0x01: Displacement (Size: WORD)

Push argument for external CALL

.. code-block:: text

    PUSH op1

0x0C
""""

* Opcode: 0x0C (12)
* Nb of operands: 0x01
* Operand 0x01: Index (Size: Immediate32)

This opcode will call a function stored in a table of address function at dword_6938A4. (see [[Script Function]])

.. code-block:: text

    .text:00613CB3 8B 46 40                mov     eax, [esi+40h]       // [esi+CVMScript.VM_pc]     ; Actual PC
    .text:00613CB6 8B 50 04                mov     edx, [eax+4]         // Operand 1
    .text:00613CB9 A1 A4 38 69 00          mov     eax, dword_6938A4    // Table of function (table initialized by sub_5E3BF0: size 0x320 (800) == 200 functions!)
    .text:00613CBE 57                      push    edi
    .text:00613CBF 8B 7E 3C                mov     edi, [esi+3Ch]
    .text:00613CC2 8D 4E 48                lea     ecx, [esi+48h]        // [esi+CVMScript.field_48] ; Function arguments
    .text:00613CC5 FF 14 90                call    dword ptr [eax+edx*4] // Operand 1 is used as an index

.. code-block:: text

    CALL [Index]

0x0D
""""

* Opcode: 0x0D (13)
* Nb of operands: 1
* Operand 0x01: Displacement (Size: WORD)

Save return value from external function called before

0x0E
""""

* Opcode: 0x0E (14)
* Nb of operands: 1
* Operand 0x01: Address (Size: DWORD)

Jmp to desired address

.. code-block:: text

    JMP Imm32

0x0F
""""

* Opcode: 0x0F (15)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Address (Size: DWORD)

Conditional jump if value is TRUE.

.. code-block:: text

    TEST op1, op1 ; JZ Imm32


0x10
""""

* Opcode: 0x10 (16)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Address (Size: DWORD)

Conditional jump if value is FALSE.

.. code-block:: text

    TEST op1, op1 ; JNZ Imm32

0x11
""""

* Opcode: 0x11 (17)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)

mov from op2 to op1

.. code-block:: text

    mov op1, op2

0x12
""""

* Opcode: 0x12 (18)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)

mov from op2 to op1

.. code-block:: text

    mov op1, op2


TODO: check why same as 0x11

0x13
""""

* Opcode: 0x13 (19)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Immediate (Size: DWORD)

mov Immediate to op1

.. code-block:: text

    mov op1, Imm32

0x14
""""

* Opcode: 0x14 (20)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Immediate (Size: DWORD)

mov Immediate to op1

.. code-block:: text

    mov op1, Imm32


TODO: check why same as 0x13

0x15
""""

* Opcode: 0x15 (21)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)

.. code-block:: text

    sub op1, op2


0x16
""""

* Opcode: 0x16 (22)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)

.. code-block:: text

    sub (float)op1, (float)op2

0x17
""""

* Opcode: 0x17 (23)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, (float)op2


0x18
""""

* Opcode: 0x18 (24)
* Nb of operands: 2
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, (double)op2

0x19
""""

* Opcode: 0x19 (25)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 + op3)


0x1A
""""

* Opcode: 0x1A (26)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 - op3)


0x1B
""""

* Opcode: 0x1B (27)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 * op3)

0x1C
""""

* Opcode: 0x1C (28)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 / op3).. code-block:: text

0x1D
""""

* Opcode: 0x1D (29)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 + (float)op3)


0x1E
""""

* Opcode: 0x1E (30)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 - (float)op3)

0x1F
""""

* Opcode: 0x1F (31)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 * (float)op3)

0x20
""""

* Opcode: 0x20 (32)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 / (float)op3)

0x21
""""

* Opcode: 0x21 (33)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 <= op3)

0x22
""""

* Opcode: 0x22 (34)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 < op3)

0x23
""""

* Opcode: 0x23 (35)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 >= op3)

0x24
""""

* Opcode: 0x24 (36)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 > op3)

0x25
""""

* Opcode: 0x25 (37)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 != op3)

0x26
""""

* Opcode: 0x26 (38)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov op1, (op2 == op3)

0x27
""""

* Opcode: 0x27 (39)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 > (double)op3)

0x28
""""

* Opcode: 0x28 (40)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 >= (double)op3)


0x29
""""

* Opcode: 0x29 (41)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 < (double)op3)

0x2A
""""

* Opcode: 0x2A (42)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 <= (double)op3)


0x2B
""""

* Opcode: 0x2B (43)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 == (double)op3)


0x2C
""""

* Opcode: 0x2C (44)
* Nb of operands: 3
* Operand 0x01: Displacement (Size: WORD)
* Operand 0x02: Displacement (Size: WORD)
* Operand 0x03: Displacement (Size: WORD)

.. code-block:: text

    mov (float)op1, ((float)op2 != (double)op3)

