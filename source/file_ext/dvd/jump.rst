JUMP
====


General
-------

Jump coordinate informations:

If you are standing on a roof or balcony of a house and you see a horse directly underneath, you can jump into the saddle and ride away.

VA: 0x004EFF80

Specifications
--------------

.. code-block:: text

    struct file_header
    for (file_header.nb_jumps) {
        Struct JUMP
        if (JUMP.unk_dword_cc > 1) {
            for (JUMP.unk_dword_cc - 1) {
                STRUCT_INFO_ROOF_BALCONY
            } 
        }
    }
    struct Sounds
    struct Exclamations

File Header
^^^^^^^^^^^

.. code-block:: text

    +0x00:   VERSION    [DWORD]
    +0x04:   NB_JUMPS   [WORD]

* Version must be equal to 0x01.

Struct JUMP
^^^^^^^^^^^

.. code-block:: text

    +0x00:   unk_dword_aa               [WORD]
    +0x02:   unk_dword_bb               [WORD]
    +0x04:   unk_dword_cc               [WORD]
    +0x06:   pos_y                      [WORD]
    +0x08:   pos_x                      [WORD]
    +0x0A:   unk_dword_ff               [WORD]
    +0x0C:   unk_dword_gg               [WORD]
    +0x0E:   unk_dword_hh               [WORD]
    +0x10:   STRUCT_INFO_ROOF_BALCONY   [] * (unk_dword_cc - 1)
    +0xXX:   unk_dword_ii               [WORD]
    +0xXX:   unk_dword_jj               [WORD]
    +0xXX:   STRUCT_COORDS              []

STRUCT_INFO_ROOF_BALCONY
^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00:   pos_y                      [WORD]
    +0x02:   pos_x                      [WORD]
    +0x04:   unk_dword_cc               [WORD]
    +0x06:   unk_dword_dd               [WORD]
    +0x08:   unk_dword_ee               [WORD]

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

Example (Level_02.dvd)
----------------------

.. [[File:Dvd_jump_level_02_example.png|center|thumb |500px|Go fullscreen to see pink crosshair for Struct JUMP coordinate, green for STRUCT_INFO_ROOF_BALCONY coordinate and blue polygon for STRUCT_COORDS]]
