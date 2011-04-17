=================================
Arguments common to all utilities
=================================

Description
===========

All utilities which accept CSV as input share a set of common command-line arguments::

  -d DELIMITER, --delimiter DELIMITER
                        Delimiting character of the input CSV file.
  -t, --tabs            Specifies that the input CSV file is delimited with
                        tabs. Overrides "-d".
  -q QUOTECHAR, --quotechar QUOTECHAR
                        Character used to quote strings in the input CSV file.
  -u {0,1,2,3}, --quoting {0,1,2,3}
                        Quoting style used in the input CSV file. 0 = Quote
                        Minimal, 1 = Quote All, 2 = Quote Non-numeric, 3 =
                        Quote None.
  -b, --doublequote     Whether or not double quotes are doubled in the input
                        CSV file.
  -p` ESCAPECHAR, --escapechar ESCAPECHAR
                        Character used to escape the delimiter if quoting is
                        set to "Quote None" and the quotechar if doublequote
                        is not specified.
  -e ENCODING, --encoding ENCODING
                        Specify the encoding the input file.

These arguments may be used to override csvkit's default "smart" parsing of CSV files.  This is frequently necessary if the input file uses a particularly unusual style of quoting or is an encoding that is not compatible with utf-8.

Note that the output of csvkit's utilities is always formatted with "default" formatting options. This means that when executing multiple csvkit commands (either with a pipe or via intermediary files) it is only ever necessary to specify formatting arguments the first time. (And doing so for subsequent commands will likely cause them to fail.)

Examples
========

Cut the 1st and 3rd columns from a file with pipe delimiters and latin-1 encoding::

    $ csvcut -c 1,3 -d "|" -e "iso-8859-1" my_badly_formed.csv
