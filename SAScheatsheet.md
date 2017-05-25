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

Numeric variables only: ```sas <var1>--numeric--<var2>```
Character variables only: ```sas<var1>--character--<var2>```
All variables from-to: ```sas <var1>--<var2>```
Particular Observations only: ```sas var <var1>```
Changing the first observation: ```sas firstobs = 30```
Changing the last observation: ```sas obs = 30```
Not printing observations column: ```sas noobs```
Printing only distinct observations: ```sas distinct```


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