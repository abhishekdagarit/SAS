# SAS Cheatsheet

&nbsp;
&nbsp;
&nbsp;
## Procedures
---


#### Print
```sas
Proc print data=<dataset's name>;
````

Variation: 

Printing particular column only: 
```sas 
Proc print data=D1; var var1 var2; 
```

Printing without observations: 
```sas
Proc print data=D1 noobs;
```

Printing till an observation: 
```sas
Proc print data=D1(obs=30);
```

Printing from an observation: 
```sas
Proc print data=D1(firstobs=30);
```

Printing from first to last observation: 
```sas
Proc print data=D1(firstobs=10 obs=30);
```

Printing from and to a particular column: 
```sas
Proc print data=D1; var1 -- var5;
```

Printing numeric values only: 
```sas
Proc print data=D1; var1 -numeric- var5;
```

Printing character values only: 
```sas
Proc print data=D1; var1 -character- var5;
```


---
#### Freq

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

---
#### Sort
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

---
#### Means
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

---
#### Contents 

```sas
Proc contents data=<dataset's name>;
```
Variation:
_all_
```sas
Proc contents data=<dataset's name> _all_;
```

---
#### Ttest

```sas
Proc Ttest data=<dataset's name> alpha=0.5;
class <var1>;
var <var2>;
```