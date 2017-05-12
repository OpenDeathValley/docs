BOND
====

.. [[DVD_File_Format#Type_Signature|BOND]] entries in the [[DVD File Format]].

Contains a list of coordinates?

Structure
---------

.. code-block:: text

    struct bond_header
    for (bond_header.nb_entry) {
        struct bond_entries
    }

Specification
-------------

.. code-block:: text

    +0x00 :      VERSION      [DWORD]
    +0x04 :      NB_ENTRY     [WORD]


Entries
^^^^^^^

.. code-block:: text

    +0x00 :      X_1          [WORD]
    +0x02 :      Y_1          [WORD]
    +0x04 :      X_2          [WORD]
    +0x06 :      Y_2          [WORD]
    +0x08 :      UNK_DWORD_00 [WORD]
    +0x0A :      UNK_DWORD_01 [WORD]
    +0x0C :      UNK_DWORD_02 [WORD]

* Version is not tested

Example (Level_01.dvd)
----------------------

.. [[File:Level_01_bond_crosshair.jpg|center|thumb |500px|Go fullscreen to see pink crosshair of all coordinates]]
