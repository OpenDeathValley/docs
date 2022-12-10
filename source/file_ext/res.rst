RES
===

General
-------

Files with extension ``*.res`` contains dialogs, buttons, cursors, etc... stored in different ways.

File list
---------

+----------------------------------------------------------------------+----------------------------------+
| Filename                                                             | md5sum                           |
+----------------------------------------------------------------------+----------------------------------+
| data/sounds/expressions/expressions.res                              | dc45e9538a6ac4683e2c66b071fe6fd7 |
+----------------------------------------------------------------------+----------------------------------+
| demo/data/interface/default.res                                      | 864dba4dc53ddac85220917e2ebac55b |
+----------------------------------------------------------------------+----------------------------------+
| localisation/dutch/data/interface/default.res                        | 64301d08b0070910b9a5f5f8a1f1ff06 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/dutch/data/interface/texts.res                          | 896d15c6d65f135b53405074de0065aa |
+----------------------------------------------------------------------+----------------------------------+
| localisation/english/data/interface/default.res                      | 3c18108ac7ba9576cd09d82c340a4fe6 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/english/data/interface/texts.res                        | db21118e7be568573a8fd377082daafe |
+----------------------------------------------------------------------+----------------------------------+
| localisation/french/data/interface/default.res                       | ff8bbdf8ac39f472e92d1392a405f375 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/french/data/interface/texts.res                         | c5debbfee1600aa8c907bedbf1956328 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/german/data/interface/default.res                       | e919510da87df778777dec8949221aff |
+----------------------------------------------------------------------+----------------------------------+
| localisation/german/data/interface/texts.res                         | 8a26a38d24821ec6b9ac52b15b7f79b7 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/german/data/sounds/expressions/expressions.res          | 71a0b5c0dcb497725e20442717333b93 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/italian/data/interface/default.res                      | 60243c5fb1cea1bf45353905d6be0b53 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/italian/data/interface/texts.res                        | 0ca98c08de8ee12813b02bc75ca6e994 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/italian/data/sounds/expressions/expressions.res         | dc45e9538a6ac4683e2c66b071fe6fd7 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/russian/data/interface/default.res                      | cf450d0dec042decbf5bdec481d65781 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/russian/data/interface/texts.res                        | 5194c687f948f84abdc0a00206727670 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/russian/data/sounds/expressions/expressions.res         | dc45e9538a6ac4683e2c66b071fe6fd7 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/spanish/data/interface/default.res                      | 80d9111473d8495eb53aef3177e1b54e |
+----------------------------------------------------------------------+----------------------------------+
| localisation/spanish/data/interface/texts.res                        | b366f0cc3ad42403708a9ba48a864e22 |
+----------------------------------------------------------------------+----------------------------------+
| localisation/spanish/data/sounds/expressions/expressions.res         | dc45e9538a6ac4683e2c66b071fe6fd7 |
+----------------------------------------------------------------------+----------------------------------+
| localisation_demo/french/data/interface/default.res                  | ea0851031814436d4c80f1bc681c00e8 |
+----------------------------------------------------------------------+----------------------------------+
| localisation_demo/french/data/interface/texts.res                    | f3d43779f1c895ba0c84f11d6b12c44e |
+----------------------------------------------------------------------+----------------------------------+
| localisation_demo/german/data/interface/default.res                  | 158e699a55746727f8b5cd7dda7df3df |
+----------------------------------------------------------------------+----------------------------------+
| localisation_demo/german/data/interface/texts.res                    | 66c475f0f2b9e0ab2b734802dca44144 |
+----------------------------------------------------------------------+----------------------------------+
| localisation_demo/spanish/data/interface/default.res                 | c4238b4eb99186d543451bdfe033dcea |
+----------------------------------------------------------------------+----------------------------------+
| localisation_demo/spanish/data/interface/texts.res                   | 76905fad96f264a9d8e6947245477869 |
+----------------------------------------------------------------------+----------------------------------+

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

Structure
^^^^^^^^^

.. code-block:: text

    struct file_header
    for (file_header.nb_type_entry) {
        struct resource_type_entry
    }

File Header
^^^^^^^^^^^

.. code-block:: text

    + 0x00:    SIGNATURE                  [DWORD]
    + 0x04:    VERSION                    [DWORD]
    + 0x08:    NB_TYPE_ENTRY              [DWORD]

The header is followed by different type entries

* Size of ``Header`` : `0x0C`
* ``SIGNATURE`` must be equal to "SERS" (`0x53455253`)
* ``VERSION`` must be equal to `0x100`

Resource Type Entry
^^^^^^^^^^^^^^^^^^^

.. code-block:: text

    + 0x00:    SIGNATURE_RESOURCE_TYPE    [DWORD]
    + 0x04:    ID_RESOURCE                [DWORD]

Resource Type Signature
^^^^^^^^^^^^^^^^^^^^^^^

