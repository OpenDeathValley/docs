LOG
===

File list
---------

* :file:`.\\Data\\Configuration\\debug.log`

Description
-----------

bzip2 archive containing exception information.

Example
-------

.. code-block:: text

    00000000  42 5A 68 39 31 41 59 26 53 59 AC C9 E4 8E 00 00  BZh91AY&SY......
    00000010  18 5F 80 00 12 60 65 4A 72 57 87 4D 84 3F E7 DE  ._...`eJrW.M.?..
    00000020  E0 30 00 A6 C1 A9 A3 49 A9 EA 00 34 7A 8F 51 A3  .0.....I...4z.Q.
    00000030  40 D1 E9 A9 8C 90 AA 79 A9 E5 4C 0D 35 30 00 9A  @......y..L.50..
    00000040  60 00 09 88 A6 10 68 C8 03 40 00 00 00 24 0B CF  `.....h..@...$..
    00000050  5E A2 57 98 C2 3A 0E 0B 4C 19 45 D7 AD 58 C9 5B  ^.W..:..L.E..X.[
    00000060  B6 F2 93 5C 8D 2F 43 98 F7 FA ED CC 54 00 F6 20  ...\./C.....T..
    00000070  2B 68 59 58 60 D5 3F C9 31 42 4A BE 04 FB 1E 78  +hYX`.?.1BJ....x
    00000080  3B A5 51 60 B5 78 5A D9 9C E5 8D D4 95 20 57 36  ;.Q`.xZ...... W6
    00000090  76 EF 8E 1D BA 4D B3 6B 75 99 20 9E 38 21 12 FB  v....M.ku. .8!..
    000000A0  EA 4C 31 2A A4 26 62 24 9C 85 10 15 B0 18 D4 5D  .L1*.&b$.......]
    000000B0  73 3C 06 29 81 D9 DE F9 02 5C 39 90 FE FF C5 B2  s<.).....\9.....
    000000C0  49 C1 48 75 40 D0 A0 4E 2D A0 BD 09 06 1E D8 39  I.Hu@..N-......9
    000000D0  78 2E E4 8A 70 A1 21 59 93 C9 1C                 x...p.!Y...

* 0x5A42 = 'BZ' signature/magic number
* 0x68 = version ('h' for Bzip2 ('H'uffman coding), '0' for Bzip1 (deprecated))
* 0x39 = '1'..'9' block-size 100 kB-900 kB (uncompressed)
* ... etc ...

Extracted
---------

.. code-block:: text

    ====================================================================
    Fatal Exception in File P:\Death Valley\SBLibNG\SBDrawManager.cpp, Line 883:
    The surface you try to delete does not exist (859)!
    ====================================================================
    Writing error information to E:\Game\Desperados\Game\crash000.dat