# Advanced SAS Question Part 2

1. Given the SAS data set 

> ONE: ONEDIVISIONSALES A 1234 A 3654 B 5678 

The following SAS program is submitted: 

> data _null_; set one; 
> by division; 
> if first.division then do; 
> %let mfirst = sales; 
> end; 
> run; 

What is the value of the macro variable MFIRST when the program finishes execution?  

A.1234  
B.5678  
C.null  
D.sales  

> Answer: D

---



2. The following SAS program is submitted: 

> data temp; array points{2,3} (10, 15, 20, 25, 30, 35); 
> run; 

What impact does the ARRAY statement have in the Program Data Vector (PDV)?  

A.The variables named POINTS1, POINTS2, POINTS3, POINTS4, POINTS5, POINTS6 are created in the PDV. 
B.The variables named POINTS10, POINTS15, POINTS20, POINTS25, POINTS30, POINTS35 are created in the PDV.  
C.The variables named POINTS11, POINTS12, POINTS13, POINTS21, POINTS22, POINTS23 are created in the PDV.  
D.No variables are created in the PDV.  

> Answer: A

---


3. Given the SAS data sets 

> MATH1A and MATH1B: MATH1AMATH1BNAME FINAME FI Lauren LSmith M Patel ALauren S Chang ZPatel A Hillier R 

The following SAS program is submitted: 

> proc sql; select * from MATH1A select * from MATH1B; quit; 

The following output is desired: 

> NAME FI Lauren L Patel A Chang Z Smith M Lauren S Patel A Hillier R 

Which SQL set operator completes the program and generates the desired output? 

A.APPEND CORR  
B.EXCEPT CORR  
C.OUTER UNION CORR  
D.INTERSECT ALL CORR  

> Answer: C

---



4. The following SAS program is submitted: 

> %let test = one; 
> %let one = two; 
> %let two = three; 
> %let three = last; 
> %put what displays is &&&&&test; 

What is written to the SAS log? 

A.what displays is one  
B.what displays is two  
C.what displays is three  
D.what displays is last  

> Answer: B

---



5. Given the following partial S

> AS log: 
> 29 %macro test; 
> 30 %if &a = 5 %then %do; 
> 31 proc print data = sashelp.prdsale; 
> 32 run; 
> 33 %end; 
> 34 %else %put a is not 5; 
> 35 %mend; 
> 36 
> 37 %let a = 5; 
> 38 %test (TEST): Beginning execution. : Macro variable A resolves to 5(TEST): %IF condition &a = 5 is TRUE (TEST): proc print data = sashelp.prdsale; (TEST): 
> run; 

Which SAS System option writes to the SAS log the note Macro variable A resolves to 5?

A.MLOGIC  
B.MPRINT  
C.SYMBOLGEN  
D.MSGLEVEL= I  

> Answer: C

---



6. The SAS data set WORK.TEMPDATA contains the variables > FMTNAME, START, and LABEL and it consists of 10 observations. 

The following SAS program is submitted: 

> proc format cntlin = work.tempdata; 
> run; 

What is the result of submitting the FORMAT procedure step?  

A.No formats are created in this step.  
B.All formats created will be stored in the WORK.TEMPDATA SAS data set.  
C.It uses the WORK.TEMPDATA SAS data set as input to create the format.  
D.An ERROR message is written to the SAS log because the program is incomplete. 

> Answer: C

---



7. Given the SAS data sets 

> ONE and TWO: ONETWO YEARQTRBUDGETYEARQTRSALES 20013 50020014 300 20014 40020012 200 20021 70020021 600 

The following SAS program is submitted: 

> proc sql; 
> select one.*, 
> sales from one, two where one.year = two.year; 
> quit; 

Which report is generated?  

A.YEAR QTR BUDGET SALES 2001 4 400 300 2002 1 700 600  
B.YEAR QTR BUDGET SALES 2001 3 500 300 2001 4 400 200 2002 1 700 600  
C.YEAR QTR BUDGET SALES 2001 3 500 300 2001 3 500 200 2001 4 400 300 2001 4 400 200 2002 1 700 600  
D.YEAR QTR BUDGET SALES 2001 3 500 300 2001 4 400 300 2002 1 700 300 2001 3 500 200 2001 4 400 200 2002 1 700 200 2001 3 500 600 2001 4 400 600 2002 1 700 600 

> Answer: C

---



8. Given the SAS data sets 

> ONE and TWO: ONETWO YEARQTRBUDGETYEARQTRSALES 20013 50020014 300 20014 40020021 600 20021 700 

The following SAS program is submitted: 

> proc sql; 
> select one.*, 
> sales from one left join two on one.year = two.year 
> where one.year=2001; 
> quit; 

Which report is generated? 

A.YEAR QTR BUDGET SALES 2001 3 500 . 2001 4 700 600  
B.YEAR QTR BUDGET SALES 2001 3 500 300 2001 4 400 300  
C.YEAR QTR BUDGET SALES 2001 3 500 300 2001 4 400 300 2002 1 700 600  
D.YEAR QTR BUDGET SALES 2001 3 500 . 2001 4 400 300 2001 4 . 300  

> Answer: B

---



9. Given the SAS data set 

> ONE: ONE COUNTRYCITY VISIT USABOSTON 10 UKLONDON 5 USADALLAS 10 UKMARLOW 10 USABOSTON 20 USABOSTON 20 UKLONDON 15 USADALLAS 10 

The following SAS program is submitted: 

> proc sql; 
> select country, city, sum(visit) 
> as TOTAL from one 
> group by country, city 
> order by country, total desc; 
> quit; 

Which report is generated?  

A.COUNTRY CITY TOTAL USA DALLAS 20 USA BOSTON 50 UK MARLOW 10 UK LONDON 20  
B.COUNTRY CITY TOTAL UK LONDON 20 UK MARLOW 10 USA BOSTON 50 USA DALLAS 20  
C.COUNTRY CITY TOTAL USA BOSTON 50 USA DALLAS 20 UK LONDON 20 UK MARLOW 10  
D.COUNTRY CITY TOTAL UK MARLOW 10 UK LONDON 20 USA DALLAS 20 USA BOSTON 50  

> Answer: B

---



10. Given the SAS data set 

> ONE: ONE CATEGORYAGESALARYBONUS M 29 200 20 M 25 100 10 M 48 300 10 F 38 300 50 F 25 200 . 

The following output is desired: 

> CATEGORY EARNINGS F 550 M 640 The following SAS program is submitted: proc sql; 

from one group by category; quit; Which SQL procedure clause completes the program and generates the desired output?  

A.select category, sum(salary, bonus) as EARNINGS  
B.select category, sum(salary + bonus) as EARNINGS  
C.select distinct category, sum(salary, bonus) as EARNINGS  
D.select distinct category, sum(sum(salary, bonus)) as EARNINGS  

> Answer: D

---


11. Given the SAS data sets 

> ONE and TWO: ONE TWONUM COUNTRY NUM CITY 1 CANADA 3 PARIS 2 FRANCE 5 TOKYO 3 GERMANY 4 BELGIUM 5 JAPAN 

The following SAS program is submitted: proc sql; select country from one where not exists 

> (select * from two where one.num = two.num); 
> quit; 

Which report is generated?    
A.COUNTRYFRANCEJAPAN  
B.COUNTRYGERMANYJAPAN  
C.COUNTRYCANADAFRANCEBELGIUM  
D.COUNTRY FRANCEGERMANYBELGIUM  

> Answer: C

---



12. Given the SAS data set 

> ONE: ONEREP COST SMITH 200 SMITH 400 JONES 100 SMITH 600 JONES 100 

The following SAS program is submitted: 

> proc sql; 
> select rep, avg(cost) as AVERAGE from one group by rep quit; 

The following output is desired: 

> REP AVERAGE SMITH 400 Which SQL procedure clause completes the program and generates the desired output?  

A.having avg(cost) < select avg(cost) from one);  
B.where avg(cost) > (select avg(cost) from one);  
C.having avg(cost) > (select avg(cost) from one);  
D.where calculated average > (select avg(cost) from one);  

