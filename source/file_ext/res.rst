RES
===

File list
---------

* :file:`.\Game\Data\Interface\Texts.res`
* :file:`.\Game\Data\Interface\DEFAULT.RES`
* :file:`.\Game\Data\Sounds\Expressions\Expressions.res`

Texts.res
---------

This file contains only 'TEXT' & 'WAVE'

Expressions.res
---------------

This file contains only 'WAVE'

DEFAULT.RES
-----------

This file contains 'SLID', 'TEXT', 'NPTF', 'BTTN', 'WAVE', 'TOGL', 'CUR ', 'RDO ', 'PIC ', 'PICC'

Specifications
--------------

File Header
^^^^^^^^^^^

.. code-block:: text

    + 0x00:    SIGNATURE                  [DWORD]   /* 0x53455253 / 'SERS' */
    + 0x04:    VERSION                    [DWORD]   /* Must be 0x100 */
    + 0x08:    NB_TYPE_ENTRY              [DWORD]

The header is followed by different type entries

Resource Type Entry
^^^^^^^^^^^^^^^^^^^

.. code-block:: text

    + 0x00:    SIGNATURE_RESOURCE_TYPE    [DWORD]
    + 0x04:    INDEX                      [DWORD]

Resource Type Signature
^^^^^^^^^^^^^^^^^^^^^^^

* 0x45564157 / 'EVAW' => 'WAVE'
* 0x43434950 / 'CCIP' => 'PICC'
* 0x44494C53 / 'DILS' => 'SLID'
* 0x20525543 / ' RUC' => 'CUR '
* 0x20434950 / ' CIP' => 'PIC '
* 0x204F4452 / ' ODR' => 'RDO '
* 0x4E545442 / 'NTTB' => 'BTTN'
* 0x4654504E / 'FTPN' => 'NPTF'
* 0x4C474F54 / 'LGOT' => 'TOGL'
* 0x54584554 / 'TXET' => 'TEXT'

Example (Texts.res)
^^^^^^^^^^^^^^^^^^^

.. code-block:: text

    00000000  53 52 45 53 00 01 00 00 6F 00 00 00 54 45 58 54  SRES....o...TEXT
    00000010  00 00 00 01 01 00 00 00 22 00 4C 00 51 00 75 00  ........".L.Q.u.


* SIGNATURE = 0x53455253
* Version = 0x100
* Number of TYPE entry = 0x0000006F (111)

'WAVE'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00    [DWORD]
    + 0x04:    NB_ENTRY        [WORD]

Entries are path to wave file in this format:

.. code-block:: text

    + 0x00:    LENGTH          [WORD]
    + 0x02:    PATH_STR        [BYTE] * LENGTH


Example (Expressions.res)
"""""""""""""""""""""""""

.. code-block:: text

    00000000  53 52 45 53 00 01 00 00 33 00 00 00 57 41 56 45  SRES....3...WAVE
    00000010  00 00 00 04 01 00 00 00 0C 00 14 00 5C 44 56 49  ............\DVI
    00000020  5F 58 43 54 30 31 45 30 30 56 30 31 2E 77 61 76  _XCT01E00V01.wav
    00000030  14 00 5C 44 56 49 5F 58 43 54 30 31 45 30 31 56  ..\DVI_XCT01E01V


* Signature Resource Type = 0x45564157
* Index = 0x4000000 (67108864)
* UNK_DWORD_00 = 0x01
* Number of entry = 0x000C (12)
* First Entry length = 0x0014 (20)
* First Entry path = "\DVI_XCT01E00V01.wav"
* Second Entry length = 0x0014 (20)
* Second Entry path = "\DVI_XCT01E01V......"

'PICC'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00    [DWORD] /* Seems useless */
    + 0x04:    NB_ENTRY        [DWORD]


Entries are image (ODVImage) stored in RAW or ZLIB format

