BUIL
====

.. [[DVD_File_Format#Type_Signature|BUIL]] (building) entries in the [[DVD File Format]]. 

Contains data about buildings, doors, trapdoors etc.

Structure
---------

.. code-block:: text

    struct BUIL_header
    for (BUIL.nb_building) {
        struct BUILDING_entry
        for (BUILDING_entry.nb_door) {
            struct DOOR_entry
            struct DOOR_FRONT_entry
            struct DOOR_ON_entry
            struct DOOR_IN_entry
        }
    }
    word nb_entry
    for (nb_entry) {
        struct unknow_entry
    }

Specification
-------------

Header
^^^^^^

.. code-block:: text

    +0x00 :   VERSION        [DWORD]
    +0x04 :   NB_BUILDING    [WORD]
    +0x06 :   BUILDING_ENTRY [...]
    + ... :   NB_ENTRY       [WORD]
    + ... :   UNKNOW_ENTRY   [...]

Building Entry
^^^^^^^^^^^^^^

.. code-block:: text

    +0x00              :   UNK_WORD_00    [WORD]
    +0x02              :   UNK_WORD_01    [WORD] /* NB OF SOMETHING */
    +0x04              :   ARRAY_NS       [WORD] * UNK_WORD_01
    +0x04 + UNK_WORD_01:   NB_DOOR        [WORD]

DOOR Entry
^^^^^^^^^^

.. code-block:: text

    +0x00                    :     UNK_BYTE_00               [BYTE] /* Type ? : 0x01 DOOR, 0x02, TRAPDOOR ? */
    +0x01                    :     UNK_BYTE_01               [BYTE]
    +0x02                    :     UNK_BYTE_02               [BYTE]
    +0x03                    :     UNK_BYTE_03               [BYTE]
    +0x04                    :     UNK_BYTE_04               [BYTE]
    +0x05                    :     UNK_BYTE_05               [BYTE]
    +0x06                    :     UNK_BYTE_06               [BYTE]
    +0x07                    :     UNK_BYTE_07               [BYTE]
    +0x08                    :     UNK_BYTE_08               [BYTE]
    +0x09                    :     UNK_BYTE_09               [BYTE]
    +0x0A                    :     NB_COORDINATE             [WORD]
    +0x0C + NB_COORDINATE * 2:     [Y, X]                    [WORD] * NB_COORDINATE * 2

DOOR FRONT Entry
^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00 :     ID_POINTS                 [WORD]
    +0x02 :     Y                         [WORD]
    +0x04 :     X                         [WORD]
    +0x06 :     UNK_WORD_00               [WORD]
    +0x08 :     UNK_WORD_01               [WORD]


DOOR ON Entry
^^^^^^^^^^^^^

.. code-block:: text

    +0x00 :     Y                         [WORD]
    +0x02 :     X                         [WORD]
    +0x04 :     UNK_WORD_00               [WORD]
    +0x06 :     UNK_WORD_01               [WORD]


DOOR INSIDE Entry
^^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00 :     Y                         [WORD]
    +0x02 :     X                         [WORD]
    +0x04 :     UNK_WORD_00               [WORD]
    +0x06 :     UNK_WORD_01               [WORD]

Example (Level_01.dvd)
----------------------

.. [[File:test_dvd_BUIL.jpg|center|thumb |500px|Go fullscreen to see pink & green crosshair of all coordinates]]