> Answer: C

---


 
13. Given the SAS data sets 

> ONE and TWO: ONE TWO NUMCHAR1NUMCHAR2 1A 2 X 2B 3 Y 4D 5 V 

The following SAS program is submitted, creating the output table 

> THREE: data three; set one two; run; THREENUMCHAR1 CHAR2 1A 2B 4D 2 X 3 Y 5 V 

Which SQL procedure program creates an equivalent SAS data set THREE?  

A.proc sql; create table three as select * from one outer union corr select * from two; quit; 
B.proc sql; create table three as select * from one outer union select * from two; quit; 
C.proc sql; create table three as select * from one union select * from two; quit;  
D.proc sql; create table three as select * from one union corr select * from two; quit; 

> Answer: A

---



14. The following SAS program is submitted: 

> proc contents data = testdata.one; 
> run; 
 
Which SQL procedure program produces similar information about the column attributes of the dataset TESTDATA.ONE?  

A.proc sql; contents testdata.one; quit;  
B.proc sql; describe testdata.one; quit;  
C.proc sql; contents table testdata.one; quit;  
D.proc sql; describe table testdata.one; quit;  

> Answer: D

---



15. The following SAS program is submitted: 

> proc datasets lib = testdata; 
> modify one; 
> label num = 'Number'; 
> format num 4.; 
> quit; 

Which SQL procedure program produces the same results?   

A.proc sql; modify table testdata.one set num format = 4. label = 'Number'; quit;  
B.proc sql; alter table testdata.one modify num format = 4. label = 'Number'; quit;  
C.proc sql; modify table testdata.one alter num format = 4. label = 'Number'; quit;  
D.proc sql; alter table testdata.one set num format = 4. label = 'Number'; quit;  

> Answer: B

---



16. What does the DICTIONARY.MACROS table store?  

A.information about user defined macro variables only  
B.information about system defined macro variables only  
C.information about both user and system defined macro variables  
D.information about macros stored in the autocall macro library only  

> Answer: C

---



17. The following SAS program is submitted: 

> %let lib = %upcase(sasuser); 
> proc sql; 
> select nvar from dictionary.tables 
> where libname = "&lib"; 
> quit; 

Several SAS data sets exist in the SASUSER library. 

What is generated as output?  

A.a report showing the numeric columns in each table in SASUSER  
B.a report showing the number of columns in each table in SASUSER  
C.a report showing the names of the columns in each table in SASUSER  
D.a report showing the number of numeric columns in each table in SASUSER  

> Answer: B

---


 
18. The following SAS program is submitted: 

> proc sql; 
> select * from dictionary.tables; 
> quit; 

What is generated as output?  

A.metadata on all tables in all libraries  
B.metadata on all tables in the WORK library only  
C.metadata on the DICTIONARY.TABLES table only  
D.metadata on all tables in the DICTIONARY library only  

> Answer: A

---



19. Which should be avoided when creating and using an SQL procedure view?  

A.using a HAVING clause  
B.using summary functions  
C.referencing a view multiple times in the same program  
D.creating views on tables whose structures remain constant  

> Answer: C

---



20. Given the SAS data set 

> ONE: ONENUMVAR 1 A 2 B 3 C 

Which SQL procedure program deletes the data set ONE?  

A.proc sql; delete table one; quit;  
B.proc sql; remove table one; quit;  
C.proc sql; drop table one; quit;  
D.proc sql; delete from one; quit;  

> Answer: C

---


 
21. Given the SAS data set ONE: 

> ONE JOBLEVEL SALARY ACC2 300 SEC1 100 SEC2 200 MGR3 700 ACC1 . ACC3 . MGR2 400 

The following SAS data set TWO is required: 

> TWO JOBLEVEL BONUS ACC2 30 MGR3 70 MGR2 40 

Which SQL procedure program creates the data set TWO?

A.proc sql; create table two as select job, level, salary * 0.1 as BONUS from one where 3 > 20; quit;  
B.proc sql; create table two as select job, level, salary * 0.1 as BONUS from one where calculated 3 > 20; quit;  
C.proc sql; create table two as select job, level, salary * 0.1 as BONUS from one where bonus * 0.1 > 20; quit;  
D.proc sql; create table two as select job, level, salary * 0.1 as BONUS from one where calculated bonus > 20; quit;  

> Answer: D

---



22. Given the SAS data set ONE: 

> ONE CATEGORY AGE M 28 M 25 M 28 M 33 F 18 F 25 F 35 

The following SAS program is submitted: 

> proc sql; 
> create table two as select distinct age from one where age < 33; 
> quit; 

How many rows are written to the SAS data set TWO? 

A.0  
B.3  
C.4  
D.5  
 

> Answer: B

---



23. Given the SAS data set 

> ONE: ONEGROUP SUM A 765 B 123 C 564 

The following SAS program is submitted: 

> data _null_; 
> set one; call s  ymput(GROUP,SUM); 
> stop; 
> run; 

What is the result when the program finishes execution?  

A.Macro variable A has a value of 765.  
B.Macro variable C has a value of 564.  
C.Macro variable GROUP has a value of 564.  
D.Macro variable GROUP has a value of SUM.  

> Answer: A

---



24. The following SAS program is submitted: 

> %let first = yourname; 
> %let last = first; 
> %put &&&last; 

What is written to the SAS log?  

A.first  
B.&&first  
C.yourname  
D.&yourname  

> Answer: C

---



25. The following SAS program is submitted: 

> %let a = cat; 
> %macro animal(a = frog); 
> %let 

> a = bird; %mend; 
> %animal(a = pig) %put a is &a; 

What is written to the SAS log?  

A.a is cat  
B.a is pig  
C.a is bird  
D.a is frog  

> Answer: A

---



26. Given the SAS data set SASUSER.HIGHWAY: 

> SASUSER.HIGHWAY STEERINGSEATBELTSPEED STATUS COUNT absentNo0-29serious 31 absentNo0-29not 1419 absentNo30-49serious 191 absentno30-49not 2004 absentno50+serious 216 

The following SAS program is submitted: 

> %macro highway; 
> proc sql noprint; 
> %let numgrp = 6; 
> select distinct status 
> into :group1 - :group&numgrp 
> from sasuser.highway; 
> quit; 
> %do i = 1 %to &numgrp; 
> proc print data = sasuser.highway; 
> where status = "&&group&i"; 
> run; 
> %end; 
> %mend; 
> %highway 

How many reports are produced? 
A.0  
B.2  
C.5  
D.6  

> Answer: B

---



27. The following SAS program is submitted: 

> %macro execute; 
> proc print data = sasuser.houses; 
> run; %end; 
> %mend; 
> %execute 

Which statement completes the program so that it executes on Tuesday?  

A.%if &sysday = Tuesday %then %do;  
B.%if &sysday = 'Tuesday' %then %do;  
C.%if &sysdate = Tuesday %then %do;  
D.%if &sysdate = 'Tuesday' %then %do;  

> Answer: A

---



28. Assume today is Tuesday, August 15, 2006. 

Which statement, submitted at the beginning of a SAS session, assigns the value Tuesday, August 15, 2006 to the macro variable START?  

A.%let start = %eval(today(), weekdate.);  
B.%let start = %sysfunc(today(), weekdate.);  
C.%let start = %sysexec(today(), weekdate.);  
D.%let start = %sysevalf(today(), weekdate.);  

> Answer: B

---



29. The following SAS program is submitted: 

> %let value = 0.5; 
> %let add = 5; 
> %let newval = %eval(&value + &add); 

What is the value of the macro variable NEWVAL?  

A.5 
B.5.5  
C.0.5 + 5  
D.null  

> Answer: D

---


 
30. The following SAS program is submitted: 

> %macro test(var); 
> %let jobs = BLACKSMITH WORDSMITH SWORDSMITH; 
> %let type = %index(&jobs, &var); 
> %put type = &type; 
> %mend; 
> %test(SMITH) 

What is the value of the macro variable TYPE when the %PUT statement executes?  

A.0  
B.3  
C.6  
D.null  