'SLID'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00    [DWORD] /* Seems useless */
    + 0x04:    NB_ENTRY_BIT    [DWORD]

Nb entry of image is the number of bit (max 6 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 6; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (ODVImage) stored in RAW or ZLIB format

'CUR '
^^^^^^

Contains all CURSOR

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00                     [DWORD]   /* Seems useless */
    + 0x04:    TICK_COUNT_REDRAW                [WORD]
    + 0x06:    HIT_POINT_Y                      [WORD]
    + 0x08:    HIT_POINT_X                      [WORD]
    + 0x0A:    TICK_COUNT_REDRAW_PER_IMAGE      [WORD]   /* IF NB_ENTRY > 1 */
    + 0x0C:    NB_ENTRY                         [DWORD]

Entries are image (ODVImage) stored in RAW or ZLIB format

'PIC '
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00    [DWORD] /* Seems useless */


One entry is an image (ODVImage) stored in RAW or ZLIB format

'RDO '
^^^^^^

Ressource for RADIO button img (it's used in Sound menu option for volume choice).

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00    [DWORD]   /* Seems useless */
    + 0x04:    NB_ENTRY_BIT    [DWORD]

Nb entry of image is the number of bit (max 7 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 7; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (ODVImage) stored in RAW or ZLIB format

'BTTN'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00    [DWORD] /* Seems useless */
    + 0x04:    NB_ENTRY_BIT    [DWORD]


Nb entry of image is the number of bit (max 4 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 4; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (ODVImage) stored in RAW or ZLIB format

'NPTF'
^^^^^^

Similar to 'SLID'

'TOGL'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00    [DWORD] /* Seems useless */
    + 0x04:    NB_ENTRY_BIT    [DWORD]

Nb entry of image is the number of bit (max 5 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 5; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (ODVImage) stored in RAW or ZLIB format

'TEXT'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    UNK_DWORD_00    [DWORD]
    + 0x04:    NB_ENTRY        [WORD]

Entries are in-game dialog stored in wide character string:

.. code-block:: text

    + 0x00:    LENGTH          [WORD]
    + 0x02:    PATH_STR        [BYTE] * LENGTH * 2


Example (Texts.res)
"""""""""""""""""""

.. code-block:: text

    00000000  53 52 45 53 00 01 00 00 6F 00 00 00 54 45 58 54  SRES....o...TEXT
    00000010  00 00 00 01 01 00 00 00 22 00 4C 00 51 00 75 00  ........".L.Q.u.
    00000020  27 00 65 00 73 00 74 00 2D 00 63 00 65 00 20 00  '.e.s.t.-.c.e. .
    00000030  71 00 75 00 65 00 20 00 76 00 6F 00 75 00 73 00  q.u.e. .v.o.u.s.
    00000040  20 00 66 00 61 00 69 00 74 00 65 00 73 00 20 00   .f.a.i.t.e.s. .
    00000050  69 00 63 00 69 00 20 00 3F 00 20                 i.c.i. .?. 

* Signature Resource Type = 0x54584554
* Index = 0x1000000 (16777216)
* UNK_DWORD_00 = 0x01
* Number of entry = 0x0022 (34)
* First Entry length = 0x004C (76)
* First Entry dialog = "Qu'est-ce que vous faites ici ? C'est ma ville ! Je suis arrive le premier !"
* ... etc ...

ODVImage
--------

.. code-block:: text

    +0x00:    WIDTH             [WORD]
    +0x02:    HEIGHT            [WORD]
    +0x04:    TYPE_COMPRESSION  [DWORD]
    +0x08:    SIZE_COMPRESSED   [DWORD]
    +0x0C:    DATA_COMPRESSED   [BYTE] * SIZE_COMPRESSED

TYPE_COMPRESSION
^^^^^^^^^^^^^^^^

* 0x01: zlib compression, R5G6B5
* 0x02: bz2 compression, R5G6B5

IDA
---

sub_5D5F00 // Parse RES file
