# SAS Cheatsheet

&nbsp;
&nbsp;
&nbsp;
## Procedures
---


Print
```sas
Proc print data=<dataset's name>;
````

Variation: 

```sas
Numeric variables only: `<var1>--numeric--<var2>`&nbsp;
Character variables only: `<var1>--character--<var2>`&nbsp;
All variables from-to: `<var1>--<var2>` &nbsp;
Particular Observations only: `var <var1>`&nbsp;
Changing the first observation: `firstobs = 30`&nbsp;
Changing the last observation: `obs = 30`&nbsp;
Not printing observations column: `noobs`&nbsp;
Printing only distinct observations: `distinct`&nbsp;
```

Freq

```sas
Proc freq data=<dataset's name>;
table <var1> <var2>;
```

Variation: 

```sas
No commulative: `/nocum`
No percentage: `/nopercentage`
No row: `/norow`
No col: `/nocol`
No freq: `/nofreq`
Two tables: `table <var1> <var2>`
Two way frequency distribution: `table <var1>*<var2>`
```

Sort
```sas
Proc sort data=<dataset's name>;
by <var1>
```
Variation:
```sas
by descending <var1>
by <var1> descending <var2>
by descending <var1> <var2>
by descending <var1> descending <var2>;
```

Means
```sas
Proc means data=<dataset's name>;
by <var1> <var2>;
```

Variation:
Another option for by: `class <var1>`
```sas
maxdesc = 2
mean min max std
```

Contents 

```sas
Proc contents data=<dataset's name>;
```
Variation:
_all_
```sas
Proc contents data=<dataset's name> _all_;
```