> Answer: C

---



31. Which of the following successfully creates and displays a macro variable with the value Patel's Restaurant? 

A.%let name = Patel's Restaurant; %put &name;  
B.%let name = Patel%'s Restaurant; %put &name; ^^^^ 
C.%let name = %bquote(Patel's Restaurant); %put &name;  
D.%let name = %bquote(Patel%'s Restaurant); %put &name;  

> Answer: C

---



32. The SAS data set ONE has a variable X on which an index has been created. The data sets ONE and THREE are sorted by X. The following SAS program is submitted: 

> data two; 
> set three; 
> set one key = X; 
> run; 

What is the purpose of including the KEY= option in the program?  
 
A.It forces SAS to use the index X.  
B.It re-creates the index X on the output data set TWO.  
C.It instructs SAS to do a sequential read of both sorted data sets.  
D.It gives SAS the option to use the index X or to do a sequential read of the data set ONE. 

> Answer: A

---



33. The SAS data set ONE contains the variables X, Y, Z, and W. 

The following SAS program is submitted: 

> proc transpose data = one out = trans name = new; 
> by x; 
> var y; 
> run; 

What are the names of all of the columns created by the TRANSPOSE procedure?  

A.new, X, and Y only  
B.new, X, and COL1 only  
C.new, Y, and COL1 only  
D.new, X, Y, and _COL1_    

> Answer: B

---



34. Given the variable attributes of SAS data sets ONE and TWO: 

> ONE TWO VariableType Len Variable Type Len sales Num 8 budget Num8 year Num 8 sales Char8 year Num8 Both data sets are sorted by the variable YEAR. 

The following SAS program is submitted: 

> data three; 
> merge one two; 
> by year; 
> run; 

What is the result?  

A.Data set THREE is created with two variables.  
B.Data set THREE is created with three variables.  
C.Data set THREE is created and WARNING messages are written to the SAS log.  
D.Data set THREE is not created. ERROR and WARNING messages are written to the SAS log.  

> Answer: D

---



35. The data set ONE has a simple index X. The index X needs to be deleted and a composite index Y on the variables X and W created. 

Which statement describes using PROC DATASETS to complete this task?  

A.The index X should be deleted first so that the index Y can reuse the space.  
B.The index X must be deleted first because the index Y cannot be created until the index X is deleted.  
C.The index Y should be created first to take advantage of the values stored in the simple index X.  
D.The order of the deleting the index X and creating the index Y does not im  pact resource utilization.  

> Answer: A

---


36. Given the SAS data sets ONE and TWO: 

> ONETWO YEARQTR BUDGETYEARQTR SALES 20013 50020014 300 20014 40020021 600 20021 700 

The following SAS program is submitted: 

> proc sql; 
> select one.*, 
> sales from one, two;
> quit; 

Which report is generated?  

A.YEAR QTR BUDGET SALES 2001 3 500 300 2001 4 400 . 2002 1 700 600  
B.YEAR QTR BUDGET SALES 2001 3 500 . 2001 4 400 300 2002 1 700 600   
C.YEAR QTR BUDGET SALES 2001 3 500 300 2001 4 400 300 2002 1 700 600  
D.YEAR QTR BUDGET SALES 2001 3 500 300 2001 4 400 300 2002 1 700 300 2001 3 500 600 2001 4 400 600 2002 1 700 600  

> Answer: D

---


37. The SAS data set ONE contains fifty million observations and contains the variables

> PRICE, QUANTITY, FIXED, and VARIABLE. 

Which SAS program successfully creates three new variables TOTREV, TOTCOST, and PROFIT and requires the least amount of 
CPU resources to be processed?  

A.data two; set one; totrev = sum(price * quantity); totcost = sum(fixed,variable); if totrev > 1000; profit = sum(totrev,-totcost); run;  
B.data two; set one; totrev = sum(price * quantity); if totrev > 1000; totcost = sum(fixed,variable); profit = sum(totrev,-totcost); run;  
C.data two; set one; totrev = sum(price * quantity); where totrev > 1000; totcost = sum(fixed,variable); profit = sum(totrev,-totcost); run;  
D.data two; set one; where totrev > 1000; totrev = sum(price * quantity); totcost = sum(fixed,variable); profit = sum(totrev,-totcost); run;  

> Answer: B

---


38. The following SAS program is submitted. 

> filename sales ('externa  l file1' 'external file2'); 
> data new; 
> infile sales; 
> input date date9. company $ revenue; 
> run; 

What is the result of including the FILENAME statement in this program?  
 
A.The FILENAME statement produces an ERROR message in the SAS log.  
B.The FILENAME statement associates SALES with external file1 followed by external 
file2.  
C.The FILENAME statement associates SALES with external file2 followed by external 
file1.  
D.The FILENAME statement forces the INFILE statement to alternate reading from 
external file 1 and external file 2.  

> Answer: B

---


39. Given the SAS data sets 

> ONE and TWO: ONE TWOCOMMON XCOMMON Y A 10 A 1 A 13 A 3 A 14 B 4 B 9 B 2 

The following SAS program is submitted: data combine; set one; set two; run; What data values are stored in data set COMBINE?  

A.COMMON XY A 10 1 A 13 3 A 14 3 B 9 4  
B.COMMON XY A 10 1 A 13 3 B 14 4 B 9 2  
C.COMMON XY A 10 1 A 13 3 A 14 . B 9 4 B . 2  
D.COMMON XY A 10 1 A 13 1 A 14 1 A 10 3 A 13 3 A 14 3 B 9 4 B 9 2  

> Answer: B

---


40. Which statement about compressed SAS data sets is always true?  

A.Deleted observation space is never reused.  
B.Each observation is treated as a single string of bytes.  
C.An updated observation is stored in its original location.  
D.New observations are added to the end of the SAS data set.  

> Answer: B

---


41. Given the SAS data set 

> SASUSER.HOUSES: SASUSER.HOUSES STYLE RANCH 
> RANCH CONDO CONDO CONDO 

The following SAS program is submitted: 

> data sasuser.ranch sasuser.condo / view = sasuser.ranch; 
> set sasuser.houses; 
> if style = 'RANCH' then output sasuser.ranch; 
> else if style = 'CONDO' 
> then output sasuser.condo; 
> run; 

What is written to the SAS log?  

A.NOTE: DATA STEP view saved on file SASUSER.RANCH.  
B.ERROR: A SAS data step view and a SAS data file cannot be created in the same DATA step.  
C.NOTE: DATA STEP view saved on file SASUSER.RANCH.NOTE: DATA STEP view saved on file SASUSER.CONDO.  
D.NOTE: DATA STEP view saved on file SASUSER.RANCH.NOTE: The data set SASUSER.CONDO has 3 observations and 1 variables.  

> Answer: A

---


42. The following SAS program is s  ubmitted: 

> data temp; array points{3,2} _temporary_ (10,20,30,40,50,60); 
> score = points{2,1} run; 

What is the value of the variable SCORE in the data set TEMP?  

A.20  
B.30  
C.40 
D.(missing numeric)  

> Answer: B

---


43. The following SAS program is submitted: 

> data new (bufsize = 6144 bufno = 4); 
> set old; 
> run; 

What is the difference between the usage of BUFSIZE= and BUFNO= options? 

A.BUFSIZE= specifies the size of the input buffer in bytes; BUFNO= specifies the number of input buffers.  
B.BUFSIZE= specifies the size of the output buffer in bytes; BUFNO= specifies the number of output buffers.  
C.BUFSIZE= specifies the size of the input buffer in kilobytes; BUFNO= specifies the number of input buffers.  
D.BUFSIZE= specifies the size of the output buffer in kilobytes; BUFNO= specifies the number of output buffers.  

> Answer: B

---


44. Which SAS program uses the most memory resources for output buffers?  

A.data new(bufsize = 1000 bufno = 2); set temp;run;  
B.data new(bufsize = 1000 bufno = 5); set temp;run;  
C.data new(bufsize = 2000 bufno = 3); set temp;run;  
D.data new(bufsize = 4000 bufno = 1); set temp;run;  

> Answer: C

---


 
45. The SAS data set TEMP has the following distribution of values for variable A: 

> TEMPAFrequency 1 500,000 2 500,000 6 7,000,000 8 3,000 

Which SAS program requires the least amount of CPU resources to be processed?  

A.data new; set temp; if a = 8 then b = 'Small '; else if a in(1, 2) then b = 'Medium'; else if a = 6 then b = 'Large'; run;  
B.data new; set temp; if a in (1, 2) then b = 'Medium'; else if a = 8 then b = 'Small'; else if a = 6 then b = 'Large'; run;  
C.data new; set temp; if a = 6 then b = 'Large '; else if a in (1, 2) then b = 'Medium'; else if a = 8 then b = 'Small'; run;  
D.data new; set temp; if a in (1, 2) then b = 'Medium'; else if a = 6 then b = 'Large '; else if a = 8 then b = 'Small'; run;  

> Answer: C

---


46. The variable TOTOBS has a value of 123, which represents the total number of observations in a SAS data set. 

Which assignment statement correctly creates the variable PTOBS that guarantees a valid observation number in that SAS data set? 

A.ptobs = ranuni(0) * totobs;  
B.ptobs = int(ranuni(0) * totobs);  
C.ptobs = ceil(ranuni(0) * totobs);  
D.ptobs = floor(ranuni(0) * totobs);  

> Answer: C

---


 
47. What is the purpose of the IDXNAME= data set option?  

A.It instructs SAS to name a composite index. 
B.It instructs SAS to name and store a specific index.  
C.It instructs SAS to use a specific index for WHERE processing.  
D.It instructs SAS to read the data sequentially if the index usage increases CPU 
resources.  

> Answer: C

---


48. Which SAS procedure changes the name of a permanent format for a variable stored in a SAS data set?  

A.MODIFY  
B.FORMAT  
C.REGISTRY  
D.DATASETS  

> Answer: D

---


49. Which statement(s) in the DATASETS procedure alter(s) the name of a SAS data set stored in a SAS data library?  

A.RENAME statement only  
B.CHANGE statement only  
C.MODIFY and RENAME statements  
D.MODIFY and CHANGE statements  
 

> Answer: B

---


50. Which SAS integrity constraint type ensures that a specific set or range of values are the only values in a variable?  

A.CHECK  
B.UNIQUE  
C.NOT NULL  
D.PRIMARY KEY  

> Answer: A

---


51. Given the SAS dataset ONE 

> ONENAMESALARY Hans 200 Maria 205 Jose 310 Ariel 523 

The following SAS program is submitted: 

> proc sql; 
> from one; 
> quit; 

The following output is desired: 

> SALARY BONUS 200 20 205 20.5 310 31 523 52.3 

Which SQL procedure clause completes the program and generates the desired output?  

A.select salary, salary * .10 var = BONUS  
B.select salary, salary * .10 name = 'BONUS'  
C.select salary, salary * .10 label = 'BONUS'  
D.select salary, salary * .10 column = 'BONUS'  

> Answer: C

---


52. Given the SAS dataset ONE ONE SALARY 200 205 . 523 

The following SAS program is submitted: 

> proc sql; 
>select * from one ; 
> quit; 

The following output is desired: SALARY 
 
200 205 523 

Which WHERE expression completes the program and generates the desired output?  

A.where salary ne null  
B.where salary is not .  
C.where salary ne missing  
D.where salary is not missing  

> Answer: D

---



53. Which SQL procedure clause allows for dynamically assigning a library when creating an SQL procedure view?  

A.FROM  
B.USING  
C.CONNECT  
D.LIBNAME  

> Answer: B

---



54. Given the SAS data sets ONE and TWO: 

> ONETWOYEARQTRBUDGETYEARQTRSALES 20013 50020014 300 20014 40020021 600 20031 350 

The following SAS program is submitted: 

> proc sql; 
> select two.*, 
> budget from one two on one.year = two.year; 
> quit; 

The following output is desired: YEAR QTR BUDGET SALES 2001 4 300 500 2001 4 300 400 2002 1 600 . 

Which JOIN operator completes the program and generates the desired output?  
 
A.LEFT JOIN  
B.RIGHT JOIN  
C.FULL JOIN  
D.INNER JOIN  

> Answer: B

---



55. Given the SAS data sets ONE and TWO: 

> ONETWO YEAR QTR BUDGETYEARQTRSALES 20013 50020014 300 20014 40020021 600 20031 350 

The following SAS program is submitted: 

> proc sql; 
> select two.*, budget 
> from one two on one.year = two.year; 
> quit; 

The following output is desired: 

> YEAR QTR BUDGET SALES 2001 4 300 500 2001 4 300 400 2002 1 600 . . . . 350 

Which JOIN operator completes the program and generates the desired output?  

A.LEFT JOIN  
B.RIGHT JOIN  
C.FULL JOIN  
D.INNER JOIN  

> Answer: C

---



56. Given the SAS data sets CLASS1 and CLASS2: 

> CLASS1CLASS2 NAME COURSENAME COURSE Lauren MATH1Smith MATH2 Patel MATH1Farmer MATH2 Chang MATH1Patel MATH2 Hillier MATH2 

The following SAS program is submitted: 

> proc sql; 
> select name from CLASS1 select name from CLASS2; 
> quit; 

The following output is desired: 

> NAME Chang Lauren 

Which SQL set operator completes the program and generates the desired output?  

A.UNION  
B.EXCEPT  
C.INTERSECT  
D.OUTER UNION CORR  

> Answer: B

---



57. Given the SAS data sets CLASS1 and CLASS2: CLASS1CLASS2NAME COURSENAME COURSE Lauren MATH1Smith MATH2 Patel MATH1Farmer MATH2 
Chang MATH1Patel MATH2 Chang MATH3Hillier MATH2 

The following SAS program is submitted: 

> proc sql; 
> select name from CLASS1 select name from CLASS2; 
> quit; 

The following output is desired: NAME Chang Chang Lauren Which SQL set operator completes the program and generates the desired output?  
A.UNION ALL  
B.EXCEPT ALL  
C.INTERSECT ALL  
D.OUTER UNION ALL  

> Answer: B

---



58. Given the SAS data sets MATH1A and MATH1B: MATH1AMATH1B 
 
NAME FINAME FI Lauren LSmith M Patel ALauren S Chang ZPatel A Hillier R The 
following SAS program is submitted: proc sql; select * from MATH1A select * from 
MATH1B; quit; The following output is desired: NAME FI Patel A Which SQL set operator 
completes the program and generates the desired output?  

A.UNION  
B.EXCEPT  
C.INTERSECT  
D.OUTER UNION CORR  

> Answer: C

---



59. Given the following SAS program: 

> proc sql; 
> select name, salary, birthdate from employee 
> where 500 = (select amount from sales where employee.name = sales.name); 
> quit; 

Which SQL procedure program produces the same output?  

A.proc sql; select sales.name, salary, birthdate from employee, sales where employee.name = sales.name and amount = 500; quit;  
B.proc sql; select name, salary, birthdate from employee where select amount from sales where employee.name = sales.name = 500; quit;  
C.proc sql; select name, salary, birthdate from employee, sales where name = name and amount = 500; quit;  
D.proc sql; select (select sales.name from sales where amount = 500), salary, birthdate from employee where employee.name = sales.name; quit;  

> Answer: A

---


 

60. Which SQL procedure program deletes rows from the data set CLASS?  

A.proc sql; alter from class delete where age < (select stop_age from threshold); quit; 
B.proc sql; delete from class where age < (select stop_age from threshold); quit;  
C.proc sql; modify table class delete where age < (select stop_age from threshold); quit;    
D.proc sql; select * from class delete where age < (select stop_age from threshold); quit; 

> Answer: B

---



61. Which of the following is true about a noncorrelated subquery in SAS?  

A.The outer query executes before the subquery.  
B.The subquery executes once before the outer query.  
C.The subquery creates a data set in the WORK library.  
D.The subquery can reference tables in the FROM clause in the outer query.  

> Answer: B

---



62. Given the SAS data sets EMPLOYEE and NEWEMPLOYEE: 

> EMPLOYEE NEWEMPLOYEENAME DEPT NAMESALARY Alan Sales Michelle 50000 Michelle Sales Paresh 60000 

A SAS program is submitted and the following is written to the SAS 

> log: 530 proc sql; 
> 531 select dept, name 
> 532 from employee 
> 533 where name = (select name from newemployee where salary > 40000); ERROR: Subquer  y evaluated to more than one row. 
> 534 quit; 

What would allow the program to successfully execute without errors?  

A.Change the equal sign to IN.   
B.Qualify the column names with the table names.  
C.Add an observation with a name of Paresh to the EMPLOYEE data set.  
D.Replace line 533 withwhere employee.name = (select name from newemployee where 
salary > 40000);.  

> Answer: A

---



63. The following SAS program is submitted: 

> proc sort data=class out=class1 nodupkey; 
> by name course ; 
> run; 

Which SQL procedure program produces the same results?  

A.proc sql; create table class1 as select distinct name, course from class; quit;  
B.proc sql; create table class1 as select nodup name, course from class; quit;  
C.proc sql; create table class1 as select exclusive name, course from class; quit;  
D.proc sql; create table class1 as select name, course from class order by distinct name; quit;  

> Answer: A

---



64. Given the SAS data sets ONE and TWO: 

> ONETWOIDNAMEID SALARY 112 Smith243 150000 243 Wei355 45000 457 Jones523 75000 

The following SAS program is submitted: 

> data combine; 
> merge one two; 
> by id; 
> run; 

Which SQL procedure program produces the same results?  

A.proc sql; create table combine as select coalesce(one.id, two.id) as id, name, salary from one full join two on one.id = two.id; quit;
B.proc sql; create table combine as select one.id, name, salary from one inner join two on  one.id = two.id; quit;  
C.proc sql; create table combine as select coalesce(one.id, two.id) as id, name, salary from one, two where one.id = two.id; quit    ; 
D.proc sql; create table combine as select one.id, name, salary from one full join two where one.id = two.id; quit;  

> Answer: A

---



65. The following SAS program is submitted: 

> proc append data = M base = F; 
> run; 

Which SQL procedure program will produce the same results?  

A.proc sql; insert into F select * from M; quit;  
B.proc sql ; select * from F outer union corr select * from M; quit;  
C.proc sql ; create table F as select * from F intersect select * from M; quit;  
D.proc sql ; create table F as select * from F intersect corr select * from M; quit;  

> Answer: A

---



66. Which DICTIONARY table provides information on all the tables containing a variable named LASTNAME?  

A.DICTIONARY.TABLES  
B.DICTIONARY.COLUMNS  
C.DICTIONARY.MEMBERS  
D.DICTIONARY.VARIABLES  

> Answer: B

---


 

67. Which of the following is true about the DICTIONARY.TABLES table?  

A.It can be edited in the SAS viewtable window.  
B.New rows and columns can be inserted directly into DICTIONARY.TABLES.  
C.It contains information about all the SAS data sets in the current SAS session.     
D.It can be directly referenced by both the SQL procedure and the SAS DATA step. 

> Answer: C

---



68. Given the following partial SAS log: NOTE: SQL table SASHELP.CLASS was created like: create table SASHELP.CLASS( bufsize=4096 ) ( Name char(8), Gender char(1), Age num, Height num, Weight num ); 

Which SQL procedure statement generated this output? 

A.LIST TABLE  
B.CREATE TABLE  
C.DESCRIBE TABLE  
D.VALIDATE TABLE  

> Answer: C

---



69. The data set SASHELP.CLASS contains the variables NAME, GENDER, AGE, HEIGHT, WEIGHT. The following SAS program is submitted: 

> proc sql; 
> create index firstname on sashelp.class(name); 

What is the result of the program execution? 

A.An index called FIRSTNAME is created.  
B.The FIRSTNAME index does not get created because there is no QUIT statement.  
C.An error message is output to the log because the variable in parenthesis is not in uppercase.  
D.An error message is output to the log because the index name does not match the variable name.  

> Answer: D

---



70. The following SAS program is submitted: 

> proc sql; 
> insert into company.employee(name, salary, birthdate) 
> select name, salary, birthdate 
> from work.newemployees; 

What is the result of the program execution?  

A.A report of the observations from WORK.NEWEMPLOYEES is created.  
B.Three macro variables named NAME, SALARY, and BIRTHDATE are created.  
C.An error message is written to the SAS log because the INSERT statement is invalid in the SQL procedure.  
D.Observations from WORK.NEWEMPLOYEES are appended to the COMPANY.EMPLOYEE data set.  

> Answer: D

---



71. A SAS program is submitted and the following is written to the SAS log: 

> 15 %let col1 = dept; 
> 16 %let data = company; 
> 17 
> 18 proc sql; 
> 19 select * 
> 20 from &data, employee 
> 21 where &data.&col1 = employee.name; 
> 22 quit; 

> ERROR: The following columns were not found in the contributing tables: companydept. 

What caused the error?  

A.The data set COMPANY does not contain the variable DEPT.  
B.There should be a second period after &DATA in the WHERE clause.  
C.There should be two ampersands in front of DATA in the WHERE clause.  
D.There should be two ampersands in front of COL1 in the WHERE clause.  

> Answer: B

---



72. Which of the following is true about SAS automatic macro variables?

A.They are always read only.  
B.All can have their value changed by a user.  
C.Some can have the value changed by a user.  
D.They can only be used inside of a macro definition.  

> Answer: C

---



73. The following SAS program is submitted: 

> %let cola = dept; 
> %let num = a; 
> proc print data = company; 
> var; 
> run; 

What is the correct code to complete the VAR statement and print the variable DEPT?  

A.&COL&NUM  
B.&&COL&NUM  
C.&&COL&&NUM  
D.&&&COL&&NUM  

> Answer: B

---



74. The following SAS program is submitted: 

> %macro one(input); 
> %two %put the value is &date; 
> %mend; 
> %macro t  wo; 
> data _null_; 
> call symput('date', '12SEP2008'); 
> run; 
> %mend; 
> %let date = 31DEC2006; 
> %one(&date) 

What is the result when the %PUT statement executes?  

A.A macro variable DATE with the value 12SEP2008 is retrieved from the global symbol table.  
B.A macro variable DATE with the value 31DEC2006 is retrieved from the global symbol table.  
C.A macro variable DATE with the value 12SEP2008 is retrieved from the local symbol table for the ONE macro.  
D.A macro variable DATE with the value 12SEP2008 is retrieved from the local symbol table for the TWO macro.  

> Answer: A

---



75. The following SAS program is submitted: 

> %macro one(input); 
> %two %mend; %macro two; 
> data _null_; 
> call symputx('date', '12SEP2008', 'L'); 
> run; 
> %put the value is &date; 
> %mend; 
> %let date = 31DEC2006; 
> %one(&date) 

What is the result when the %PUT statement executes?  

A.A macro variable DATE with the value 12SEP2008 is retrieved from the global symbol table.  
B.A macro variable DATE with the value 31DEC2006 is retrieved from the global symbol table.  
C.A macro variable DATE with the value 12SEP2008 is retrieved from the local symbol table for the ONE macro.  
D.A macro variable DATE with the value 12SEP2008 is retrieved from the local symbol table for the TWO macro.  

> Answer: D

---



76. The following SAS program is submitted: 

> %macro one(input); 
> %two %mend; 
> %macro two; 
> data _null_; 
> call symputx('date', '12SEP2008', 'G'); 
> run; 
> %put the value is &date; 
> %mend; 
> %let date = 31DEC2006; 
> %one(&date) 

What is the result when the %PUT statement executes?  

A.A macro variable DATE with the value 12SEP2008 is retrieved from the global symbol table.  
B.A macro variable DATE with the value 12SEP2008 is retrieved from the local symbol table for the ONE macro.  
C.A macro variable DATE with the value 12SEP2008 is retrieved from the local symbol table for the TWO macro.  
D.A macro variable DATE with the value 31DEC2006 is retrieved from the local symbol table for the TWO macro.  

> Answer: A

---



77. The following SAS program is submitted: 

> %macro let(name); 
> proc print data = &name; 
> run; 
> %mend; 
> %let(sashelp.class) 

Why does the program fail to execute?  

A.There is no equal sign after the parameter name.  
B.The word LET is a reserved word for macro names.  
C.There should be no parentheses around SASHELP.CLASS.  
D.The %LET call needs a semicolon at the end of the statement.  

> Answer: B

---



78. The following SAS program is submitted: 

> %macro print(dsn = sashelp.class, var1, var2 = name); 
> proc print data = &dsn; 
> var &var1 &var2; 
> run; 
> %mend; 
> %print(dsn = sashelp.prdsale, age name, var2 =height) 

What is the result?  

A.The value of the macro variable VAR1 is age.  
B.The value of the macro variable VAR1 is null.  
C.The value of the macro variable VAR1 is age name.  
D.The macro variable VAR1 has no value; the macro failed to compile.  

> Answer: D

---



79. The following SAS program is submitted: 

> %macro test; 
> data out; 
> set sashelp.prdsale end = final; 
> if predict > 500 then counter + 1; 
> if final then do; 
> end; 
> run; 
> %mend; 
> %test 

Which statement successfully completes the program, creates a global macro variable named TOTAL and assigns it the value from the variable COUNTER?  

A.%let total = counter;  
B.%global total = counter;  
C.call symput('counter', total);  
D.call symput('total', counter);  
 

> Answer: D

---



80. The following SAS program is submitted: 

> %let rc = Begin; 
> %macro test; 
> data out; 
> set sashelp.prdsale nobs = totalobs; 
> if totalobs > 10 then do; 
> %let rc = high; 
> end; 
> else do; 
> %let rc = low; 
> end; 
> run; 
> %mend; 
> %let rc = Before Execution; 
> %test 

The data set SASHELP.PRDSALE has 50 observations. 

What is the value of the variable RC when the macro finishes execution?  

A.low  
B.high  
C.Begin  
D.Before Execution  

> Answer: A

---



81. At the start of a new SAS session, the following program is submitted: 

> %macro one; 
> data _null_; 
> call symput('proc', 'means'); 
> run; 
> proc &proc data = sashelp.class; 
> run; 
> %mend; 
> %one() 

What is the result?  

A.The macro variable PROC is stored in the local symbol table. 
B.The macro variable PROC is stored in the global symbol table.  
C.The macro variable PROC is stored in the SAS catalog WORK.SASMACR.  
D.The program fails to execute because PROC is a reserved word.  

> Answer: B

---


 

82. The following SAS program is submitted: 

> %macro cols1; 
> name age; 
> %mend; 
> %macro cols2; 
> height weight; 
> %mend; 
> proc print data = sashelp.class; 
> run; 

Which VAR statement successfully completes the program and produces a report?  

A.var %cols2 %cols1;  
B.var height %cols1;  
C.var %cols1 height;  
D.var %cols1 %cols2 height;  

> Answer: B

---



83. The following SAS program is submitted: 

> options mstored sasmstore = sasuser; 
> %macro output / store   source; 
> %if &syslast =_NULL_ %then %do; 
> %put No data set; 
> %end; 
> %else %do; 
> proc print data = &syslast; 
> run; 
> %end; 
> %mend; 

Which program accesses the source program of the compiled macro OUTPUT and writes it to the SAS log? 

A.%display output;  
B.%output / source;  
C.%copy output / source;  
D.options mprint; %output  

> Answer: C

---



84. The following SAS program is submitted: 

> %let value = 9; 
> %let add = 5; 
> %let newval = %eval(&value / &add); 

What is the value of the macro variable NEWVAL?

A.1   
B.2  
C.1.8  
D.null  

> Answer: A

---



85. Given the SAS data set OURDATA: 

> OURDATAObsproduct sales 1 OR 1000 2 NE 1200 3 MM 1450 

After submitting a SAS program, the following is written to the SAS log: 

> 70 %macro a; 
> 71 data _null_; 
> 72 set ourdata; 
> 73 call symput('product'!!left(_n_), product); 
> 74 run; 
> 75 %if &product1 = OR %then %do; 
> 76 proc means data = ourdata; 
> 77 run; 
> 78 %end; 
> 79 %mend; 
> 80 %a NOTE: Numeric values have been converted to character values at the places given by: (Line):(Column). 73:66 NOTE: There were 3 observations read from the data set WORK.OURDATA. NOTE: DATA statement used (Total process time): real time 0.00 seconds cpu time 0.00 seconds ERROR: A character operand was found in the %EVAL function or %IF condition where a numeric operand is required. The condition was: &product1=OR ERROR: The macro A will stop executing. 

Which statement replaces the code in line 75 to successfully complete the program?  

A.%if &product1 = %bquote(OR) %then %do;  
B.%if %bquote(&product1) = OR %then %do;  
C.%if %bquote(&product1 = OR) %then %do;  
D.%if %bquote(&product1) = %bquote(OR) %then %do;  

> Answer: D

---



86. The following SAS program is submitted: 

> %macro check(num = 4); 
> %let result = %eval(&num gt 5); 
> %put result is &result; 
> %mend; 
> %check(num = 10) 

What is written to the SAS log?  

A.result is 0  
B.result is 1 
C.result is 10 gt 5  
D.result is true  

> Answer: B

---



87. The following SAS program is submitted: 

> %macro check(num = 4); 
> %let result = %sysevalf(&num + 0.5); 
> %put result is &result; 
> %mend; 
> %check(num=10) 

What is written to the SAS log?  

A.result is  
B.result is 10  
C.result is 10.5  
D.result is 10 + 0.5  

> Answer: C

---



88. The macro variable STATEMENT should resolve to: 

> proc print data = sashelp.class; 

Which of the following statements successfully creates this result?  

A.%let statement = proc print data = sashelp.class;;  
B.%let statement = proc print data = sashelp.class;; 
C.%let statement = %bquote(proc print data = sashelp.class;);  
D.%let statement = %bquote(proc print data = sashelp.class;);  

> Answer: C

---



89. Given the data set 

> SASHELP.CLASS: SASHELP.CLASS NAME AGE Mary 15 Philip 16 Robert 12 Ronald 15 

The following SAS program is submitted: 

> %let value = Philip; 
> proc print data = sashelp.class; 
> run; 

Which WHERE statement successfully completes the program and produces a report?  

A.where upcase(name) = upcase(&value);  
B.where upcase(name) = %upcase(&value);  
C.where upcase(name) = "upcase(&value)";  
D.where upcase(name) = "%upcase(&value)";  

> Answer: D

---



90. The following SAS program is submitted: 

> options mprint; 
> %macro test(parm); 
> proc &parm data = sashelp.prdsale; 
> run; 
> %mend; 
> %test(print) 

What is the result of the MPRINT option?  


A.It has no effect in this example.  
B.It writes macro execution messages to the SAS log.  
C.It writes the original program code inside the macro definition to the SAS log.  
D.It echoes the text sent to the SAS compiler as a result of macro execution in the SAS 
log.  
 

> Answer: D

---



91. The following SAS program is submitted: 

> %macro loop; 
> data one; 
> %do I = 1 %to 3; 
> var&I = &i; 
> %end; 
> run; 
> %mend; 
> %loop 

After this program executes, the following is written to the SAS log: 

> (LOOP): Beginning execution. (LOOP): %DO loop beginning; 
> index variable I; 
> start value is 1; 
> stop value is 3; 
> by value is 1. 

> (LOOP): %DO loop index variable I is now 2; 
> loop will iterate again. 
> (LOOP): %DO loop index variable I is now 3;
> loop will iterate again. 
> (LOOP): %DO loop index variable I is now 4; 
> loop will not iterate again. 
> (LOOP): Ending execution. 

Which SAS System option displays the notes in the SAS log? 

A.MACRO 
B.MLOGIC  
C.MPRINT  
D.SYMBOLGEN  

> Answer: B

---



92. Given the following partial SAS log: 

> 29 %macro test; 
> 30 %if &a = 5 %then %do; 
> 31 proc print data = sashelp.prdsale; 
> 32 run; 
> 33 %end; 
> 34 %else %put a is not 5; 
> 35 %mend; 
> 36 
> 37 %let a = 5; 
> 38 %test (TEST): Beginning execution. : Macro variable A resolves to 5 (TEST): %IF condition &a = 5 is TRUE (TEST): proc print data = sashelp.prdsale; (TEST): 
> run; 

Which SAS System option prevents the display in the SAS log of the note proc print data = sashelp.prdsale;?  

A.NOMPRINT   
B.NOSOURCE  
C.NOSOURCE2  
D.NOMAUTOLOCDISPLAY  

> Answer: A

---



93. At the start of a new SAS session, which keyword on the %PUT statement displays macro variables created by the SAS System?  

A._ALL_    
B._AUTO_    
C._ GLOBAL _    
D._SYMBOLTABLE_    

> Answer: A

---



94. The following SAS program is submitted: 

> %macro location(country); 
> proc sql ; 
> select 'sales', * into: 
> dept from sashelp.class; 
> quit; 
> %put _global_; 
> %mend; 
> %let company = ABC; 
> %location(US) 

Which macro variable(s) is/are written to the SAS log?  

A.DEPT only  
B.COMPANY only  
C.COMPANY and DEPT only  
D.COMPANY, COUNTRY and DEPT  

> Answer: B

---


 

95. The following SAS program is submitted: 

> %macro location; data _null_; 
> call symput ('dept', 'sales'); 
> run; 
> %let country = Germany; 
> %put _global_; 
> %mend; 
> %let company = ABC; 
> %location 

Which macro variables are written to the SAS log?  

A.COMPANY only  
B.COMPANY and DEPT only  
C.COMPANY and COUNTRY only  
D.COMPANY, COUNTRY and DEPT  

> Answer: B

---



96. The following SAS program is submitted: %let dept = prod; %let prod = merchandise; 

The following message is written to the SAS log: 

> the value is "merchandise" Which SAS System option writes this message to the SAS log?  

A.%put the value is "&&&dept";  
B.%put the value is ""&&&dept"";  
C.%put the value is '"'&&&&dept'"';  
D.%put the value is %quote(&&&dept);  

> Answer: A

---



97. Given the SAS data sets ONE and TWO: 

> ONE TWO X YSUMY A 10 45 A 13 A 14 B 9 

The following SAS DATA step is submitted: 

> data combine; if _n_ = 1 then set two; set one; 
> run; 

What data values are stored in data set COMBINE?  

A.SUMY X Y 45 A 10  
B.SUMY X Y 45 A 10 . A 13 . A 14 . B 9  
C.SUMY X Y 45 A 10 45 A 13 45 A 14 45 B 9  
D.An ERROR message is written to the SAS log and the data set COMBINE is not created.  

> Answer: C

---



98. The following SAS program is submitted: 

> data new; 
> do I = 1, 2, 3; 
> nextfile = compress('March' || I ); 
> infile abc filevar = nextfile end = eof; 
> do until (eof); 
> input dept $ sales; 
> end; 
> run; 

What is the purpose of the FILEVAR = option on the INFILE statement? 

A.It names the variable NEXTFILE, whose value is a SAS file reference.  
B.It names the variable NEXTFILE, whose value is output to the SAS data set NEW.  
C.It names the variable NEXTFILE, whose values point to an aggregate storage location. 
D.It names the variable NEXTFILE, whose change in value causes the INFILE statement to open a new input file.  

> Answer: D

---



99. Given the following OPTIONS statement: 

> libname A 'SAS library reference';
> libname F 'SAS library reference';
> options fmtsearch = (A F.X); 

What is the second location searched for formats?  

A.F.X  
B.A.FORMATS  
C.WORK.FORMATS  
D.SAS supplied formats  

> Answer: C

---



100. What describes the COMPRESS= BINARY data set option?  

A.It cannot be used with character data.  
B.It handles simple repetitions rather than patterns.  
C.It takes more CPU resources to uncompress than COMPRESS= CHAR.  
D.It is most efficient with observations less than one hundred bytes in length.  

> Answer: C

---



101. The following SAS program is submitted: 

> data temp; 
> length a 1 b 3 x; 
> infile 'file reference'; 
> input a b x; 
> run; 

What is the result?  

A.The data set TEMP is created, but variable X is not created.  
B.The data set TEMP is created and variable X has a length of 8.  
C.The data set TEMP is not created because variable A has an invalid length.  
D.The data set TEMP is not created because variables A and B have invalid lengths. 

> Answer: C

---



102. The following SAS program is submitted: 

> data view = sasuser.ranch; 
> describe; 
> run; 

What is the result? 

A.The program retrieves the SAS source code that creates the view and places it in the SAS log.  
B.The program creates a DATA step view called SASUSER.RANCH and places it in the SAS log.  
C.The program retrieves the SAS source code that creates the view and places it in the output window.  
D.The program creates a DATA step view called SASUSER.RANCH and places the program code in the current editor window.  

> Answer: A

---



103. The following SAS program is submitted: 

> data sasuser.new (compress = ); 
> infile 'file reference'; 
> input name1 - name100 ($100.) position1 - position100 ($50.) salary1 - salary50 (12.2); 
> run; 

Which COMPRESS data set option value will compress only repeated characters such as blanks or binary zeros?  

A.YES  
B.TRUE  
C.BINARY  
D.CHARACTER  

> Answer: A

---



104. Which of the following is true about the COMPRESS= YES data set option?  

A.It uses the Ross Data Compression method to compress numeric data.  
B.It is most effective with character data that contains repeated characters.  
C.It is most effective with numeric data that represents large numeric values.  
D.It is most effective with character data that contains patterns, rather than simple repetitions.  

> Answer: B

---



105. The following SAS program is submitted: 

> options reuse = YES; 
> data sasuser.RealEstate(compress = CHAR); 
> set sasuser.houses; 
> run; 

What is the effect of the REUSE = YES SAS system option?  

A.It allows updates in place.  
B.It tracks and recycles free space.  
C.It allows a permanently stored SAS data set to be replaced.  
D.It allows users to access the same SAS data set concurrently.  

> Answer: B

---



106. What is the result of including the _TEMPORARY_ keyword option on an ARRAY statement?  

A.The values in the array are automatically retained.  
B.The values are written to temporary variables in the Program Data Vector.  
C.The option allows both character and numeric variables to be stored in one array.  
D.The values occupy 40 bytes more space in memory per value than DATA step variables. 

> Answer: A

---



107. When does a SELECT statement in a DATA step always use fewer CPU resources than IF-THEN/ELSE statements?  

A.when there is a large selection of randomly distributed numeric values  
B.when there is a large selection of uniformly distributed numeric values  
C.when there is a small selection of randomly distributed character values  
D.when there is a small selection of uniformly distributed character values  

> Answer: B

---



108. Which of the following is required to use the UPDATE statement successfully in a SAS DATA step?  

A.Data sets must be sorted or indexed.  
B.All of the data sets can contain duplicate BY variable values.  
C.Data sets can be listed in any order on the UPDATE statement.  
D.An unlimited number of data sets can be listed on the UPDATE statement.  

> Answer: A

---



109. The following SAS program is submitted: 

> proc format lib = sasuser ; 
> value code 1 = 'One' 2 = 'Two' other = 'Miscoded'; 
> run; 

Which FORMAT statement option completes the program and documents the format in the listing destination?  

A.DOC  
B.PAGE  
C.FMTLIB  
D.CNTLOUT  
 

> Answer: C

---



110. What is an advantage of using a hash object in a SAS DATA step?  

A.The hash object automatically sorts the data.  
B.The hash object does not require unique keys.  
C.The hash object persists after the DATA step has executed.  
D.The hash object key values can be multiple numeric and character data values.  

> Answer: D

---



111. What is the advantage of changing the SAS data set size?  

A.to change the memory usage whenever the SAS data set is used  
B.to change from direct access to sequential access whenever the SAS data set is used 
C.to vary the number of bytes of physical storage used by the data values in a SAS d at a set
D.to optimize the unit of data transfer between the operating system buffers and SAS buffers in memory  

> Answer: D

---



112. The following SAS program is submitted: 

> data new (bufno = 4); 
> set old(bufno = 4); 
> run; 

Why are the BUFNO options used?  

A.to reduce network traffic  
B.to reduce memory usage 
C.to reduce the amount of data read  
D.to reduce the number of I/O operations  

> Answer: D

---



113. What is an advantage of using the SASFILE statement?  

A.It reduces network traffic.  
B.It reduces memory usage.  
C.It reduces the number of I/O operations.  
D.It reduces the amount of disk storage space required.  

> Answer: C

---



114. What is the purpose of the SASFILE statement?  

A.It requests that a SAS data set be opened and loaded into SAS memory in its entirety. 
B.It requests that a SAS data set be opened and loaded into SAS memory one page at a time.  
C.It requests that a SAS data set be opened and loaded into SAS memory one variable at a time.  
D.It requests that a SAS data set be opened and loaded into SAS memory one observation at a time.  

> Answer: A

---



115. When do IF-THEN/ELSE statements in a SAS DATA step always use fewer CPU resources than a SELECT statement?  

A.when there is a small selection of uniformly distributed values  
B.when there is a small selection of randomly distributed values  
C.when there is a large selection of uniformly distributed values  
D.when there is a large selection of randomly distributed values  

> Answer: B

---



116. Which statement prevents a DATA step from looping continuously and causes it to continue processing with the next SAS step, without writing error or warning messages to the SAS log?  

A.HALT;  
B.STOP;  
C.ABORT;  
D.ABEND;  

> Answer: B

---



117. Which SET statement option names a variable that contains the number of the observation to read during the current iteration of the DATA step?  

A.OBS = pointobs  
B.KEY = pointobs  
C.NOBS = pointobs  
D.POINT = pointobs  
 

> Answer: D

---



118. The following SAS programs ONE and TWO are submitted: 

> ONE data RealEstate; set sasuser.RealEstate; 
> fee = price *   .06; 
> run; 
> proc tabulate data = RealEstate; 
> class state; 
> var fee; table state, fee * mean; run; 
> TWO data RealEstate(keep = state fee); 
> set sasuser.RealEstate; fee = price * .06; 
> run; 
> proc tabulate data = RealEstate; 
> class state; 
> var fee; 
> table state, fee * mean; 
> run; 

The data set SASUSER.REALESTATE contains 20 variables and 10,000 observations. Which of the following is true?  

A.Program Two requires less memory than Program One.  
B.Program One uses less CPU resources than Program Two.  
C.Program Two requires fewer I/O operations than Program One.  
D.The data set created by Program One requires less hard disk space than the data set 
created by Program Two.  

> Answer: C

---



119. When reading data into a SAS DATA step, if the input data is in a raw data file, what minimizes the amount of CPU resources required to read and process the data?  

A.using an INPUT statement that selects only necessary variables  
B.using a KEEP statement that selects only necessary variables  
C.using a RETAIN statement that selects only necessary variables  
D.using a WHERE statement that selects only necessary observations  

> Answer: A

---


 

120. When reading a SAS data file, what does the NOBS= option on the SET statement represent?  

A.a variable that represents the current observation number  
B.a variable that represents a flag indicating the end of the file     
C.a variable that represents the total number of observations in the input data set(s)  
D.a variable that represents the total number of observations in the output data set(s) 

> Answer: C

---



121. What is generated as a result of submitting the RANUNI function with a seed of 123? 

A.a random number between 0 and 123  
B.a different sequence of random numbers with each program execution  
C.a consistent sequence of random numbers with each program execution  
D.a missing value because 123 is an invalid argument for the RANUNI function  

> Answer: C

---



122. Given the SAS data set SASUSER.STUDENTS: 

> SASUSER.STUDENTS ObsID NAME 1 12345 Hans1 2 12345 Hans2 3 67890 Bruno1 4 67890 Bruno2 5 54321 Nigel1 6 54321 Nigel2 7 9876 Suzy1 8 9876 Suzy2 9 11111 Jose 10 11111 Maria 

The following SAS program is submitted: 

> proc sort data = sasuser.students out = students dupout = temp nodupkey; 
> by ID; 
> run; 

Which of the following is true?  

A.WORK.TEMP contains no observations and WORK.STUDENTS contains no observations.  
B.WORK.TEMP contains two observations for each value of ID and WORK.STUDENTS contains no observations.  
C.WORK.TEMP contains one observation for each value of ID and WORK.STUDENTS contains one observation for each value of ID.  
D.WORK.TEMP contains two observations for each value of ID and WORK.STUDENTS contains one observation for each value of ID.  

> Answer: C

---



123. Given the non-indexed SAS data set TEMP: TEMP X Y P52 P45 A13 A56 R34 R12 R78 The following SAS program is submitted: 

> proc print data = temp; 
> run; 

Which BY statement completes the program, creates a listing report that is grouped by X, and completes without errors?  

A.by X;  
B.by X grouped;  
C.by X notsorted;  
D.by descending X;  

> Answer: C

---



124. The following SAS program is submitted. data temp; 

> set sasuser.history(keep = date); 
> format date qtr.; 
> if first.date then total = 0; 
> total + 1; 
> if last.date; 
> run; 
> proc print data = temp; 
> run; 

SASUSER.HISTORY is sorted by the SAS date variable DATE. The following output is required: 

> datetotal 1 13 2 12 3 15 4 25 

Which BY statement completes the data step and successfully generates the required output?  

A.by date qtr.;  
B.by notsorted date;  
C.by formatted date;  
D.by groupformat date;  

> Answer: D

---



125. The SAS data set WORK.CLASS contains 5 variables. The following SAS program is submitted: 

> proc sort data = class out = class1 ; 
> by ID; 
> run; 

Which SORT procedure option eliminates observations with duplicate BY values only?  

A.NODUP  
B.UNIQUE  
C.SORTDUP  
D.NODUPKEY  

> Answer: D

---



126. The following SAS program is submitted: 

> data temp(); 
> infile 'rawdata'; 
> input x $ y z; 
> run; 

RAWDATA is a file reference to an external file that is ordered by the variable X. 

Which option specifies how the data in the SAS data set TEMP will be sorted? 

A.ORDERBY= X  
B.GROUPBY= X   
C.SORTEDBY= X  
D.SORTSYNC= X  

> Answer: C

---



127. The following SAS program is submitted. 

> data sasuser.myfile(); 
> infile rawdata2; 
> input x $ y $ z $ a b c; 
> run; 

Which output data set option creates a composite index? 

A.INDEX=(X Y);  
B.INDEX=(Z=(X Y));  
C.INDEX=(X=(X Y));  
D.INDEX=(IND=(X Y));  

> Answer: D

---



128. The following SAS program is submitted. 

> data sasuser.history; 
> set sasuser.history(keep = State x y rename = (State = St)); 
> total = sum(x, y); 
> run; 

The SAS data set SASUSER.HISTORY has an index on the variable STATE. 

Which describes the result of submitting the SAS program?  

A.The index on STATE is deleted.  
B.The index on STATE is updated as an index on ST.  
C.The index on STATE is recreated as an index on ST.  
D.The index on STATE is deleted and an index on ST is created.  

> Answer: A

---


129. When creating an index using the INDEX CREATE statement in the DATASETS procedure, which of the following is true?  

A.The index can be renamed.  
B.The index can not be unique.  
C.The index must be a simple index.  
D.The index can not exist previously, but the data set must exist.  

> Answer: D

---


130. Which SAS program creates a simple index on the variable X in the dataset ONE? 

A.proc datasets data = work.one; index create X; quit;  
B.proc datasets data = work.one; index create X = X; quit;  
C.proc datasets lib = work; modify one; index create X; quit;  
D.proc datasets lib = work; modify one; index create X = X; quit;  

> Answer: C

---

