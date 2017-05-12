MSIC
====

General
-------

Contains filename of "Quiet", "alert", "fight" music loop

VA: 0x0057FF20

Specifications
--------------

.. code-block:: text

    struct file_header
    List <Struct MSIC Quiet>
    List <Struct MSIC Alert>
    List <Struct MSIC Fight>

File Header
^^^^^^^^^^^

.. code-block:: text

    +0x00:   VERSION    [DWORD]


* Version must be equal to 0x01.

Struct MSIC Quiet
^^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00:   NB_ELEMS       [WORD]
    +0x02:   PASCAL_STRING  [] * NB_ELEMS


Struct MSIC Alert
^^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00:   NB_ELEMS       [WORD]
    +0x02:   PASCAL_STRING  [] * NB_ELEMS

Struct MSIC Fight
^^^^^^^^^^^^^^^^^

.. code-block:: text

    +0x00:   NB_ELEMS       [WORD]
    +0x02:   PASCAL_STRING  [] * NB_ELEMS

PASCAL_STRING
^^^^^^^^^^^^^

.. code-block:: text

    +0x00:   LENGTH_STR     [WORD]
    +0x02:   STR            [BYTE] * LENGTH_STR

Example (Level_01.dvd)
----------------------

.. code-block:: text

    Container:
        version = 1
        StructMSICQuiet = Container:
            nb_elems = 1
            name = [
                'green01.wav'
            ]
        StructMSICAlert = Container:
            nb_elems = 1
            name = [
                'orange02.wav'
            ]
        StructMSICFight = Container:
            nb_elems = 1
            name = [
                'red00.wav'
            ]
