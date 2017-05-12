MAT
===

.. [[DVD_File_Format#Type_Signature|MAT]] (material) entries in the [[DVD File Format]].

Defines the material for an area?

Structure
---------

.. code-block:: text

    struct mat_header
    for (mat_header.nb_entry) {
        struct Entries_00
        for (Entries_00.nb_entry) {
            byte type
            if type == 0x08 {
                struct Entries_01_type_1
            }
            else {
                struct Entries_02_type_2
            }
        }
    }

Specification
-------------

.. code-block:: text

    +0x00 :      VERSION      [DWORD]
    +0x04 :      NB_ENTRY     [DWORD]

* Version must be equal to 0x04

Entries_00
^^^^^^^^^^

.. code-block:: text

    +0x00 :      UNK_WORD_00    [WORD]
    +0x02 :      NB_ENTRY       [WORD]


Entries_01
^^^^^^^^^^

.. code-block:: text

    +0x00 :      NS_TYPE            [BYTE]
    if NS_TYPE == 0x08:
        +0x01 :      UNK_WORD_00    [WORD]
        +0x03 :      NB_COORD       [WORD]
        +0x05 :      [Y, X]         [WORD] * NB_COORD
    else:
        +0x01 :      UNK_DWORD_00   [DWORD]
        +0x05 :      UNK_DWORD_01   [DWORD]
        +0x09 :      UNK_BYTE_00    [BYTE]
        +0x0A :      UNK_DWORD_02   [DWORD]
        +0x0E :      NB_COORD       [WORD]
        +0x10 :      [Y, X]         [WORD] * NB_COORD
