QtShell - Manipulate files by a shell command style API
===============================================

Installation
------------

For user who are already using qpm from qpm.io

1) Run qpm install

    qpm install com.github.benlau.qtshell

2) Include vendor/vendor.pri in your .pro file

You may skip this step if you are already using qpm.

    include(vendor/vendor.pri)

3) Include header

    #include <QtShell>

API
===

dirname
-------

    QString QtShell::dirname(const QString& pathname);

Return directory portion of pathname.

basename
--------

    QString QtShell::basename(const QString& path);

return filename portion of pathname

find
----

    QStringList QtShell::find(const QString& path, const QStringList& nameFilters = QStringList());

walk a file hierarchy

rmdir
-----

    bool QtShell::rmdir(const QString& path);

The rmdir utility removes the directory entry specified by each directory argument, provided it is empty.

touch
-----

    bool QtShell::touch(const QString &path);

The touch utility sets the modification and access times of files.  If any file does not exist, it is created with default permissions.

rm
--

    bool QtShell::rm(const QString& file);
    bool QtShell::rm(const QString& options, const QString& file);

Remove directory entries. Preserved paths (all paths defined in QStandPaths will not be removed)

Examples:

    rm("/tmp/tmp.txt");

    rm("/tmp/*.txt");

    rm("*.txt"); // Remove all txt files in current path

    rm("-rf", "/tmp/dir"); // Remove a directory

Options:

    -v          Be verbose when deleting files, showing them as they are removed.

    -r          Equivalent to -R.

    -R          Attempt to remove the file hierarchy rooted in each file argument include directory

    -f          Dummy option. No different will be made.

mkdir
-----

    bool QtShell::mkdir(const QString &path)

Creates the directory. (-p is applied automatically)

cp
--

    bool cp(const QString& source , const QString &target);

Copy files (recursive is not supported yet)

Examples

    cp("tmp.txt", "/tmp");

    cp("*.txt", "/tmp");

    cp("/tmp/123.txt", "456.txt");
