# [Better programming practice tips](http://studysas.blogspot.in/2008/08/learn-sas-online.html)

1. Header description: It is very important to have a description header inside a SAS program. 

```sas
********************************************************************;
Program Name       : name.sas
Author             : Sarath Annapareddy
Date last Modified : Apr 02 2010 :
Purpose/Description: Macro to add titles and footnotes
Input Files        :
Output Files       :
Macros Used        :
Notes              :
*********************************************************************;
```

2. Use proper indentation: New step (eg. data step, proc sort, proc sql, etc) must always start with no indentaion, first line in any step must have one tab indentation line and after if (or similar) statements we must have one additional tab indentation before the next if (or similar) statements. 

3. UPCASE: Always use uppercase variable name and uppercase dataset names (including termporaru datasets created in the program).

4. Dataset names: Never use same dataset name for input and output datasets. 

5. Comments: Comments are used to make your program easier to read and edit. Use the comment statement anywhere in a SAS program to document the purpose of the program. Nothing is more frustating as to return to a program written months ago and not being able to figure out what you did and why you did it. Also, if someone else needs to look over your program, the task is made much easier, if the code is committed. 

6. Create a Macro: If you think code will be used in multiple programs, create a macro. Do not try to do multiple things in one macro. Chances are if something is broken in the macro, other programmer will not use that macro in their program. 

7. Give some meaningful name to the temporary datasets. 