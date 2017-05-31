# [Base SAS](http://www.blog.iisastr.com/base-sas-free-practice-test.html)

1. The following SAS program is submitted:

```sas
data work.bazzar;
cost = ‘30000’;
newtotal = .10 * cost;
run;
```

> Which one of the following is the value of the variable newTOTAL in the output data set?


> 1. `3000`
> 2. .[missing numberic value]
> 3. 3000
> 4. ''[missing character value]

> Correct Answer: 3. 3000

2. The following SAS program is submitted:

```sas
data Retail;
set   OD;
x = mdy(1,27,1960);
run;
```

> Which one of the following values does the variable named x contain?

> 1. 1
> 2. 1960
> 3. 26
> 4. 01/27/1960
> 5. 27
> 6. 01-27-1960
> 7. 01271960
> 8. It will give complile time error

> Correct Answer: 3. 26

3. The following SAS program is submitted:

```sas
DATA _null_;
set newdata;
put jan feb;
run;
```

> Where is the output written?

> 1. the SAS output window
> 2. by default will go to any of the dataset in work library
> 3. in SAS log
> 4. In the data set name _null_;
> 5. the last dataset created
> 6. the raw data file that was opened last

> Correct Answer: 3. in SAS log

4. Which one of the following SAS procedures displays the Description  portion of a SAS data set?

> 1. proc PRINT D. DATASETS
> 2. proc DATASETS
> 3. A. proc CONTENTS
> 4. A. PRINT FSLIST
> 5. procedure

5. The following SAS program is submitted:

```sas
data work.bank;
JobCategory = ‘BA’;
Level = ‘9’;
JobCategory = JobCategory || Level;
run;
```

> Which one of the following is the value of the variable JOBCATEGORY in the output data set?

> 1. BA 9
> 2. BA9
> 3. BA
> 4. BA 9
> 5. ' ' [missing character value]

> Correct Answer: 3. BA

6. The following SAS  proc  SORT procedure step generates an output data set:

```sas
proc sort data = iisastr.test out = sales;
by id;
run;
```

> In which library is the output data set stored?

> 1. TEST
> 2. SASUSER
> 3. WORK
> 4. SALES
> 5. IISASTR

> Correct Answer: 3. WORK

7. The following SAS program is submitted:

```sas
data work.bank;
date3 = put(’13mar2015’d,date9.);
run;
```

> Which one of the following represents the type and length of the variable DATE3 in the output data set?

> 1. character, 9 bytes
> 2. numeric, 9 bytes
> 3. character, 10 bytes 
> 4. numeric, 8 bytes
> 5. numeric, 10 bytes
> 6. numeric, 8 bytes

> Correct Answer: 1. character, 9 bytes

8. 

```sas
data samp ;
x=’IISASTR’;
y=’999’;
z=x||y;
run;
```

> What will be the value in z?

> 1. IISASTR999
> 2. error because we can’t concatenate character and numeric.
> 3. IISASTR
> 4. 999
> 5. IISASTR 999

> Correct Answer: 1. IISASTR999

9. 

```sas
Data iisastr;
Input y;
datalines;
-98765
;
run;
```

> What will be the value of y  in the iisastr;

> 1. -98765
> 2. +98765
> 3. 987
> 4. 8765
> 5. error: it will not read negative sign

> Correct Answer: 1. -98765

### Category: data types

10.

> Which  of  the  following  is   not  available    data  types  in  SAS?

> 1. DATE
> 2. none of the above
> 3. Character
> 4. number

> Correct Answer: 1. DATE

### Category: sas libray

11. 

> Which of the following files is a permanent SASdatset file?

> 1. temp.iisastr
> 2. Sasuser.admitjune
> 3. Sashelp.class
> 4. iisastr.test
> 5. temporary.iisastr

> Correct Answer: 1,2,3,4,5

### Category: sas libray

12. 

> Which of the following files is a permanent SAS dataset?

