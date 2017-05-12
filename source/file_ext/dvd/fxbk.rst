FXBK
====

General
-------

Load FXs, Sounds, Exclamations files

* VA: 0x57FF70

Specifications
--------------

.code-block:: text

    struct file_header
    struct FXs
    struct Sounds
    struct Exclamations


File Header
^^^^^^^^^^^

.code-block:: text

    +0x00:   VERSION    [DWORD]

* Version must be equal to 0x03.

It's followed by a list of FXs, Sounds and Exclamations to load

struct FXs
^^^^^^^^^^

.code-block:: text
    
    +0x00:   NB_FXS    [WORD]
    +0x02:   ID_FXS    [WORD] * NB_FXS

ID is an entry in file :file:`\\Data\\Sounds\\desperados.fxg`.

struct Sounds
^^^^^^^^^^^^^

.code-block:: text

    +0x00:   NB_SOUNDS [DWORD]
    +0x04:   ID_SOUND  [DWORD] * NB_SOUNDS 

ID is an entry in file :file:`\\Data\\Sounds\\desperados.sbk`.

struct Exclamations
^^^^^^^^^^^^^^^^^^^

.code-block:: text

    +0x00:   NB_XET    [WORD]
    +0x02:   ID_XET    [WORD] * NB_XET
    +0xXX:   NB_XCT    [WORD]
    +0xXX:   ID_XCT    [WORD] * NB_XCT
    +0xXX:   NB_XPT    [WORD]
    +0xXX:   ID_XPT    [WORD] * NB_XPT


:file:`XET%02d.dat`, :file:`XPT%02d.dat`, :file:`XCT%02d.dat` stored in :file:`\\Data\\Sounds\\Expressions`
