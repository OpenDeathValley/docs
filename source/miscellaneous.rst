Miscellaneous
=============

.. _sbpicture:

SBPicture
---------

All graphics in the game are stored in the R5G6B5 pixel format (5 bits for red, 6 bits for green and 5 bits for blue).

Two colors are used for transparency in the game:

* `0x07C0`: `R5G6B5(0, 62, 0)` / `R8G8B8(0, 248, 0)`
* `0x001F`: `R5G6B5(0, 0, 31)` / `R8G8B8(0, 0, 248)`

Specifications
^^^^^^^^^^^^^^

.. code-block:: text

    struct picture_header
    unsigned char pixel_data[picture_header.size_compressed]


PICTURE HEADER
""""""""""""""

.. code-block:: text

    +0x00:    WIDTH             [WORD]
    +0x02:    HEIGHT            [WORD]
    +0x04:    TYPE_COMPRESSION  [DWORD]
    +0x08:    SIZE_COMPRESSED   [DWORD]

TYPE_COMPRESSION
""""""""""""""""

* `0x00` : raw
* `0x01` : `zlib` compression
* `0x02` : `bz2` compression

Convertion (`R5G6B5` to `R8G8B8`)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: c

    unsigned short r5g6b5;
    unsigned char red8, green8, blue8;

    /* ... */

    red8 = (r5g6b5 >> 11 << 8) / 32;
    green8 = (((r5g6b5 >> 5) & 0x3F) << 8) / 64;
    blue8 = ((r5g6b5 & 0x1F) << 8) / 32;