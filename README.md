table-to-wiki
=============

Take a table formatted as plain text and convert it to Wiki format.

In Wiki format, columns are separated by "||", and rows
begin and end with "||".

The columns of the input might be separated by tabs or spaces:

  * If the input has no tab characters, then we infer the table column
    boundaries: any character column that is a space in every row is assumed
    to be a table column boundary.

  * If there are tabs, we assume all columns are separated by one tab.  This
    is the case if you paste from Excel, for example.
