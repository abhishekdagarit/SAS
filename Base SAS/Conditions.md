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