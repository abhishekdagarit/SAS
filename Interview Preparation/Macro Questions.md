# [Macro Questions](http://studysas.blogspot.in/2008/09/sas-interview-questionsmacros.html)

## 1. Have you used macros? For what purpose you have used those?

Yes I have, I used macros in creating analysis datasets and tables where it is necessary to make a small change throughout the program and where it is necessary to use the code again and again. 

## 2. How do you invoke a macro?

After I define a macro I can invoke it by adding the percent sign prefix to its name like this: %macro name a semicolon is not required when invoking a macro, though adding one generally does no harm.

## 3. How can you create a macro variable with its data step?

with CALL SYMPUT

## 4. How would you identify a macro variable?

with Ampersand (&) sign. 

## 5. How would you define the end of a macro?

The end of the macro is defined by the %Mend statement. 

## 6. For what purpose have you used macros?

If we want to use the same program step on multiple datasets. We can use it for repetitive tasks quickly and effeciently. It can be reused. Variables passed within the program customize the results without having to change the main code. 

## 7. What is the difference between %local and %global?
 
 %local is a macro variable defined inside a macro. %global is a macro variable defined outside of the macro (can be used anywhere).

## 8. How long can a macro variable be? A token?

A component of SAS known as word scanner breaks the program text into fundamental units called tokens. 
1. Tokens are passed on demand to the compiler.
2. The compiler then requests token until it recieves a semicolon.
3. Then the compiler performs the syntax check on the statement. 

## 9. If you use a SYMPUT in a DATA step, when and where can you use the macro variable?

The macro variable created by the CALL SYMPUT routine cannot be used in the same desktop in which it got created. Other than that we can use the macro variable at any time. 

## 10. What do you code to create a macro? 
We create a macro with %macro statement and end with a %mend statement. 

## 11. What is the differece between %PUT and SYMBOLGEN?
%PUT is used to define user defined messages on log window after execution of a program whereas %SYMBOLGEN is used to print the value of a macro variable resolved, in log window. 

## 12. How do you add a number to a macro variable?

Using %eval function or %sysevalf function if the number is a floating point.

## 13. Can you execute a macro withon a macro? Describe?

Yes, such macros are called nested macros. They can be obtained by using symget and call symput macros. 

## 14. If you need the value of a variable rather than the variable itself what whould you use to load the value to a macro variable?

If we need a value of a macro variable then we must define it in such terms that we can call them everywhere in the program. Define it as Global. There are different ways of assigning a globla variable. Simplest method is %LET.

> Example: 

A, is a macro variable. use the following statement to assign the value of 'A' rather than the variable itself. 

```sas
%LET A=xyz; %put x="&A";
```

This will assign "xyz" to x, not the variable xyz to x. 

## 15. Can you execute macro within another macro? If so, how would SAS know where the current macro ended and the new one began? 

Yes, I can execute macro within a macro, we call it as nesting of macros, which is allowed. 
Every macro's beginning is identified the keyword %macro and end with %mend. 

## 16. How are parameters passed to a macro? 
A macro variable defined in parentheses in a %MACRO statement is a macro parameter. Macro parameters allow you to pass information into a macro. 

Here is a simple example:

```sas
%macro plot(yvar= ,xvar= ); 
proc plot; 
plot &yvar*&xvar; 
run; 
%mend plot;
%plot(age,sex) 
```

## 17. How would you code a macro statement to produce information on the SAS log? 

This statement can be coded anywhere? 

> OPTIONS MPRINT MLOGIC MERROR SYMBOLGEN; 

## 18. How we can call macros with in data step? 

We can call the macro with 
CALL SYMPUT, 
Proc SQL , 
%LET statement. and macro parameters. 

## 19. Tell me about call symput?

CALL SYMPUT takes a value from a data step and assigns it to a macro variable. I can then use this macro variable in later steps. To assign a value to a single macro variable, 

