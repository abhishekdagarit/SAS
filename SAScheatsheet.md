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

#### Defining from where to read a variable

```sas
Data D1;
infile 'D:computer/code/D1.csv'
input var1 @4var2$ @6var3 @13var4;
run;

Proc print data=D1;
run;
```


---

#### Defining the length of variable to read 

This requires alignment

```sas
Data D1;
input name$1-10 age salary;
datalines;
ak das 23 34353534
bk sharma 34 234242
ck verma 43 23424
dk gupta 34 342342
;
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

## Labels 
---

Defining labels in print step doesn't change the actual value. But if it was kept in Data step, that would have.

```sas
Proc print data=D1 label;
label var1='First Name';
run;
```


## Global statements
---

#### Title

```sas
Proc print data=D1;
run;
title `this is my 1st title`;
title2 `this is my 2nd title`;
title3 `this is my 3rd title`;
title4 `this is my 4th title`;
title5 `this is my 5th title`;
title6 `this is my 6th title`;
title7 `this is my 7th title`;
title8 `this is my 8th title`;
title9 `this is my 9th title`;
title10 `this is my 10th title`;
title5 `this is my 5th title`;
```

---

#### Footnote

---


#### Options

nodate - Removes Date

```sas 
Proc print data=D1;
run;
options nodate;
```

nonumber - Removes page number

```sas 
Proc print data=D1;
run;
options nonumber;
```

Editing page number

```sas 
Proc print data=D1;
run;
options pagenumber=100;
```

List size
```sas
options ls=23;
options ls=43;
options ls=256;
Proc print data=D1;
run;
```

Page size
```sas
options ps=10;
Proc print data=D1;
run;
```

---

### if else, do end

Adding a new column using if condition

```sas
Data D1;
set D2;
if<15000<salary<20000 then grade='gradeA'; else
if<20000<=salary<=30000 then grade='gradeB'; else
ifsalary>30000 then grade='gradeC';
run;

Proc print data=D1;
run;
```

Making more than one change in if statement doesn't work. For this we need do else

```sas
Data D1;
set D2;
if<15000<salary<20000 then grade='gradeA'; position='junior manager' 
if<20000<=salary<=30000 then grade='gradeB'; position='senior manager'
ifsalary>30000 then grade='gradeC'; position='Vice President'
run;

Proc print data=D1;
run;
```

Do 

```sas
Data D1;
set D2;
if<15000<salary<20000 then do;
grade='gradeA';
position='junior manager';
end; else
if<20000<=salary<=30000 then do;
grade='gradeB';
position='senior manager';
end; else
if salary>30000 then do;
grade='gradeC';
position='Vice President';
end;
run;

Proc print data=D1;
run;
```

---

### Keep Drop

Keep

```sas
Data D1(keep var1 var2 var3);
set D2;
run;

Proc print data=D2;
run;
```

Drop

```sas
Data D1(drop=var1);
set D2;
run;

Proc print data=D1;
run;
```

---

### ODS

PDF

```sas
ods pdf file=D:/Computer/code/reports/D1.pdf'
proc print data=D1;
run;
ods pdf close;
```

RTF

```sas
ods rtf file=D:/Computer/code/reports/D1.rtf'
proc print data=D1;
run;
ods rtf close;
```

HTML

```sas
ods html file=D:/Computer/code/reports/D1.html'
proc print data=D1;
run;
ods html close;
```

Closing all

```sas
ods pdf file=D:/Computer/code/reports/D1.pdf'
ods rtf file=D:/Computer/code/reports/D1.rtf'
ods html file=D:/Computer/code/reports/D1.html'
proc print data=D1;
run;
ods _all_close;
```


































