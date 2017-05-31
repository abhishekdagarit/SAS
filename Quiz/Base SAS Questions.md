# [SAS BASE Programming](https://sasbyarvind.wordpress.com/)


### 1. The following program is submitted.

```sas
data WORK.TEST;
  input Name $ Age;
datalines;
John +35
;
run;
Which values are stored in the output data set?

Name              Age
---------------------
John               35
Name              Age
---------------------
John              (missing value)
Name              Age
---------------------
(missing value)   (missing value)
```

The DATA step fails execution due to data errors.

> correct_answer = “A”

### 2. Given the SAS data set WORK.ONE:

```sas
 Id  Char1
---  -----
182  M
190  N
250  O
720  P
```

and the SAS data set WORK.TWO:

```sas
 Id  Char2
---  -----
182  Q
623  R
720  S
```

The following program is submitted:

```sas
data WORK.BOTH;
   merge WORK.ONE WORK.TWO;
   by Id;
run;
```

What is the first observation in the SAS data set WORK.BOTH?

```sas
Id  Char1  Char2
---  -----  -----
182  M
Id  Char1  Char2
---  -----  -----
182         Q
Id  Char1  Char2
---  -----  -----
182  M      Q
Id  Char1  Char2
---  -----  -----
720  P      S
```

> correct_answer = “C”


### 3. Given the text file COLORS.TXT:

```sas
----+----1----+----2----+----
RED    ORANGE  YELLOW  GREEN
BLUE   INDIGO  PURPLE  VIOLET
CYAN   WHITE   FUCSIA  BLACK
GRAY   BROWN   PINK    MAGENTA
```

The following SAS program is submitted:

```sas
data WORK.COLORS;
  infile 'COLORS.TXT';
  input @1 Var1 $ @8 Var2 $ @;
  input @1 Var3 $ @8 Var4 $ @;
run;
```

What will the data set WORK.COLORS contain?

```sas
Var1     Var2     Var3    Var4
------   ------   ------  ------
RED      ORANGE   RED     ORANGE
BLUE     INDIGO   BLUE    INDIGO
CYAN     WHITE    CYAN    WHITE
GRAY     BROWN    GRAY    BROWN
Var1     Var2     Var3    Var4
------   ------   ------  ------
RED      ORANGE   BLUE    INDIGO
CYAN     WHITE    GRAY    BROWN
Var1     Var2     Var3    Var4
------   ------   ------  ------
RED      ORANGE   YELLOW  GREEN
BLUE     INDIGO   PURPLE  VIOLET
Var1     Var2     Var3    Var4
------   ------   ------  ------
RED      ORANGE   YELLOW  GREEN
BLUE     INDIGO   PURPLE  VIOLET
CYAN     WHITE    FUCSIA  BLACK
GRAY     BROWN    PINK    MAGENTA
```

> correct_answer = “A”

### 4. Given the SAS data set WORK.INPUT:

```sas
Var1     Var2
------   -------
A        one
A        two
B        three
C        four
A        five
```

The following SAS program is submitted:

```sas
data WORK.ONE WORK.TWO;
  set WORK.INPUT;
  if Var1='A' then output WORK.ONE;
  output;
run;
```

How many observations will be in data set WORK.ONE?

Enter your numeric answer in the space below.

> correct_answer = “8”

### 5. The following SAS program is submitted:

```sas
data WORK.LOOP;
  X = 0;
  do Index = 1 to 5  by  2;
    X = Index;
  end;
run;
```

Upon completion of execution, what are the values of the variables X and Index in the SAS data set named WORK.LOOP?

```sas
X = 3, Index = 5
X = 5, Index = 5
X = 5, Index = 6
X = 5, Index = 7
```

correct_answer = “D”


### 6. The following SAS program is submitted:

```sas
proc format;
  value score  1  - 50  = 'Fail'
              51 - 100  = 'Pass';
run;
```

Which one of the following PRINT procedure steps correctly applies the format?

```sas
proc print data = SASUSER.CLASS;
   var test;
   format test score;
run;
proc print data = SASUSER.CLASS;
   var test;
   format test score.;
run;
proc print data = SASUSER.CLASS format = score;
   var test;
run;
proc print data = SASUSER.CLASS format = score.;
   var test;  
run;
```

> correct_answer = “B”


### 7. This item will ask you to provide a line of missing code;

The SAS data set WORK.INPUT contains 10 observations, and includes the numeric variable Cost.

The following SAS program is submitted to accumulate the total value of Cost for the 10 observations:

```sas
data WORK.TOTAL;
  set WORK.INPUT;
  <insert code here>
  Total=Total+Cost;
run;
```

Which statement correctly completes the program?

```sas
keep Total;
retain Total 0;
Total = 0;
If _N_= 1 then Total = 0;
```

> correct_answer = “B”



### 8. This question will ask you to provide a line of missing code.

Given the following data set WORK.SALES:

```sas
SalesID  SalesJan  FebSales  MarchAmt
-------  --------  --------  --------
W6790          50       400       350
W7693          25       100       125
W1387           .       300       250
```

The following SAS program is submitted:

```sas
data WORK.QTR1;
   set WORK.SALES;
   array month{3} SalesJan FebSales MarchAmt;
   <insert code here>
run;
```

Which statement should be inserted to produce the following output?

```sas
SalesID  SalesJan  FebSales  MarchAmt  Qtr1
-------  --------  --------  --------  ----
W6790          50       400       350   800
W7693          25       100       125   250
W1387           .       300       250   550
Qtr1 = sum(of month{_ALL_});
Qtr1 = month{1} + month{2} + month{3};
Qtr1 = sum(of month{*});
Qtr1 = sum(of month{3});
```

> correct_answer = “C”


### 9. Given the following SAS error log

```sas
  44   data WORK.OUTPUT;
  45     set SASHELP.CLASS;
  46     BMI=(Weight*703)/Height**2;
  47     where bmi ge 20;
  ERROR: Variable bmi is not on file SASHELP.CLASS.
  48   run;
```

What change to the program will correct the error?

Replace the WHERE statement with an IF statement
Change the ** in the BMI formula to a single *
Change bmi to BMI in the WHERE statement
Add a (Keep=BMI) option to the SET statement

> correct_answer = “A”


### 10. The following SAS program is submitted:

```sas
data WORK.TEMP;
  Char1='0123456789';
  Char2=substr(Char1,3,4);
run;
```

What is the value of Char2?

```sas
23
34
345
2345
```

> correct_answer = “D”
