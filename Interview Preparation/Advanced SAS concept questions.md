# Advanced SAS concept questions

### 1. Approximately what date is represented by the SAS date value of 730? 

> 31dec1961

### 2. How would you remove a format that has been permanently associated with a variable??

```sas
data test;
format x date9.;
x = 174;
run;

data test2;
set test;
format _all_;
run;
```

### 3. How are numeric and character missing values represented internally?


### 4. Under what circumstances would you code a SELECT construct instead of If statements?

> Use IF-THEN/ELSE statements when

> a.. the data values are character values
> b.. the data values are not uniformly distributed
> c.. there are few conditions to check

> Use SELECT statements when

> a.. you have a long series of mutually exclusive numeric conditions
> b.. data values are uniformly distributed

### 5. What is the one statement to set the criteria of data that can be coded in any step?

### 6. What is the effect of the OPTIONS statement ERRORS=1?

> The maximum number of observations for which complete data error messages are printed = 1


### 7. What's the difference between VAR A1 - A4 and VAR A1 -- A4 ?

> Both are variable lists, the former is a "named list" (for iterated names), the latter is a "pdv list" (for variable order in the pdv)


### 8. Identify statements whose placement in the DATA step is critical.

> Two cases come to mind immediately:


> The first reference to a character variable in the data step defines the length of the variable, so position of LENGTH statement could be crucial.

> A subsetting-IF should be placed as "high up" in the data step as possible to preserve CPU by reducing number of variables that are read (however top-bottom position of IF has no effect on I/O).


### 9. Does SAS 'Translate' (compile) or does it 'Interpret'? Explain.

> Here's how it works:

> a.. Input stack: accumulates of program statements
> b.. Word scanner: breaks statements into tokens
> c.. Compiler: requests tokens until ";", then compiles that statement
> d.. SAS perpetuates these 3 steps until a step boundary is encountered, then step is compiled, and if contains no fatal errors, is executed


### 10. What does the RUN statement do?

> It functions as a "step boundary' and lets Your Friend the Compiler know that "this is the end of the data step"

### 11. Why is SAS considered self-documenting?

> A SAS data set created from raw data adds a descriptor portion (the info displayed by Proc Contents) to the data portion.

### 12. What are some good SAS programming practices for processing very large data sets?

> First run with options obs=0 to debug compilation errors extracting small systematic or random samples to test code on first

> Use drop and keep to minimize vars Breaking large sets into pieces, process separately, re-assemble

> Avoid traditional sorts, use alternatives

> a.. V9 threaded sorts
> b.. Tagsort
> c.. Class statements
> d.. indexes

Indexing:

Create and use indexes especially if:

a.. Subsets under %15 of parent data
b.. Variables frequently used
c.. Variables have high cardinality

Reducing I/O

a.. Indexes = reduce number of pages SAS must load
b.. Manipulate bufsize= and buffno= to increase amount of data SAS can
load in single i/o transaction

Reducing cpu

a.. Use where instead of subsetting if

Consider table and/or numeric var compression

Alternatives to sorting

a.. Set key = : for 1-1 match - but requires an index on the key= data set
b.. Proc format cntlin method

Proc Datasets for table and index management - it only reads the descriptor
portion, and will not rebuild the data set when creating an index

Use proc append to join large base data with small data, instead of set
statement or outer union

Normalizing: transforming wide lookup data into narrow and thin tables,

for faster and more natural vertical number-crunching

run macro-driven jobs against huge SAS datasets on unix servers overnight
(both data and code is in the same directory for this session) don't even
think about using SAS Enterprise Guide, come back in the morning refreshed,
ready to cultivate more good non-work habits


13)What is the different between functions and PROCs that calculate the
same simple descriptive statistics?

The ways they deal with character variable arguments and missing numeric
input values are similar; as a general rule, both SAS functions and procs
that perform computations handle missing data by omitting the missing values

SAS functions are wonderfully convenient but are also total CPU pigs, and
should be used sparingly

14)If you were told to create many records from one record, show how you
would do this using arrays and with PROC TRANSPOSE?



data one;

input id x1 x2;

cards;

1

2

3

;



data two;

set one;

array hold(*) x1 x2;

do i=1 to 2;

x=hold(i);

output;

end;

drop i x1-x2;



proc print;



proc transpose

data=one

out=three(drop=_name_ rename=(col1=x))

;

by id

;



proc print data=three;


15)What is a method for assigning first.VAR and last.VAR to the BY group
variable on unsorted data?

Note that data must at least be grouped together with BY values

data two;

set one;

by id NOTSORTED;

if first.id;

### 16. What is the order of application for output data set options, input data set options and SAS statements?

Input data set options => affect what is included in pdv

Data set statements => affect pdv processing

Output data set options => affect what is written from pdv to output buffer
in memory


### 17. What is the order of evaluation of the comparison operators: + - * / ** ( ) ?

> - negative
> 
> ** exponentiation
> 
> * multiplication
> 
> / division
> 
> + addition
> 
> - subtraction


### 18. How do you debug and test your SAS programs?

> QA and debugging:

> a.. LOG messages
> b.. ODS trace
> c.. Invoke SAS debugger
> d.. Dictionary tables for real-time SAS session info
> e.. Proc contents
> f.. Proc sql options: noexec, validate, feedback, &sqlobs
> g.. Proc sql describe table
> h.. Proc print obs=10;
> i.. For macros: mlogic symbolgen mprint, automatic macvars
> j.. Data _null_ with file print and put statements
> k.. %put statements
> l.. Sas and sql options: msglevel=i, undo_policy=


### 20. Have you ever used the SAS Debugger?

```sas
Data one/debug;
X=1;
Run;
```

### 21. How would you combine 3 or more tables with different structures?


> Vertically:

> a.. do "proc append FORCE" twice
> b.. set statement
> c.. proc sql outer union


> Horizontally:

> a.. a 1-1 read e.g.

```sas
data new;
set a;
set b;
set c;
```

```sas
	data tariff_change_v1;
	set tariff_change;
	by vkont rate_Cat_from tariff_from;
	format  rate_cat_from1 date9. tariff_from1 date9. prev_tariff $20.;
	rate_cat_from1 = input(rate_cat_from,yymmdd8.);
	tariff_from1 = input(tariff_from,yymmdd8.);
	
	prev_tariff = lag(tariff_type);
	
	if first.vkont then do;
		Tariff_change_l2 = 0;
		prev_tariff = '';
	end;
	else do;
		if prev_tariff ne tariff_type then do;
			if tariff_type = " " and "01jan2010"d <= rate_cat_from1 <= "31dec2010"d 
			then Tariff_change_l2 = 1;
			else if tariff_type ne " " and "01jan2010"d <= tariff_from1 <= "31dec2010"d 
			then Tariff_change_l2 = 1;
		end;
		else Tariff_change_l2 = 0;
	end;
	run;
```
