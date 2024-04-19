pg_complex
==========

PG_complex is a PostgreSQL C-language extension that implements a
user-defined type (UDT) for complex numbers. It is intended for
educational purposes, not production use.

(Seriously, why would anyone store complex numbers in a relational
database?)

The UDT demonstrates the use of composite types.

A discussion of the creation and use of this extension can be
found at http://invariantproperties.com/2015/07/17/extending-postgresql-complex-number-data-type/.


Installation
------------


To build it, just do this:

    make
    make installcheck
    make install

If you encounter an error such as:

    "Makefile", line 8: Need an operator

You need to use GNU make, which may well be installed on your system as
`gmake`:

    gmake
    gmake install
    gmake installcheck

If you encounter an error such as:

    make: pg_config: Command not found

Be sure that you have `pg_config` installed and in your path. If you used a
package management system such as RPM to install PostgreSQL, be sure that the
`-devel` package is also installed. If necessary tell the build process where
to find it:

    env PG_CONFIG=/path/to/pg_config make && make install && make installcheck

And finally, if all that fails, copy the entire distribution directory to the
`contrib/` subdirectory of the PostgreSQL source tree and try it there without
`pg_config`:

    env NO_PGXS=1 make && make install && make installcheck

If you encounter an error such as:

    ERROR:  must be owner of database regression

You need to run the test suite using a super user, such as the default
"postgres" super user:

    make installcheck PGUSER=postgres

Once pg_complex is installed, you can add it to a database by connecting to a
database as a super user and running:

    CREATE EXTENSION pg_complex;

Dependencies
------------
The `pg_complex` data type has no dependencies other than PostgreSQL.

Copyright and License
---------------------

Copyright (c) 2015 Bear Giles <bgiles@coyotesong.com>.

