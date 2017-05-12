DVM
===

General
-------

DVM file contains the map stored in R5G6B5 bzip2 compressed image

Specifications
--------------

File header
^^^^^^^^^^^

.. code-block:: text

    +0x00:   WIDTH                [WORD]
    +0x02:   HEIGHT               [WORD]
    +0x04:   TYPE_COMPRESSION     [DWORD]
    +0x08:   LENGTH               [DWORD]
    +0x0C:   DATA_Z               [BYTE] * LENGTH

Data are compressed with bzip2

Type
^^^^

* 0x01: zlib compression, R5G6B5
* 0x02: bz2 compression, R5G6B5

Convertion
^^^^^^^^^^

.. code-block:: text

    red = (color >> 11 << 8) / 32
    green = (((color >> 5) & 0x3F) << 8) / 64
    blue = ((color & 0x1F) << 8) / 32

Example (Level_01.dvm)
^^^^^^^^^^^^^^^^^^^^^^

.. code-block:: text

    Offset(h) 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    
    00000000  40 08 40 04 02 00 00 00 80 55 2C 00 42 5A 68 39  @.@......U,.BZh9
    00000010  31 41 59 26 53 59 FC AE 63 97 05 A8 2F 7F FF FF  1AY&SY..c.../...
    00000020  FF FF FE 7E 7C 7E 7C 7F FF FF FF FF 7F 7F 7F 7F  ...~|~|.........


Parse header and uncompressed data:

.. code-block:: text

    [+] width = 0x0840
    [+] height = 0x0440
    [+] type_picture = 0x00000002
    [+] length = 0x002C5580
    [+] length_u = 0x00462000
    0000  ca a3 49 93 48 93 89 ab ca a3 8b bc cd b4 ce b4   ..I.H...........
    0010  8c ac 8d b4 89 9b 08 83 4c a4 cb 9b 07 8b 85 7a   ........L......z
