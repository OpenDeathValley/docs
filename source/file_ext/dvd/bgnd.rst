BGND
====

Contains the minimap.

Specification
-------------

Structure
^^^^^^^^^

.. code-block:: text

    struct file_header
    struct sbpicture

File Header
^^^^^^^^^^^

.. code-block:: text

    +0x00                :    VERSION            [DWORD]
    +0x00                :    SIZE_FILENAME      [WORD]
    +0x02                :    FILENAME           [BYTE] * SIZE_FILENAME

* Version must be equal to 0x04

SBPICTURE
^^^^^^^^^

See :ref:`sbpicture`