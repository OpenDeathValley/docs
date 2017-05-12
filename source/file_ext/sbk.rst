SBK
===

SBK files map .wav files to an ID.

Specification
-------------

The file contains a header followed by an arbitrary amount of entries.

Header
^^^^^^

.. code-block:: text

    + 0x00:    SIGNATURE       [DWORD]   /* 0x4b425344 / 'DSBK' */
    + 0x04:    VERSION?        [DWORD]   /* Must be 0x1 */
    + 0x08:    UNKNOWN         [DWORD]   /* 0x78 */


Entry
^^^^^

.. code-block:: text

    + 0x00:    ID                [DWORD]
    + 0x04:    FILE_NAME_LENGTH  [WORD]
    + 0x06:    FILE_NAME         [BYTE] * FILE_NAME_LENGTH /* wav file in the same directory as the sbk file */
