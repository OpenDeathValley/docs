SXT
===

General
-------

Sprite/Image displayed on the screen when you win or loose a mission

File List
---------

* :file:`.\\Game\\Data\\Interface\\Debriefing\\GameOver1.sxt`
* :file:`.\\Game\\Data\\Interface\\Debriefing\\GameOver2.sxt`
* :file:`.\\Game\\Data\\Interface\\Debriefing\\Victory.sxt`

Specifications
--------------

File Header
^^^^^^^^^^^

.. code-block:: text

    +0x00 : WIDTH                [WORD]
    +0x02 : HEIGHT               [WORD]
    +0x04 : TYPE_COMPRESSION     [DWORD]
    +0x08 : LENGTH               [DWORD]
    +0x0C : DATA                 [BYTE] * LENGTH

Type
^^^^

* 0x01: zlib compression, R5G6B5
* 0x02: bz2 compression, R5G6B5

data here are compressed with zlib.

Data are then stored in R5G6B format.