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