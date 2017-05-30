
### ODS

---

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


































