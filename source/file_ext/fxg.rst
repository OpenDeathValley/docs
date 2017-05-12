FXG
===

General
-------

Sound bank file

File List
---------

* :file:`.\\Game\\Data\\Sounds\\desperados.fxg`
* :file:`.\\Game\\Data\\Sounds\\menu.fxg`

Specifications
--------------

File header
^^^^^^^^^^^

.. code-block:: text

    +0x00:   SIGNATURE    [DWORD]
    +0x04:   UNK_DWORD_00 [DWORD]
    +0x08:   UNK_DWORD_01 [DWORD]
    +0x0C:   NB_ENTRY     [DWORD]

...

.. code-block:: text

    +0x00:   TYPE_BANK    [DWORD]
    +0x04:   FX_ID        [DWORD]
    +0x08:   UNK_WORD_00  [WORD]

* Signature must be equal to 0x4B425846