+-----------------------+----------------------------------+-----------------+
| Signature             | Description                      | Type            |
+-----------------------+----------------------------------+-----------------+
| `0x45564157` ('EVAW') | Wave table resource              | :ref:`res_wave` |
+-----------------------+----------------------------------+-----------------+
| `0x43434950` ('CCIP') | Picture collection resource      | :ref:`res_picc` |
+-----------------------+----------------------------------+-----------------+
| `0x44494C53` ('DILS') | Slider resource                  | :ref:`res_slid` |
+-----------------------+----------------------------------+-----------------+
| `0x20525543` (' RUC') | Mouse resource                   | :ref:`res_cur`  |
+-----------------------+----------------------------------+-----------------+
| `0x20434950` (' CIP') | Picture resource                 | :ref:`res_pic`  |
+-----------------------+----------------------------------+-----------------+
| `0x204F4452` (' ODR') | Radio resource                   | :ref:`res_rdo`  |
+-----------------------+----------------------------------+-----------------+
| `0x4E545442` ('NTTB') | Button resource                  | :ref:`res_bttn` |
+-----------------------+----------------------------------+-----------------+
| `0x4654504E` ('FTPN') | Input field resource             | :ref:`res_nptf` |
+-----------------------+----------------------------------+-----------------+
| `0x4C474F54` ('LGOT') | Toggle button resource           | :ref:`res_togl` |
+-----------------------+----------------------------------+-----------------+
| `0x54584554` ('TXET') | String table resource            | :ref:`res_text` |
+-----------------------+----------------------------------+-----------------+

.. _res_wave:

'WAVE'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    PADDING_00      [DWORD] // unused
    + 0x04:    NB_ENTRY        [WORD]

Entries are path to `WAV` file in this format:

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
* First Entry path = "\\DVI_XCT01E00V01.wav"
* Second Entry length = 0x0014 (20)
* Second Entry path = "\\DVI_XCT01E01V......"

.. _res_picc:

'PICC'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    FLAG            [DWORD]
    + 0x04:    NB_ENTRY        [DWORD]


Entries are image (:ref:`sbpicture`) stored in RAW or ZLIB format

.. _res_slid:

'SLID'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    FLAG            [DWORD]
    + 0x04:    NB_ENTRY_BIT    [DWORD]

Nb entry of image is the number of bit (max 6 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 6; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (:ref:`sbpicture`) stored in RAW or ZLIB format

.. _res_cur:

'CUR '
^^^^^^

Contains all CURSOR

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    PADDING_00                       [DWORD]   // unused
    + 0x04:    TICK_COUNT_REDRAW                [WORD]
    + 0x06:    HIT_POINT_Y                      [WORD]
    + 0x08:    HIT_POINT_X                      [WORD]
    + 0x0A:    TICK_COUNT_REDRAW_PER_IMAGE      [WORD]   /* IF NB_ENTRY > 1 */
    + 0x0C:    NB_ENTRY                         [DWORD]

Entries are image (:ref:`sbpicture`) stored in RAW or ZLIB format

.. _res_pic:

'PIC '
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    FLAG         [DWORD]


One entry is an image (:ref:`sbpicture`) stored in RAW or ZLIB format

.. _res_rdo:

'RDO '
^^^^^^

Ressource for RADIO button img (it's used in Sound menu option for volume choice).

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    FLAG            [DWORD]
    + 0x04:    NB_ENTRY_BIT    [DWORD]

Nb entry of image is the number of bit (max 7 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 7; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (:ref:`sbpicture`) stored in RAW or ZLIB format

.. _res_bttn:

'BTTN'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    FLAG            [DWORD]
    + 0x04:    NB_ENTRY_BIT    [DWORD]


Nb entry of image is the number of bit (max 4 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 4; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (:ref:`sbpicture`) stored in RAW or ZLIB format

.. _res_nptf:

'NPTF'
^^^^^^

.. note::

    Similar to 'SLID'

.. code-block:: text

    + 0x00:    FLAG            [DWORD]
    + 0x04:    NB_ENTRY_BIT    [DWORD]

Nb entry of image is the number of bit (max 6 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 6; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (:ref:`sbpicture`) stored in RAW or ZLIB format

.. _res_togl:

'TOGL'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    FLAG            [DWORD]
    + 0x04:    NB_ENTRY_BIT    [DWORD]

Nb entry of image is the number of bit (max 5 bits) to 1 stored in NB_ENTRY_BIT.

.. code-block:: text

    nbentry = 0;
    for (i = 0; i < 5; i++) {
        if ((1 << i) & NB_ENTRY_BIT)
            nbentry++;
    }

Entries are image (:ref:`sbpicture`) stored in RAW or ZLIB format

.. _res_text:

'TEXT'
^^^^^^

Resource Header
"""""""""""""""

.. code-block:: text

    + 0x00:    PADDING_00      [DWORD] // unused
    + 0x04:    NB_ENTRY        [WORD]

Entries are in-game dialog stored in wide character string:

.. code-block:: text

    + 0x00:    LENGTH          [WORD]
    + 0x02:    PATH_STR        [BYTE] * LENGTH * 2


Example (Texts.res)
^^^^^^^^^^^^^^^^^^^

.. code-block:: text

    00000000  53 52 45 53 00 01 00 00 6F 00 00 00 54 45 58 54  SRES....o...TEXT
    00000010  00 00 00 01 01 00 00 00 22 00 4C 00 51 00 75 00  ........".L.Q.u.


* SIGNATURE = 0x53455253
* Version = 0x100
* Number of TYPE entry = 0x0000006F (111)

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