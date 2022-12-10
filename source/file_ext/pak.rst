PAK
===

General
-------

Files with extension ``*.pak`` contains list of file stored in R5G6B5 bzip2 compressed image

File List
---------

* :file:`.\\Game\\Data\\Interface\\Loading.pak`

But binary contains string:

* :file:`Data\\Interface\\WaitScreen.pak`
* :file:`Data\\Music\\music.pak`
* :file:`Data\\Sounds\\expressions.pak`
* :file:`Data\\Sounds\\fxs.pak`
* :file:`Data\\Interface\\Dialogs\\dialogs.pak`

Specifications
--------------

.. code-block:: text

    while (data_availabe in file) {
        struct sbpicture
    }

SBPICTURE
^^^^^^^^^

See :ref:`sbpicture`