I use CALL SYMPUT with this general form: 
CALL SYMPUT (“macro-variable-name”, value); 
Where macro-variable-name, enclosed in quotation marks, is the name of a macro variable, and value is the value I want to assign to that macro variable. Value can be the name of a variable whose value SAS will use, or it can be a constant value enclosed quotation marks. 

more abt callsymput routine can be read at: 
http://studysas.blogspot.com/2009/08/call-symput-vs-call-symputx.html 


CALL SYMPUT is often used in if-then statements such as this: 

```sas
If age>=18 then call symput (“status”,”adult”); 
else call symput (“status”,”minor”); 
```

These statements create a macro variable named &status and assign to it a value of either adult or minor depending on the variable age.Caution: We cannot create a macro variable with CALL SYMPUT and use it in the same data step because SAS does not assign a value to the macro variable until the data step executes. Data steps executes when SAS encounters a step boundary such as a subsequent data, proc, or run statement. 

## 20. Tell me about % include and % eval? 

The %include statement, despite its percent sign, is not a macro statement and is always executed in SAS, though it can be conditionally executed in a macro.It can be used to setting up a macro library. But this is a least approach. 

The use of %include does not actually set up a library. The %include statement points to a file and when it executed the indicated file (be it a full program, macro definition, or a statement fragment) is inserted into the calling program at the location of the call. 

When using the %include building a macro library, the included file will usually contain one or more macro definitions.%EVAL is a widely used yet frequently misunderstood SAS(r) macro language function due to its seemingly simple form. 

However, when its actual argument is a complex macro expression interlaced with special characters, mixed arithmetic and logical operators, or macro quotation functions, its usage and result become elusive and problematic. %IF condition in macro is evaluated by %eval, to reduce it to true or false. 

## 21. Describe the ways in which you can create macro variables? 

There are the 5 ways to create macro variables: 

> %Let
> %Global 
> Call Symput 
> Proc SQl into clause 
> Macro Parameters. 

## 22. Tell me more about the parameters in macro? 

Parameters are macro variables whose value you set when you invoke a macro. To add the parameters to a macro, you simply name the macro vars names in parenthesis in the %macro statement. 

> Syntax: 

```sas
%MACRO macro-name (parameter-1= , parameter-2= , ……parameter-n = ); 
macro-text%; 
%MEND macro-name;
%macro_name(par1,par2,....parn); 
```

## 23. What is the maximum length of the macro variable? 

32 characters long. 

## 24. Automatic variables for macro? 

Every time we invoke SAS, the macro processor automatically creates certain macro var. eg: &sysdate &sysday. 

## 25. What system options would you use to help debug a macro? 

The SAS System offers users a number of useful system options to help debug macro issues and problems. The results associated with using macro options are automatically displayed on the SAS Log. 

Specific options related to macro debugging appear in alphabetical order in the table below: 

> MEMRPT: Specifies that memory usage statistics be displayed on the SAS Log. 
> MERROR: SAS will issue warning if we invoke a macro that SAS didn’t find. Presents Warning Messages when there are misspellings or when an undefined macro is called. 
> SERROR: SAS will issue warning if we use a macro variable that SAS can’t find. 
> MLOGIC: SAS prints details about the execution of the macros in the log. 
> MPRINT: Displays SAS statements generated by macro execution are traced on the SAS Log for debugging purposes. 
> SYMBOLGEN: SAS prints the value of macro variables in log and also displays text from expanding macro variables to the SAS Log. 

## 27. What are SYMGET and SYMPUT? 

SYMPUT puts the value from a dataset into a macro variable where as 
SYMGET gets the value from the macro variable to the dataset. 

## 28. What are the macros you have used in your programs? 

Used macros for various puposes, few of them are..

1. Macros written to determine the list of variables in a dataset: 

```sas
%macro varlist (dsn); 
proc contents data = &dsn out = cont noprint; 
run; 
%mend; 
%varlist(demo); 

proc sql noprint; 
select distinct name into:varname1-:varname22 from cont; 
quit; 

%do i =1 %to &sqlobs; 
%put &i &&varname&i; 
%end; 
%mend varlist; 
%varlist(adverse) 
```

