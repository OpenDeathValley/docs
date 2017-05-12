DVD
===

General
-------

The DVD files contain data about a level. For every DVD file, there is a corresponding :doc:`/file_ext/dvm`, :doc:`/file_ext/scb`, :doc:`/file_ext/stf` file with the same name.

Specification
-------------

The file contains a list of entries.

Type Entry
^^^^^^^^^^

.. code-block:: text
    
    + 0x00:    ENTRY_TYPE                 [DWORD]
    + 0x04:    SIZE                       [DWORD]

Type Signature
^^^^^^^^^^^^^^

.. * 0x20204941 / '  IA' => '[[DVD File Format: AI|AI]]  '
.. * 0x444E4742 / 'DNGB' => '[[DVD File Format: BGND|BGND]]'
.. * 0x444E4F42 / 'DNOB' => '[[DVD File Format: BOND|BOND]]'
.. * 0x4C495542 / 'LIUB' => '[[DVD File Format: BUIL|BUIL]]'
.. * 0x54524143 / 'TRAC' => '[[DVD File Format: CART|CART]]'
.. * 0x53474C44 / 'SGLD' => '[[DVD File Format: DLGS|DLGS]]'
.. * 0x4D454C45 / 'MELE' => '[[DVD File Format: ELEM|ELEM]]'
.. * 0x4B425846 / 'KBXF' => '[[DVD File Format: FXBK|FXBK]]'
.. * 0x504D554A / 'PMUJ' => '[[DVD File Format: JUMP|JUMP]]'
.. * 0x5446494C / 'TFIL' => '[[DVD File Format: LIFT|LIFT]]'
.. * 0x4B53414D / 'KSAM' => '[[DVD File Format: MASK|MASK]]'
.. * 0x2054414D / ' TAM' => '[[DVD File Format: MAT|MAT]] '
.. * 0x4353494D / 'CSIM' => '[[DVD File Format: MISC|MISC]]'
.. * 0x45564F4D / 'EVOM' => '[[DVD File Format: MOVE|MOVE]]'
.. * 0x4349534D / 'CISM' => '[[DVD File Format: MSIC|MSIC]]'
.. * 0x20544150 / ' TAP' => '[[DVD File Format: PAT|PAT]] '
.. * 0x50524353 / 'PRCS' => '[[DVD File Format: SCRP|SCRP]]'
.. * 0x54484753 / 'THGS' => '[[DVD File Format: SGHT|SGHT]]'
.. * 0x20444E53 / ' DNS' => '[[DVD File Format: SND|SND]] '
.. * 0x53594157 / 'SYAW' => '[[DVD File Format: WAYS|WAYS]]'
