=======
csvlook
=======

Description
===========

Renders a CSV to the command line in a Markdown-compatible, fixed-width format::

    usage: csvlook [-h] [-d DELIMITER] [-t] [-q QUOTECHAR] [-u {0,1,2,3}] [-b]
                   [-p ESCAPECHAR] [-z FIELD_SIZE_LIMIT] [-e ENCODING] [-L LOCALE]
                   [-S] [--blanks] [--date-format DATE_FORMAT]
                   [--datetime-format DATETIME_FORMAT] [-H] [-K SKIP_LINES] [-v]
                   [-l] [--zero] [-V] [--max-rows MAX_ROWS]
                   [--max-columns MAX_COLUMNS]
                   [--max-column-width MAX_COLUMN_WIDTH] [-y SNIFF_LIMIT] [-I]
                   [FILE]

    Render a CSV file in the console as a Markdown-compatible, fixed-width table.

    positional arguments:
      FILE                  The CSV file to operate on. If omitted, will accept
                            input as piped data via STDIN.

    optional arguments:
      -h, --help            show this help message and exit
      --max-rows MAX_ROWS   The maximum number of rows to display before
                            truncating the data.
      --max-columns MAX_COLUMNS
                            The maximum number of columns to display before
                            truncating the data.
      --max-column-width MAX_COLUMN_WIDTH
                            Truncate all columns to at most this width. The
                            remainder will be replaced with ellipsis.
      -y SNIFF_LIMIT, --snifflimit SNIFF_LIMIT
                            Limit CSV dialect sniffing to the specified number of
                            bytes. Specify "0" to disable sniffing.
      -I, --no-inference    Disable type inference when parsing the input.

If a table is too wide to display properly try piping the output to ``less -S`` or truncating it using :doc:`csvcut`.

If the table is too long, try filtering it down with grep or piping the output to ``less``.

See also: :doc:`../common_arguments`.

.. note::

   The fractional part of a decimal numberal is always truncated. To control this truncation, use ``--no-inference`` along with ``--max-column-width``.

Examples
========

Basic use::

    csvlook examples/testfixed_converted.csv

This tool is especially useful as a final operation when piping through other tools::

    csvcut -c 9,1 examples/realdata/FY09_EDU_Recipients_by_State.csv | csvlook
