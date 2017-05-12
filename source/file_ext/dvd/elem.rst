ELEM
====

General
-------

...

IDA VA: 0x4ACD50

Specifications
--------------


File Header
^^^^^^^^^^^

.. code-block:: text

    +0x00:   VERSION    [DWORD]
    +0x04:   NB_ELEME   [WORD]

* Version must be equal to 0x1C

Type Object
^^^^^^^^^^^

.. warning::

    Those values are just gues!!

* 0x00: Character
* 0x01: Environment object (river, smoke, ...)
* 0x02: Object (Accessories, etc ... )

Elem Header
^^^^^^^^^^^

.. code-block:: text

    +0x00:   TYPE       [WORD]

There is 41 (0x29) different types. But some of them seems similar (are parsed in the same way).

Struct sub_492650
^^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00:    Struct DVFRelation [sizeof (Struct DVFRelation)]   // value = 0x1
    +0x00:    Struct sub_58B8C0 [sizeof (Struct sub_58B8C0)]   // value = 0x1
    +0x00:    UNK_BYTE_00   [BYTE]    // Related to Y coordinate
    +0x00:    UNK_BYTE_01   [BYTE]    // Related to X coordinate
    +0x00:    UNK_BYTE_02   [BYTE]    // Related to X coordinate

Struct sub_58AFF0
^^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00:    Struct DVFRelation [sizeof (Struct DVFRelation)]
    +0x00:    Struct sub_58B8C0 [sizeof (Struct sub_58B8C0)]

Struct DVFRelation
^^^^^^^^^^^^^^^^^^

* Information for relationship with [[DVF_File_Format|DVF]] file

.. code-block:: text

    +0x00                                                                   :     LENGTH_DVF_FILENAME   [WORD]
    +0x02                                                                   :     DVF_FILENAME          [BYTE] * LENGTH_DVF_FILENAME
    +0x02 + LENGTH_DVF_FILENAME                                             :     LENGTH_OBJECT_NAME    [WORD]
    +0x04 + LENGTH_DVF_FILENAME                                             :     OBJECT_NAME           [BYTE] * LENGTH_OBJECT_NAME
    if value == 0 or value == 2
    +0x04 + LENGTH_DVF_FILENAME + LENGTH_OBJECT_NAME                        :     ALT_PROFILE_PRESENT   [BYTE]
        if ALT_PROFILE_PRESENT == 1
    +0x05 + LENGTH_DVF_FILENAME + LENGTH_OBJECT_NAME                        :     LENGTH_DVF_FILENAME_2 [WORD]
    +0x07 + LENGTH_DVF_FILENAME + LENGTH_OBJECT_NAME                        :     UNK_BUF_NAME          [BYTE] * LENGTH_DVF_FILENAME_2
    +0x07 + LENGTH_DVF_FILENAME + LENGTH_OBJECT_NAME + LENGTH_DVF_FILENAME_2:     LENGTH_OBJECT_NAME_2  [WORD]
    +0x09 + LENGTH_DVF_FILENAME + LENGTH_OBJECT_NAME                        :     UNK_2_BUF_NAME        [BYTE] * LENGTH_OBJECT_NAME_2
        end
    end

* If ALT_PROFILE_PRESENT is set to TRUE, it will open an altprofile DVF file

Struct sub_58B8C0
^^^^^^^^^^^^^^^^^

if value == 0x01
""""""""""""""""

.. code-block:: text

    if value == 0x01
    +0x00:         UNK_WORD_00      [WORD]
    +0x02:         UNK_WORD_01      [WORD]
    +0x04:         HEIGHT           [WORD]   // from top to bottom
    end

Computed info come from the associated DVF fileinfo [[DVF_File_Format#Object|DVF object info]]:

.. code-block:: text

    POINT_X = UNK_WORD_00 + UNKNOWN0 (FROM DVF)
    POINT_Y = UNK_WORD_01 + UNKNOWN1 (FROM DVF) + HEIGHT


if value == 0x00
""""""""""""""""

