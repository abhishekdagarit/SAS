# SAS Cheatsheet

## Procedures
---
Print
&nbsp;
`Proc print data=<dataset's name>;`
&nbsp;
Variation: 
&nbsp;
Numeric variables only: `<var1>--numeric--<var2>`
Character variables only: `<var1>--character--<var2>`
All variables from-to: `<var1>--<var2>` 
Particular Observations only: `var <var1>`
Changing the first observation: `firstobs = 30`
Changing the last observation: `obs = 30`
Not printing observations column: `noobs`
Printing only distinct observations: `distinct`


Freq
&nbsp;
`Proc freq data=<dataset's name>;`
`table <var1> <var2>`;
&nbsp;
Variation: 
&nbsp;
No commulative: `/nocum`
No percentage: `/nopercentage`
No row: `/norow`
No col: `/nocol`
No freq: `/nofreq`
Two tables: `table <var1> <var2>`
Two way frequency distribution: `table <var1>*<var2>`

Sort
&nbsp;
`Proc sort data=<dataset's name>;`
`by <var1>`
&nbsp;
Variation:
&nbsp;
`by descending <var1>`
`by <var1> descending <var2>`
`by descending <var1> <var2>`
`by descending <var1> descending <var2>;`


Means
&nbsp;
`Proc means data=<dataset's name>;`
`by <var1> <var2>;`
&nbsp;
Variation:
&nbsp;
Another option for by: `class <var1>`
`maxdesc = 2`
`mean min max std`


Contents 
&nbsp;
`Proc contents data=<dataset's name>;`
Variation:
&nbsp;
_all_;
`Proc contents data=<dataset's name> _all_;`