PAK
===

General
-------

PAK contains list of file stored in R5G6B5 bzip2 compressed image

File List
---------

* :file:`.\\Game\\Data\\Interface\\Loading.pak`

But binary contains string:

* :file:`Data\\Interface\\WaitScreen.pak`
* :file:`Data\\Music\\music.pak`
* :file:`Data\\Sounds\\expressions.pak`
* :file:`Data\\Sounds\\fxs.pak`
* :file:`Data\\Interface\\Dialogs\\dialogs.pak`

Specifications
--------------

.. code-block:: text

    while (data_availabe in file) {
        struct image_entry
    }

Image Entry
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