.. code-block:: text

    if value == 0x00
    +0x00:         PATHFINDER_INDEX                [BYTE]
    +0x01:         UNK_WORD_01                     [WORD]   // Y TOP LEFT coordinate BOX ?
    +0x03:         UNK_WORD_02                     [WORD]   // X TOP LEFT coordinate BOX ?
    +0x05:         UNK_WORD_03                     [WORD]   // Y DOWN RIGHT coordinate BOX ?
    +0x07:         UNK_WORD_04                     [WORD]   // X TOP LEFT coordinate BOX ?
    +0x09:         PATHFINDER_ALTERNATE_INDEX      [BYTE]
    +0x0A:         UNK_WORD_05                     [WORD]   // Y TOP LEFT coordinate BOX ?
    +0x0C:         UNK_WORD_06                     [WORD]   // X TOP LEFT coordinate BOX ?
    +0x0E:         UNK_WORD_07                     [WORD]   // Y DOWN RIGHT coordinate BOX ?
    +0x10:         UNK_WORD_08                     [WORD]   // X TOP LEFT coordinate BOX ?
    +0x12:         UNK_WORD_09                     [WORD]
    +0x14:         UNK_WORD_10                     [WORD]
    +0x16:         UNK_WORD_11                     [WORD]
    +0x18:         UNK_WORD_12                     [WORD]
    +0x1A:         UNK_WORD_13                     [WORD]
    +0x1C:         UNK_BYTE_00                     [BYTE]
    +0x1D:         UNK_BYTE_01                     [BYTE]
    end

if value == 0x02
""""""""""""""""

.. code-block:: text

    if value == 0x02
    TODO
    end

Type 0x0001 || 0x0002 || 0x0003 || 0x0004 || 0x0005 || 0x0006
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Read method virtual address: 0x0048A7C0

.. code-block:: text

    +0x00:   Struct sub_58AFF0   [sizeof (Struct sub_58AFF0)] // value == 0x00
    +0x00:   UNK_WORD_00         [WORD]
    +0x00:   UNK_WORD_01         [WORD]

* 0x0001: John Cooper
* 0x0002: Doc Mc Coy
* 0x0003: Sam
* 0x0004: Kate O'Hara
* 0x0005: Pablo Sanchez
* 0x0006: Mia Jung

Type 0x0007 || 0x0210 || 0x0211 || 0x0212 || 0x0213 || 0x0214 || 0x0215
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* '''DVElementActorAnimal'''
* Read method virtual address: 0x00463E30

.. code-block:: text

    +0x00:   Struct sub_58AFF0   [sizeof (Struct sub_58AFF0)] // value == 0x00
    +0x00:   LENGTH_CLASSNAME    [WORD]
    +0x00:   CLASSNAME           [BYTE] * LENGTH_CLASSNAME
    +0x00:   IGNORED_WORD        [WORD]

Type 0x0101
^^^^^^^^^^^

* '''DVElementActorNPC'''
* Read method virtual address: 0x0047EAA0
* Second virtual method: 0x00438BA0

.. code-block:: text

    +0x00:   Struct sub_58AFF0   [sizeof (Struct sub_58AFF0)] // value == 0x00
    +0x00:   LENGTH_CLASSNAME    [WORD]
    +0x00:   CLASSNAME           [BYTE] * LENGTH_CLASSNAME
    +0x00:   UNK_DWORD_00        [DWORD]
    +0x00:   UNK_WORD_00         [WORD]
    +0x00:   UNK_BYTE_00         [BYTE]
    +0x00:   UNK_BYTE_01         [BYTE]
    +0x00:   UNK_WORD_01         [WORD]
    +0x00:   UNK_WORD_02         [WORD]

Type 0x0102
^^^^^^^^^^^

* '''DVElementActorNPC'''
* Read method virtual address: 0x0047EAA0
* Second virtual method: 0x00406760

.. code-block:: text

    +0x00:   Struct sub_58AFF0   [sizeof (Struct sub_58AFF0)] // value == 0x00
    +0x00:   LENGTH_CLASSNAME    [WORD]
    +0x00:   CLASSNAME           [BYTE] * LENGTH_CLASSNAME
    +0x00:   UNK_WORD_00         [WORD]
    +0x00:   UNK_BYTE_00         [BYTE]
    +0x00:   UNK_BYTE_01         [BYTE]
    +0x00:   UNK_WORD_01         [WORD]
    +0x00:   UNK_WORD_02         [WORD]

Type 0x0201
^^^^^^^^^^^

* '''DVElementActorHorse'''
* Read method virtual address: 0x00467DA0

.. code-block:: text

    +0x00:   Struct sub_58AFF0   [sizeof (Struct sub_58AFF0)] // value == 0x00
    +0x00:   LENGTH_CLASSNAME    [WORD]
    +0x00:   CLASSNAME           [BYTE] * LENGTH_CLASSNAME

Type 0x0800
^^^^^^^^^^^

* '''DVElementTarget'''
* Read method virtual address: 0x004A9110

.. code-block:: text

    +0x00:   Struct sub_492650 [sizeof (Struct sub_492650)]
    +0x00:   UNK_WORD_00       [WORD]
    +0x00:   UNK_WORD_01       [WORD]
    +0x00:   UNK_WORD_02       [WORD]
    +0x00:   UNK_WORD_03       [WORD]
    +0x00:   UNK_WORD_04       [WORD]
    +0x00:   UNK_DWORD_00      [DWORD]
    +0x00:   LENGTH_CLASSNAME  [WORD]
    +0x00:   CLASSNAME         [BYTE] * LENGTH_CLASSNAME

Type 0x1001
^^^^^^^^^^^

* '''DVElementFX'''
* Read method virtual address: 0x00492650

.. code-block:: text

    +0x00:   Struct sub_492650

Example (Level_01.dvd)
""""""""""""""""""""""

