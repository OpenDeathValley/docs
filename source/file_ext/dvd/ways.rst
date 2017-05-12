WAYS
====

General
-------


Specifications
--------------

.. code-block:: text

    struct ways_header
    for ways_header.nb_entry {
        short nb_waypoints
        for nb_waypoints {
            struct waypoint
        }
    }

Struct WAYS
-----------

.. code-block:: text

    +0x00:    VERSION      [DWORD]
    +0x04:    NB_ENTRY     [WORD]

* Version must be equal to 0x01

Struct waypoint
---------------

.. code-block:: text

    +0x00:    Y_COORD              [WORD]
    +0x02:    X_COORD              [WORD]
    +0x04:    UNK_WORD_00          [WORD]
    +0x06:    UNK_WORD_01          [WORD]
    +0x08:    CLASS_NAME_PRESENT   [BYTE]
    +0x0A:    LENGTH_DATA          [WORD]
    +0x0C:    DATA                 [BYTE] * LENGTH_DATA

* If CLASS_NAME_PRESENT is equal t0 0x01, DATA is a classname that we can find in the associate .scb file
