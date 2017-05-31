# [How to send an email from SAS](https://sasbyarvind.wordpress.com/category/sas-and-email/)


In your organization, are you prevented from using the email alias of a distribution list (e.g. groupname@comp.domain.com), and would therefore like to extract the list recipients into a flat file to loop through/use the SAS Enterprise Miner functions, etc. to send the mail?

This question was recently asked by a student in our SAS Programming 3: Advanced Techniques and Efficiencies course. Instructor Christine Riddiough shares some sample code she’s used to solve this challenge. This will work for a distribution list in an Exchange Server running on UNIX. The OPTIONS statement would need to be adjusted for a different platform or email server.

    
```sas
/* macro to email a file to a list */
%macro EmailFile;

   /* This creates a series of macro variables to send email
                                         to individuals. */
   proc sort data=freqstart out=list(keep=email) nodupkey;
      by inst;
   run;

   data _null_;
      set list end=last;
      call symput(compress('email'||_n_),email);
      if last then call symput('tot',trim(left(_n_)));
   run;

   /* cycle through the individual emails to send the messages */
   %do i=1 %to &tot;

       /* if you want to attach a file use the filename statement and 
          the pathname function to capture the location of the file */
       filename freq "&fn.crr.csv";
      %let path=%sysfunc(pathname(freq));
      ods csv file=freq;
      proc print data=freqstart noobs;
      run;
      ods csv close;

       /* set options for email and use the filename statement 
                     with the email option to send email */
      options emailsys=smtp emailhost=mailhost.abc.xyz.com;

      filename mymail email "&&email&i"
         subject="Frequency Template for &start to &end"
         attach="&path";

           /* Add some text to the email */
   data _null_;
      file mymail;
      put 'Attached is a report.' /;
      put "Return the modified report to Jane.Smith@xyz.com by &date..";
   run;
%end;
%mend;

%EmailFile

------------------------------------------------------------

(courtesy: sasblogs)

```























