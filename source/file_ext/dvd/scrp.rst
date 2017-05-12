SCRP
====

..[[DVD_File_Format#Type_Signature|SCRP]] (script) entries in the [[DVD File Format]].

Contains scripts for a level?

Specification
-------------

Header
^^^^^^

.. code-block:: text

    +0x00 :   VERSION       [DWORD]
    +0x04 :   NB_ENTRY      [WORD]

* Version must be equal to 0x01

Entry
^^^^^

Depending of the first WORD value read, entry are totally different.

If first DWORD equal 0x01:

.. code-block:: text

    +0x00 :   FIRST_WORD   [WORD] // Equal to 1 in this case
    +0x02 :   UNK_WORD_01  [WORD]
    +0x04 :   UNK_WORD_02  [WORD]
    +0x06 :   UNK_WORD_03  [WORD]
    +0x08 :   UNK_WORD_04  [WORD]
    +0x0A :   UNK_BYTE_00  [BYTE]


If first WORD is different of 0x02:

.. code-block:: text

    +0x00                      :   FIRST_WORD / NB_COORDINATES [WORD]
    +0x02                      :   Y / X                       [(WORD, WORD)] * NB_COORDINATES
    +0x02 + NB_COORDINATES * 4 :   UNK_WORD_01                 [WORD]
    +0x04 + NB_COORDINATES * 4 :   UNK_WORD_02                 [WORD]
    +0x06 + NB_COORDINATES * 4 :   CLASSNAME_PRESENT           [BYTE]
    +0x07 + NB_COORDINATES * 4 :   CLASSNAME_LENGTH            [WORD] // If CLASSNAME_PRESENT equal to 0x01
    +0x09 + NB_COORDINATES * 4 :   CLASSNAME                   [BYTE] * CLASSNAME_LENGTH

Example (Level1.DVD)
--------------------

.. code-block:: text

    [+] nb coordinate = 0x0006
    [(920, 806), (900, 826), (922, 842), (883, 872), (846, 809), (882, 785)]
    [+] unk_word_01 = 0x0000
    [+] unk_word_02 = 0x0000
    [+] classname_present = 0x01
    [+] classename = "Zone_Boxeur_Ko_54709ec"

"Zone_Boxeur_Ko" means "boxer area".

If we draw pink crosshair on those coordinate, they are near the boxer area.

Looks like those coordinate are here to "delimit" script execution.

.. [[File:Boxeur_area.png]]
