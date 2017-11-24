table-to-markup
===============

Take a table formatted as plain text and convert it to Wiki or Markdown
format.

The input columns can be separated by tabs or spaces:

  * If the input has no tab characters, then we infer the table column
    boundaries: any character column that is a space in every row is assumed
    to be a table column boundary.

  * If there are tabs, we assume all columns are separated by one tab.  This
    is the case if you paste from Excel, for example.

In Wiki format, columns are separated by "||", and rows begin and
end with "||".  Spacing in each cell determines alignment:

  * A cell with at least two spaces at both the beginning and end will be
    centered by the Wiki table renderer.

  * A cell that is touching exactly one || border will be aligned to that
    border (left or right aligned).

  * Otherwise, the cell gets centered for the header row and left aligned for
    other rows.

Example Wiki table:

```
  ||=Tables     =||=      Are      =||= Cool=||
  ||col 3 is     ||  right-aligned  ||  $1600||
  ||col 2 is     ||    centered     ||    $12||
  ||zebra stripes||    are neat     ||     $1||
```

In Markdown format, columns are separated by "|", and rows begin and end with
"|".  The second line determines how text in each column will be aligned;
colons indicate alignment:

  * center `:---:`

  * right `---:`

  * left `---`

Example Markdown table:

```
  | Tables        | Are           | Cool  |
  | ------------- |:-------------:| -----:|
  | col 3 is      | right-aligned | $1600 |
  | col 2 is      | centered      |   $12 |
  | zebra stripes | are neat      |    $1 |
```

The script recognizes numbers and right-justifies them by default.

Options:

  --header-row (-h)    The first row is the table header.

  --align (-a) SPEC

  SPEC is a string of "clrd" characters, one per table column.

  * c - center
  * l - left align
  * r - right align
  * d - default align: numbers are right aligned, all else left.

  If the SPEC string is too short (there are more table columns than chars)
  then the last char is used repeatedly.

  --wiki (-w)          Output Wiki format (default).

  --markdown (-m)      Output Markdown format.

  --tab (-t)           Output tab-separated columns.