.. code-block:: text

    type = 0x1001
    [+] name (DVF FileName) = Level01_Acrobate
    [+] name (Object Name) = Acrobate
    [+] val == 1: unk_word_00 = 0x0216
    [+] val == 1: unk_word_01 = 0x0189
    [+] val == 1: unk_word_02 = 0x0005

.. code-block:: text

    [+] unk_word_00  = 0x0001
    [+] unk_word_01  = 0x0001
    [+] width        = 0x001E
    [+] height       = 0x0061
    [+] unk_dword_00 = 0x000000A0
    [+] unk_dword_01 = 0x00000078

* Y = 0x0216 + 0x000000A0 = 0x2B6
* X = 0x0189 + 0x00000078 + 0x0005 = 0x206

.. [[File:Test_dvd_elm_dvf_0x1001.jpg|center|thumb |500px|Go fullscreen to see pink crosshair of the coordinate]]


Type 0x0301 || 0x1101 || 0x1102 || 0x1103 || 0x1106 || 0x1105 || 0x1104 || 0x1107 || 0x1108 || 0x1109 || 0x110D || 0x110E || 0x110B || 0x110A || 0x1110 || 0x1111 || 0x1112 || 0x1113 || 0x1114 || 0x1115 || 0x1116 || 0x1117
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* '''DVElementObject'''
* Read method virtual address: 0x004A0970

.. code-block:: text

    +0x00:   Struct sub_58AFF0   [sizeof (Struct sub_58AFF0)] // value == 0x02
    +0x00:   UNK_WORD_00         [WORD]


Type 0x110C
^^^^^^^^^^^

* '''DVElementObject'''
* Read method virtual address: 0x004A0970

.. code-block:: text

    +0x00:   Struct sub_58AFF0   [sizeof (Struct sub_58AFF0)] // value == 0x02
    +0x00:   UNK_WORD_00         [WORD]
    +0x00:   UNK_WORD_01         [WORD]
    +0x00:   UNK_WORD_02         [WORD]


 
extract_elm_info.rb script
--------------------------

Result:

