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