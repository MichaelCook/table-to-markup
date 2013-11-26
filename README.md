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

For example, if the input is:

  one fish two fish
  red fish blue fish

the output would be

||one||fish||two fish ||
||red||fish||blue fish||

The script recognizes numbers and right-justifies them by default.

Options:

  --header-row (-h)    The first row is the table header.

  --align (-a) SPEC
    SPEC is a string of "clrd" characters, one per table column.
      * c - center
      * l - left align
      * r - right align
      * d - default align: numbers are right aligned, all else left.

    If the string is too short (there are more table columns than chars) then
    the last char is used repeatedly.