> 1. temp.iisastr
> 2. temporary.iisastr
> 3. iisastr.test
> 4. Sasuser.admitjune
> 5. Sashelp.class

> Correct Answer: 1,2,3,4,5

### Category: sas libray

13. 

> Which  of  the following  are correct    syntax  for creation of   library    in  sas?

> 1. libname iisastrgurgaon "d:\iisastr";
> 2. libname iisastr 'd:\iisastr';
> 3. libname iisastr "d:\iisastr";
> 4. libname iisastrgurgaon 'd:\iisastr';
> 5. all of above

> Correct Answer: 2. libname iisastr 'd:\iisastr'; and 3. libname iisastr "d:\iisastr";

### Category: loop

14. The following SAS program is submitted:

```sas
data work.retail;
do year = 1 to 10;
do month = 1 to 12;
x + 1;
end;
end;
run;
```

> Which one of the following represents how many observations are written to the WORK.SALES data set?

> 1. 1
> 2. 10
> 3. 0
> 4. 120
> 5. 12

> Correct Answer: 1. 1

### Category: loop

15. The following SAS program is submitted:

```sas
data work.test;
do until (sales gt 9);
sales + 1;
end;
run;
```

> Which one of the following is the value of the variable sales in the output data set work.test?

> 1. 10
> 2. 9
> 3. 11
> 4. 8

> Correct Answer: 1. 10

### Category: report

16. Which format will display the number 98765432 in 98,765,432.00 format?

> 1. comma11.2
> 2. comma13.2
> 3. dollar13.2
> 4. comma13.1
> 5. comma10.2

> Correct Answer: comma13.2

### Category: report

17. The following SAS program is submitted:

```sas
proc print data =iisastr.test;
run;
```

```sas
proc means data = iisastr.reatil;
run;
```

> Which one of the following OPTIONS statements resets the page number to 1 for the second report  retail  database?

> 1. options reset pagenum = 1;
> 2. options pagenumber = 1;
> 3. options pageno = 1;
> 4. options reset pageno = 1;
> 5. options pagenum = 1;

> Correct Answer: 3. options pageno = 1;

### Category: Functions

18. 

```sas
data test;
inst_name=’IISASTRDELHI’;
sb=substr(scan(inst_name,1),1,1);
run;
```

> What is the length of a variable sb  in the above step:

> 1. 1
> 2. 200
> 3. 8 
> 4. more than 200
> 5. 12

> Correct Answer: 2. 200

### Category: query

19. 

```sas
Data iisastr9;
Set iisastr;
Where empid=600;
Where empid=700;
run;
```

> Which where statement will be affected to  op  dataset?

> 1. None of choice , there is error we can not write two where statement
> 2. Where empid=700;
> 3. Where empid=600;
> 4. both Where empid=600; and Where empid=700;

> Correct Answer: 2. Where empid=700;

### Category: PDV

20. If there is an error while  reading two  variable (which  are  defined number  but  assigning character)   then what will be the value of the _error_

> 1. 1
> 2. it will not compile. so there will compile time error as we are assigning character value to numeric variable
> 3. 2
> 4. 0

> Correct Answer: 1. 1

### Category: data step

21. Which X variable has a value of 1 at the end of an input file?

> 1. EOF =y
> 2. END = y
> 3. LASTOBS = y
> 4. OBS = y
> 5. NOOBS = y

> Correct Answer: 2. END = y

### Category: Vertical merging

22. The following SAS program is submitted:

```sas
data work.company;
set work.d1 (in = frd1)
work.d2 (in = frd2);
if    frd1     and      frd2;
run;
```

> The SAS data set WORK.d1 has   15 observations, and the data set WORK.d2 has 10 observations.
> How many observations will the data set WORK.compny contain?

> 1. 25
> 2. 15 
> 3. 10
> 4. 0
> 5. compiler time error

> Correct Answer: 4. 0


























