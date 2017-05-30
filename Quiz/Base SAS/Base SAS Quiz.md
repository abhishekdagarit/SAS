# Base SAS

1. The following SAS program is submitted:

```sas
data work.bazzar;
cost = ‘30000’;
newtotal = .10 * cost;
run;
```

Which one of the following is the value of the variable newTOTAL in the output data set?


> 1. `3000`
> 2. .[missing numberic value]
> 3. 3000
> 4. ''[missing character value]

Correct Answer: 3. 3000

2. The following SAS program is submitted:

```sas
data Retail;
set   OD;
x = mdy(1,27,1960);
run;
```

Which one of the following values does the variable named x contain?

1. 1
2. 1960
3. 26
4. 01/27/1960
5. 27
6. 01-27-1960
7. 01271960
8. It will give complile time error

Correct Answer: 3. 26