.. code-block:: text

    ba => block_address
    so => size_object
    c_va => constructor virtual address
    v_va => vtable virtual address
    rd => read method virtual address
    v => value (type of object)
    v = 0x00000001 ; rd: 0x0048A7C0 ; ba: 0x004ACE86 ; so: 0x02D0 ; c_va: 0x0044A180 ; v_va: 0x00652648 ;
    v = 0x00000002 ; rd: 0x0048A7C0 ; ba: 0x004ACEBD ; so: 0x02D4 ; c_va: 0x00453EA0 ; v_va: 0x006527E8 ;
    v = 0x00000003 ; rd: 0x0048A7C0 ; ba: 0x004ACEF4 ; so: 0x02D4 ; c_va: 0x0059D350 ; v_va: 0x00654394 ;
    v = 0x00000004 ; rd: 0x0048A7C0 ; ba: 0x004ACF37 ; so: 0x02D0 ; c_va: 0x0050EED0 ; v_va: 0x006539C4 ;
    v = 0x00000005 ; rd: 0x0048A7C0 ; ba: 0x004ACF6E ; so: 0x02D0 ; c_va: 0x00553D90 ; v_va: 0x006540D8 ;
    v = 0x00000006 ; rd: 0x0048A7C0 ; ba: 0x004ACFA5 ; so: 0x02D8 ; c_va: 0x005114C0 ; v_va: 0x00653ACC ;
    v = 0x00000007 ; rd: 0x00463E30 ; ba: 0x004ACFDC ; so: 0x026C ; c_va: 0x00463830 ; v_va: 0x00652A68 ;
    v = 0x00000101 ; rd: 0x0047EAA0 ; ba: 0x004AD00F ; so: 0x0AF0 ; c_va: 0x004858B0 ; v_va: 0x00653124 ;
    v = 0x00000201 ; rd: 0x00467DA0 ; ba: 0x004AD094 ; so: 0x029C ; c_va: 0x00467860 ; v_va: 0x00652B20 ;
    v = 0x00000102 ; rd: 0x0047EAA0 ; ba: 0x004AD0C5 ; so: 0x0878 ; c_va: 0x00485590 ; v_va: 0x00652F90 ;
    v = 0x00000210 ; rd: 0x00463E30 ; ba: 0x004AD0F8 ; so: 0x026C ; c_va: 0x00463830 ; v_va: 0x00652A68 ;
    v = 0x00000211 ; rd: 0x00463E30 ; ba: 0x004AD136 ; so: 0x026C ; c_va: 0x00463830 ; v_va: 0x00652A68 ;
    v = 0x00000212 ; rd: 0x00463E30 ; ba: 0x004AD169 ; so: 0x026C ; c_va: 0x00463830 ; v_va: 0x00652A68 ;
    v = 0x00000301 ; rd: 0x004A0970 ; ba: 0x004AD1BB ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00000213 ; rd: 0x00463E30 ; ba: 0x004AD1EC ; so: 0x026C ; c_va: 0x00463830 ; v_va: 0x00652A68 ;
    v = 0x00000214 ; rd: 0x00463E30 ; ba: 0x004AD21F ; so: 0x026C ; c_va: 0x00463830 ; v_va: 0x00652A68 ;
    v = 0x00000215 ; rd: 0x00463E30 ; ba: 0x004AD252 ; so: 0x026C ; c_va: 0x00463830 ; v_va: 0x00652A68 ;
    v = 0x00000800 ; rd: 0x004A9110 ; ba: 0x004AD285 ; so: 0x0148 ; c_va: 0x004A8630 ; v_va: 0x006535CC ;
    v = 0x00001001 ; rd: 0x00492650 ; ba: 0x004AD2E3 ; so: 0x00B8 ; c_va: 0x00490EF0 ; v_va: 0x00653368 ;
    v = 0x00001101 ; rd: 0x004A0970 ; ba: 0x004AD31D ; so: 0x01B4 ; c_va: 0x004A2D90 ; v_va: 0x00653530 ;
    v = 0x00001102 ; rd: 0x004A0970 ; ba: 0x004AD362 ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001103 ; rd: 0x004A0970 ; ba: 0x004AD39C ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001106 ; rd: 0x004A0970 ; ba: 0x004AD3E7 ; so: 0x01B4 ; c_va: 0x004A2D90 ; v_va: 0x00653530 ;
    v = 0x00001105 ; rd: 0x004A0970 ; ba: 0x004AD421 ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001104 ; rd: 0x004A0970 ; ba: 0x004AD45B ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001107 ; rd: 0x004A0970 ; ba: 0x004AD495 ; so: 0x01B4 ; c_va: 0x004A2D90 ; v_va: 0x00653530 ;
    v = 0x00001108 ; rd: 0x004A0970 ; ba: 0x004AD4F5 ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001109 ; rd: 0x004A0970 ; ba: 0x004AD52F ; so: 0x01B4 ; c_va: 0x004A2D90 ; v_va: 0x00653530 ;
    v = 0x0000110D ; rd: 0x004A0970 ; ba: 0x004AD569 ; so: 0x01B4 ; c_va: 0x004A2D90 ; v_va: 0x00653530 ;
    v = 0x0000110E ; rd: 0x004A0970 ; ba: 0x004AD5A3 ; so: 0x01B4 ; c_va: 0x004A2D90 ; v_va: 0x00653530 ;
    v = 0x0000110B ; rd: 0x004A0970 ; ba: 0x004AD5DD ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x0000110C ; rd: 0x004A0970 ; ba: 0x004AD617 ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x0000110A ; rd: 0x004A0970 ; ba: 0x004AD651 ; so: 0x01B4 ; c_va: 0x004A2D90 ; v_va: 0x00653530 ;
    v = 0x00001110 ; rd: 0x004A0970 ; ba: 0x004AD68B ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001111 ; rd: 0x004A0970 ; ba: 0x004AD6C5 ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001112 ; rd: 0x004A0970 ; ba: 0x004AD6FF ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001113 ; rd: 0x004A0970 ; ba: 0x004AD739 ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001114 ; rd: 0x004A0970 ; ba: 0x004AD773 ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001115 ; rd: 0x004A0970 ; ba: 0x004AD7AD ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
    v = 0x00001116 ; rd: 0x004A0970 ; ba: 0x004AD7E7 ; so: 0x012C ; c_va: 0x0049A7D0 ; v_va: 0x006534C0 ;
