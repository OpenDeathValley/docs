DVD
===

.. toctree::
    :hidden:

    /file_ext/dvd/ai.rst
    /file_ext/dvd/bgnd.rst
    /file_ext/dvd/bond.rst
    /file_ext/dvd/buil.rst
    /file_ext/dvd/cart.rst
    /file_ext/dvd/dlgs.rst
    /file_ext/dvd/elem.rst
    /file_ext/dvd/fxbk.rst
    /file_ext/dvd/jump.rst
    /file_ext/dvd/lift.rst
    /file_ext/dvd/mask.rst
    /file_ext/dvd/mat.rst
    /file_ext/dvd/misc.rst
    /file_ext/dvd/move.rst
    /file_ext/dvd/msic.rst
    /file_ext/dvd/pat.rst
    /file_ext/dvd/scrp.rst
    /file_ext/dvd/sght.rst
    /file_ext/dvd/snd.rst
    /file_ext/dvd/ways.rst

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

* 0x20204941 / '  IA' => :doc:`/file_ext/dvd/ai`
* 0x444E4742 / 'DNGB' => :doc:`/file_ext/dvd/bgnd`
* 0x444E4F42 / 'DNOB' => :doc:`/file_ext/dvd/bond`
* 0x4C495542 / 'LIUB' => :doc:`/file_ext/dvd/buil`
* 0x54524143 / 'TRAC' => :doc:`/file_ext/dvd/cart`
* 0x53474C44 / 'SGLD' => :doc:`/file_ext/dvd/dlgs`
* 0x4D454C45 / 'MELE' => :doc:`/file_ext/dvd/elem`
* 0x4B425846 / 'KBXF' => :doc:`/file_ext/dvd/fxbk`
* 0x504D554A / 'PMUJ' => :doc:`/file_ext/dvd/jump`
* 0x5446494C / 'TFIL' => :doc:`/file_ext/dvd/lift`
* 0x4B53414D / 'KSAM' => :doc:`/file_ext/dvd/mask`
* 0x2054414D / ' TAM' => :doc:`/file_ext/dvd/mat`
* 0x4353494D / 'CSIM' => :doc:`/file_ext/dvd/misc`
* 0x45564F4D / 'EVOM' => :doc:`/file_ext/dvd/move`
* 0x4349534D / 'CISM' => :doc:`/file_ext/dvd/msic`
* 0x20544150 / ' TAP' => :doc:`/file_ext/dvd/pat`
* 0x50524353 / 'PRCS' => :doc:`/file_ext/dvd/scrp`
* 0x54484753 / 'THGS' => :doc:`/file_ext/dvd/sght`
* 0x20444E53 / ' DNS' => :doc:`/file_ext/dvd/snd`
* 0x53594157 / 'SYAW' => :doc:`/file_ext/dvd/ways`
