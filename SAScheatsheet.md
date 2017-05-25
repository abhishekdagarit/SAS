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

Printing particular column only: `Proc print data=D1; var var1 var2;`
Printing without observations: `Proc print data=D1 noobs;`
Printing till an observation: `Proc print data=D1(obs=30);`
Printing from an observation: `Proc print data=D1(firstobs=30);`
Printing from first to last observation: `Proc print data=D1(firstobs=10 obs=30);`
Printing from and to a particular column: `Proc print data=D1; var1 -- var5;`
Printing numeric values only: `Proc print data=D1; var1 -numeric- var5;`
Printing character values only: `Proc print data=D1; var1 -character- var5;`


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

## Reading Data from external source

---


```sas
Data D1;
infile 'D:computer/code/file.csv';
input var1 var2;
run;

Proc print data=D1;
run;
```


## Reading Data

---


#### Reading data created wihtin SAS

```sas
Data D1;
	Input var1 var2;
Datalines

1 2
1 3
4 2
5 6 
3 7
7 4 
5 88
5 1
9 323
4 6774
32 64
;

run;

Proc print data=D1;
run;

```

#### Less variables more data

---

```sas 
/* Here it takes only the values that it needs and moves on to the next line */ 
Data D1;
input var1 var2;
datalines;
1 2 55
3 4 77
5 6 99
3 6 44
3     23     43
;
run;

Proc print data=D1;
run;

```

#### More variables less data

---

```sas 
/* Here it takes only the values that it needs and moves on to the next line. Hangs on for what it needs. */ 
Data D1;
input var1 var2 var3 var 4;
datalines;
1 2 55
3 4 77
5 6 99
3 6 44
3     23     43
;
run;

Proc print data=D1;
run;

```

#### Won't assign anything

---

```sas 
/* When there isn't enough data for even one observation */ 
Data D1;
input var1 var2;
datalines;
1 
;
run;

Proc print data=D1;
run;

```

---

#### Reading data as either Character or Number

```sas
Data D1;
infile datalines;
input name$ age sex$;

datalines

abhi 23 male
sunny 18 female
;
run;

Proc print data=D1;
run;
```

---

#### Delimiter Sensitive Data

```sas
Data D1;
infile 'd:/computer/code/file1.csv' dsd dlm=';';
input var1 var2$;
run;

Proc print data=D1;
run;
```

---

#### Missover 

When some values are missing and we need to move forward. 

```sas
Data D1;
infile datalines missover;

input var1, var2;
datalines 
1 2
3 4
5 
3 6
2
;

Proc print data=D1;
run;
```





















