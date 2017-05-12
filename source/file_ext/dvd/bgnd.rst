BGND
====

.. [[DVD_File_Format#Type_Signature|BGND]] (background) entries in the [[DVD File Format]].

Contains the minimap (R5G6B5 image bz2 compressed).

Specification
-------------

.. code-block:: text

    +0x00                :    VERSION            [DWORD]
    +0x00                :    SIZE_FILENAME      [WORD]
    +0x02                :    FILENAME           [BYTE] * SIZE_FILENAME
    +0x02 + SIZE_FILENAME:    WIDTH              [WORD]
    +0x04 + SIZE_FILENAME:    HEIGHT             [WORD]
    +0x06 + SIZE_FILENAME:    TYPE_COMPRESSION   [DWORD]
    +0x0A + SIZE_FILENAME:    LENGTH_COMPRESSED  [DWORD]
    +0x0E + SIZE_FILENAME:    DATA_COMPRESSED    [BYTE] * LENGTH_COMPRESSED

* Version must be equal to 0x04
