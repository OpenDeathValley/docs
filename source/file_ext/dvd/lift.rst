LIFT
====

General
-------

Lift coordinate.

VA: 0x4E1920

Specifications
--------------

.. code-block:

    X

File Header
^^^^^^^^^^^

.. code-block:: text

    +0x00:   VERSION    [DWORD]
    +0x04:   NB_LIFTS   [WORD]

* Version must be equal to 0x02.

Struct LIFT
^^^^^^^^^^^

.. code-block:: text

    +0x00:   sector_id                  [WORD]
    +0x02:   type                       [BYTE]
    +0x03:   unk_word_01                [WORD]
    +0x05:   unk_word_02                [WORD]
    +0x07:   unk_word_03                [WORD]
    +0x09:   unk_word_04                [WORD]
    +0x0B:   STRUCT_COORDS              []
    +0xXX:   StructCOORD                [0x06]
    +0xXX:   unk_word_04                [WORD]

STRUCT_COORDS is present when it is a wall that you can climb.

StructCOORD is the position of the character during the climbing of wall, ladder, stair, etc ...

type
""""

* 0x00: ????
* 0x01: stair
* 0x02: ladder
* 0x03: wall

STRUCT_COORDS
^^^^^^^^^^^^^

.. code-block:: text

    +0x00:   nb                         [WORD]
    +0x02:   STRUCT_COORD               [] * nb

STRUCT_COORD
""""""""""""

.. code-block:: text

    +0x00:   y                          [WORD]
    +0x02:   x                          [WORD]

Example (Level_01.dvd)
----------------------

.. [[File:Dvd_lift_level_01_example.png|center|thumb |500px|Go fullscreen to see pink crosshair for Struct JUMP coordinate, green for STRUCT_INFO_ROOF_BALCONY coordinate and blue polygon for STRUCT_COORDS]]
