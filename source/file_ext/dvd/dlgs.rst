DLGS
====

.. [[DVD_File_Format#Type_Signature|DLGS]] (dialog) entries in the [[DVD File Format]].

Contains dialog, objectives and debriefing text and sound.

Structure
---------

.. code-block:: text

    struct dlgs_header
    for (dlgs_header.nb_entry) {
        struct text_wave_entries
    }
    struct dlgs_tricks
    struct dlgs_objectives
    struct dlgs_debriefing

Specifications
--------------

.. code-block:: text

    +0x00 :   VERSION       [DWORD]
    +0x04 :   INDEX_TEXT    [DWORD]
    +0x08 :   INDEX_WAVE    [DWORD]
    +0x0C :   NB_ENTRY      [DWORD]
    +0x10 :   TEXT_WAVE_ENTRIES [TEXT_WAVE_ENTRIES] * NB_ENTRY

* Version must be equal to 0x04
* Index Text is an Index that you can find in "Texts.res" :doc:`/file_ext/res`, it's a list of text dialog
* Index Wave is an Index that you can find in "Texts.res" :doc:`/file_ext/res`, it's a list of wave file path
* The nb of entry of the index inside "Texts.res" and NB_ENTRY must be equal!

TEXT_WAVE_ENTRIES
^^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00 :   UNK_DWORD_00   [DWORD]
    +0x04 :   UNK_DWORD_00   [DWORD]
    +0x08 :   UNK_DWORD_00   [DWORD]

TODO

"Trick"
^^^^^^^

The file is then followed by:

.. code-block:: text

    +0x00 :   INDEX          [DWORD]
    +0x04 :   NB_ENTRY       [DWORD]
    +0x08 :   ID             [DWORD] * NB_ENTRY

* Index can be find in "Texts.res"

"Objectives"
^^^^^^^^^^^^

The file is then followed by:

.. code-block:: text

    +0x00 :   INDEX          [DWORD]
    +0x04 :   NB_ENTRY       [DWORD]
    +0x08 :   ID             [DWORD] * NB_ENTRY

* Index can be find in "Texts.res"

"Debriefing"
^^^^^^^^^^^^

The file is then followed by:

.. code-block:: text

    +0x00 :   INDEX          [DWORD]
    +0x04 :   NB_ENTRY       [DWORD]
    +0x08 :   ID             [DWORD] * NB_ENTRY
    +0xXX :   NB_ENTRY_2     [DWORD]
    +0xXX :   ID_2           [DWORD] * NB_ENTRY_2

* Index can be find in "Texts.res"