2. Distribution or Missing / Non-Missing Values

```sas
%macro missrep (dsn, vars=_numeric_); 

proc freq data=&dsn.; 
tables &vars. / missing; 
format _character_ $missf. _numeric_ missf.; 
title1 ‘Distribution or Missing / Non-Missing Values’; 
run; 
%mend missrep; 
%missrep(study.demog, vars=age gender bdate); 
```

3. Written macros for sorting common variables in various datasets

```sas
%macro sortit (datasetname,pid,inverstigator);

PROC SORT DATA = &DATASETNAME; 
BY &PID &INVESTIGATOR; 
%mend sortit; 
%sortit (ae,001,sarath);
```

4. Macros written to split the number of observations in a dataset

```sas
%macro split (dsnorig, dsnsplit1, dsnsplit2, obs1); 
data &dsnsplit1; 
set &dsnorig (obs = &obs1); 
run;
data &dsnsplit2; 
set &dsnorig (firstobs = %eval(&obs1 + 1)); 
run;
%mend split; 
%split(sasuser.admit,admit4,admit5,2) 
```

## 29. What is auto call macro and how to create a auto call macro? What is the use of it? How to use it in SAS with macros? 

SAS Enables the user to call macros that have been stored as SAS programs. 

The auto call macro facility allows users to access the same macro code from multiple SAS programs. Rather than having the same macro code for in each program where the code is required, with an autocall macro, the code is in one location. This permits faster updates and better consistency across all the programs.Macro set-up:The fist step is to set-up a program that contains a macro, desired to be used in multiple programs. Although the program may contain other macros and/or open code, it is advised to include only one macro. 

Set MAUTOSOURSE and SASAUTOS: 
Before one can use the autocall macro within a SAS program, The MAUTOSOURSE option must be set open and the SASAUTOS option should be assigned. The MAUTOSOURSE option indicates to SAS that the autocall facility is to be activated. The SASAUTOS option tells SAS where to look for the macros. 

For ex: sasauto=’g:\busmeas\internal\macro\’; 

## 30. Why and How to Use %PUT Statement: 

%Put statement is similar to the PUT statement in data step, What it does is it writes text and values of macro variable after execution to the SAS System LOG. If you want to make sure your macro variable resolves as expected, you can make sure it with %PUT statement. 

Unique advantage of %PUT over PUT is …you can use %PUT outside the data step whereas you can’t with PUT. 

How to use %PUT: 

%let program=AE; 
%put program Name here as &program; 

Above %put statement resolves to … %put Program Name here as AE; 

What can you do with %PUT: 

Numerous options are available for the %PUT statement. 

> %PUT _all_: 
It prints all macro variables in the log that are available in all environments (global, local, user and automatic). 

> %PUT _automatic_: 
It prints all the SAS defined automatic macro variables in the log. (ex: &sysdate, &systime ,%sysdsn, %syserr etc) 

> %PUT _global_: 
It prints macro variables that are created by the user and available in all environments. 

> %PUT _local_: 
It prints macro variables that are created by the user and available only in the local environment. (couldn’t be able use those macro variables outside the particular data step) 

> %PUT _user_: 
It prints macro variables that are created by the user in each environment.


## 31. How to know how &&var&i or &&dsn&i resolves?

It is very confusing some times to tell rightaway how &&var&i or &&dsn&i get resolved...
but here is the simple technique you can use to know....
ex: We generally use &&var&i or &&dsn&i these macro variables when we are using a %do loop... to execute same code n number of times.
You have a dataset and it has 5 variables ... Patid sex age ethnic race wt ht;

```sas
%macro doit;
%do i=1 %to &nvars;
&&var&i
%end;
%mend doit;
```

So if the nvars value is 7, then the loop creates a macro variable list of

&var1 &var2 &var3 &var4 &var5 &var6 &var7
which further get resolved to
patid sex age ethnic race wt ht

You can always use Macro debugging option SYMBOLGEN to see how each macro variable got resolved....







































