======================================
getebuild - I couldn't live without it
======================================

getebuild helps you to quickly operate on ebuilds, by either opening them in
your $EDITOR, just printing the filename or run ebuild (1) on them.

- If `ARGUMENT` is given, ebuild (1) is executed with the selected ebuild as
  first parameter - ``ebuild selected-ebuild ARGUMENT``.

- With the `-e` / `--editor` option, $EDITOR is used to view the ebuild -
  ``$EDITOR selected-ebuild``.

- With the `-l` / `--changelog` option, $PAGER is used to view the ChangeLog
  for the given package.

- If neither cases match, the full path to the ebuild is printed to stdout.

If `ATOM` matches more then one ebuild, the highest visible one
is choosen. If only one ebuild matches the atom, all maskings for this ebuild
are ignore and it is selected.

It is also possible to let getebuild show you a list of all ebuilds with the
``--select`` option and choose which to one to operate on.

Synopsis
========

**getebuild** [`OPTIONS`] <`ATOM`> [`ARGUMENT`]

Options
=======

::

    -e, --editor     Open found ebuild with $EDITOR.
    -c, --changelog  Open ChangeLog with $PAGER
    -l, --list       Show numbered list of possbile ebuilds.
    -s, --select     Like --list, but let the user choose an ebuild by inputing a
                     number and then continue with the selected ebuild.
    
    -V, --version    Print version string.
    -h, --help       Show help text.

Examples
========

Sometimes I want to see what some specific useflag does exactly, so I just run
``getebuild -e ccze`` to open the current ebuild and check ``RDEPEND`` and the
code.


Also helpful is a small shell function::
    
    eunpack() {
        getebuild "$@" unpack
    }

Now everytime I want to e.g. check the ccze source for some bug or
oddity, I just run ``eunpack ccze``::

    stovokor ~ # eunpack ccze
    >> ebuild /usr/portage/app-admin/ccze/ccze-0.2.1-r2.ebuild unpack
    [sniped checksum stuff]
    >>> Unpacking source...
    >>> Unpacking ccze-0.2.1.tar.gz to /var/tmp/portage/app-admin/ccze-0.2.1-r2/work

.. vim:set ft=rst:
