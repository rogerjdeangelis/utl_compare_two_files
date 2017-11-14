# utl_compare_two_files
Five solutions using 5 "languages" or "system commands".     This type of question is best solved using Perl->Python->R- Unix OS/Widows OS?     Quickest way to get a True/Fasle result appears to be Python       1. Use Python for a Truse False      2. Use R for an interactive two panel display of differences      3. Use Perl for the best text base analysis?      4. Use Windows operating sysyem command  'fc'      5. Use Unix 'diff' command

    ```  SAS-l:  Quickly checking if two test fiies are identical?                                                                                                    ```
    ```                                                                                                                                                               ```
    ```     This type of question is best solved using Perl->Python->R- Unix OS/Widows OS?                                                                            ```
    ```                                                                                                                                                               ```
    ```     Quickest way to get a True/Fasle result appears to be Python                                                                                              ```
    ```                                                                                                                                                               ```
    ```       1. Use Python for a Truse False                                                                                                                         ```
    ```       2. Use R for an interactive two panel display of differences                                                                                            ```
    ```       3. Use Perl for the best text base analysis?                                                                                                            ```
    ```       4. Use Windows operating sysyem command  'fc'                                                                                                           ```
    ```       5. Use Unix 'diff' command                                                                                                                              ```
    ```                                                                                                                                                               ```
    ```  INPUT                                                                                                                                                        ```
    ```  =====                                                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```  FILE  d:/txt/file1.txt                                                                                                                                       ```
    ```  ==========================                                                                                                                                   ```
    ```                                                                                                                                                               ```
    ```  _N_=1 libname xel "d:/xls/cats.xlsx";                                                                                                                        ```
    ```  _N_=2 data _null_;                                                                                                                                           ```
    ```  _N_=3     dcl hash  a  (ordered: "a");                                                                                                                       ```
    ```  _N_=4     a.definekey('key');                                                                                                                                ```
    ```  _N_=5     a.definedata("ID", "Visit", "Model", "Type", "Speed", "Viscocity", "Date");                                                                        ```
    ```  _N_=6     a.definedone();                                                                                                                                    ```
    ```  _N_=7   do until (last.id);                                                                                                                                  ```
    ```  _N_=8     set have;                                                                                                                                          ```
    ```  _N_=9     by id;                                                                                                                                             ```
    ```  _N_=10     key+1;                                                                                                                                            ```
    ```  _N_=11     a.add();                                                                                                                                          ```
    ```  _N_=12   end;                                                                                                                                                ```
    ```  _N_=13   outdsn=cats('xel.',id);                                                                                                                             ```
    ```  _N_=14   a.output(dataset:outdsn);                                                                                                                           ```
    ```  _N_=15   a.delete();                                                                                                                                         ```
    ```  _N_=16 run;quit;                                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  FILE2  d:/txt/file2.txt                                                                                                                                      ```
    ```  ========================                                                                                                                                     ```
    ```                                                                                                                                                               ```
    ```  _N_=1 libname xel "d:/xls/cats.xlsx";                                                                                                                        ```
    ```  _N_=2 data _null_;                                                                                                                                           ```
    ```  _N_=3     dcl hash  a  (ordered: "a");                                                                                                                       ```
    ```  _N_=4     a.definekey('key');                                                        ------------                                                            ```
    ```  _N_=5     a.definedata("ID", "isit", "Model", "Type", "Speed", "iscocity", "Date");  ** V REMOVED;                                                           ```
    ```  _N_=6     a.definedone();                                                            -------------                                                           ```
    ```  _N_=7   do until (last.id);                                                                                                                                  ```
    ```  _N_=8     set have;                                                                                                                                          ```
    ```  _N_=9     by id;                                                                                                                                             ```
    ```  _N_=10     key+1;                                                                                                                                            ```
    ```  _N_=11     a.add();                     --------------                                                                                                       ```
    ```                                          ** MISSING END                                                                                                       ```
    ```  _N_=13   outdsn=cats('xel.',id);        --------------                                                                                                       ```
    ```  _N_=14   a.output(dataset:outdsn);                                                                                                                           ```
    ```  _N_=15   a.delete();                                                                                                                                         ```
    ```  _N_=16 run;quit;                                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  PROCESSES  AND OUTUT                                                                                                                                         ```
    ```  =====================                                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```      Python True/False                                                                                                                                        ```
    ```      =================                                                                                                                                        ```
    ```         %utl_submit_py64("                                                                                                                                    ```
    ```         import filecmp;                                                                                                                                       ```
    ```         print filecmp.cmp('d:/txt/file1.txt',                                                                                                                 ```
    ```                           'd:/txt/file2.txt');                                                                                                                ```
    ```         ");                                                                                                                                                   ```
    ```                                                                                                                                                               ```
    ```         False                                                                                                                                                 ```
    ```                                                                                                                                                               ```
    ```      Perl                                                                                                                                                     ```
    ```      ====                                                                                                                                                     ```
    ```        %utl_submit_pl64("                                                                                                                                     ```
    ```           #!c:/perl/bin/perl -w`                                                                                                                              ```
    ```           use Text::Diff;`                                                                                                                                    ```
    ```               use Data::Dumper qw(Dumper);`                                                                                                                   ```
    ```           my $diffs = diff 'd:/txt/file1.txt' => 'd:/txt/file2.txt';`                                                                                         ```
    ```           print Dumper($diffs);`                                                                                                                              ```
    ```        ");                                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```        OUTPUT                                                                                                                                                 ```
    ```                                                                                                                                                               ```
    ```        $VAR1 = '--- d:/txt/file1.txt	Tue Nov 14 12:44:35 2017                                                                                                 ```
    ```        +++ d:/txt/file2.txt	Tue Nov 14 12:44:35 2017                                                                                                          ```
    ```        @@ -2,14 +2,13 @@                                                                                                                                      ```
    ```         data _null_;                                                                                                                                          ```
    ```             dcl hash  a  (ordered: "a");                                                                                                                      ```
    ```             a.definekey(\'key\');                                                                                                                             ```
    ```        -    a.definedata("ID", "Visit", "Model", "Type", "Speed", "Viscocity", "Date");                                                                       ```
    ```        +    a.definedata("ID", "isit", "Model", "Type", "Speed", "iscocity", "Date");                                                                         ```
    ```             a.definedone();                                                                                                                                   ```
    ```           do until (last.id);                                                                                                                                 ```
    ```             set have;                                                                                                                                         ```
    ```             by id;                                                                                                                                            ```
    ```             key+1;                                                                                                                                            ```
    ```             a.add();                                                                                                                                          ```
    ```        -  end;                                                                                                                                                ```
    ```           outdsn=cats(\'xel.\',id);                                                                                                                           ```
    ```           a.output(dataset:outdsn);                                                                                                                           ```
    ```           a.delete();                                                                                                                                         ```
    ```        ';                                                                                                                                                     ```
    ```                                                                                                                                                               ```
    ```      R                                                                                                                                                        ```
    ```      ==                                                                                                                                                       ```
    ```        %utl_submit_r64('                                                                                                                                      ```
    ```        source("c:/Program Files/R/R-3.3.2/etc/Rprofile.site",echo=T);                                                                                         ```
    ```        library(diffr);                                                                                                                                        ```
    ```        library(plotly);                                                                                                                                       ```
    ```        res<-diffr("d:/txt/file1.txt", "d:/txt/file2.txt", before = "f1", after = "f2");                                                                       ```
    ```        str(res);                                                                                                                                              ```
    ```        htmlwidgets::saveWidget(res, "d:/htm/index.html")                                                                                                      ```
    ```        ');                                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```        OUTPUT                                                                                                                                                 ```
    ```                                                                                                                                                               ```
    ```        see screenshot (javascript interactive?)                                                                                                               ```
    ```                                                                                                                                                               ```
    ```        Uses color coding                                                                                                                                      ```
    ```                                                                                                                                                               ```
    ```        libname xel "d:/xls/cats.xlsx";               libname xel "d:/xls/cats.xlsx";                                                                          ```
    ```        data _null_;                                  data _null_;                                                                                             ```
    ```            dcl hash  a  (ordered: "a");                  dcl hash  a  (ordered: "a");                                                                         ```
    ```            a.definekey('key'); -----                     a.definekey('key');  ----                                                                            ```
    ```            a.definedata("ID", "Visit", "Model",          a.definedata("ID",  "isit", "Model",                                                                 ```
    ```            a.definedone();     -----                   a.definedone();        ----                                                                            ```
    ```          do until (last.id);                           do until (last.id);                                                                                    ```
    ```            set have;                                     set have;                                                                                            ```
    ```            by id;                                        by id;                                                                                               ```
    ```             key+1;                                        key+1;                                                                                              ```
    ```             a.add();                                      a.add();                                                                                            ```
    ```           end;                                                                                                                                                ```
    ```           outdsn=cats('xel.',id);                       outdsn=cats('xel.',id);                                                                               ```
    ```           a.output(dataset:outdsn);                     a.output(dataset:outdsn);                                                                             ```
    ```           a.delete();                                   a.delete();                                                                                           ```
    ```         run;quit;                                     run;quit;                                                                                               ```
    ```                                                                                                                                                               ```
    ```       Win 7 64bit                                                                                                                                             ```
    ```       ===========                                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```         Comparing files D:\TXT\file1.txt and D:\TXT\FILE2.TXT                                                                                                 ```
    ```         ***** D:\TXT\file1.txt                                                                                                                                ```
    ```             a.definekey('key');                                                                                                                               ```
    ```             a.definedata("ID", "Visit", "Model", "Type", "Speed", "Viscocity", "Date");                                                                       ```
    ```             a.definedone();                                                                                                                                   ```
    ```         ***** D:\TXT\FILE2.TXT                                                                                                                                ```
    ```             a.definekey('key');                                                                                                                               ```
    ```             a.definedata("ID", "isit", "Model", "Type", "Speed", "iscocity", "Date");                                                                         ```
    ```             a.definedone();                                                                                                                                   ```
    ```         *****                                                                                                                                                 ```
    ```                                                                                                                                                               ```
    ```         * gives before and after a difference (has many options)                                                                                              ```
    ```                                                                                                                                                               ```
    ```         ***** D:\TXT\file1.txt                                                                                                                                ```
    ```             a.add();                                                                                                                                          ```
    ```           end;                                                                                                                                                ```
    ```           outdsn=cats('xel.',id);                                                                                                                             ```
    ```         ***** D:\TXT\FILE2.TXT                                                                                                                                ```
    ```             a.add();                                                                                                                                          ```
    ```           outdsn=cats('xel.',id);                                                                                                                             ```
    ```         *****                                                                                                                                                 ```
    ```                                                                                                                                                               ```
    ```         Too Lazy to check Unix diff.                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```       UNIX                                                                                                                                                    ```
    ```       ====                                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```         x "/usr/bin/rm -f /home/txt/filecmp.txt;                                                                                                              ```
    ```         x "diff -s /home/txt/file1.txt /home/txt/file2.txt > /home/txt/filecmp.txt";                                                                          ```
    ```                                                                                                                                                               ```
    ```         donth have a copy of output                                                                                                                           ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  %macro utl_submit_pl64(pgm)/des="bactic separated set of py commands";                                                                                       ```
    ```    * write the program to a temporary file;                                                                                                                   ```
    ```    filename pl_pgm "%sysfunc(pathname(work))/pl_pgm.pl" lrecl=32766 recfm=v;                                                                                  ```
    ```    data _null_;                                                                                                                                               ```
    ```      length pgm  $32755 cmd $255;                                                                                                                             ```
    ```      file pl_pgm ;                                                                                                                                            ```
    ```      pgm=&pgm;                                                                                                                                                ```
    ```      semi=countc(pgm,'`');                                                                                                                                    ```
    ```        do idx=1 to semi;                                                                                                                                      ```
    ```          cmd=cats(scan(pgm,idx,'`'));                                                                                                                         ```
    ```          put cmd $char96.;                                                                                                                                    ```
    ```          putlog cmd $char96.;                                                                                                                                 ```
    ```        end;                                                                                                                                                   ```
    ```    run;                                                                                                                                                       ```
    ```    run;quit;                                                                                                                                                  ```
    ```    %let _loc=%sysfunc(pathname(pl_pgm));                                                                                                                      ```
    ```    %put &_loc;                                                                                                                                                ```
    ```    filename rut pipe "D:\Dwimperl\perl\bin\perl &_loc > d:/log/__log.txt";                                                                                    ```
    ```    data _null_;                                                                                                                                               ```
    ```      file print;                                                                                                                                              ```
    ```      infile rut;                                                                                                                                              ```
    ```      input;                                                                                                                                                   ```
    ```      put _infile_;                                                                                                                                            ```
    ```    run;quit;                                                                                                                                                  ```
    ```    filename rut clear;                                                                                                                                        ```
    ```    filename pl_pgm clear;                                                                                                                                     ```
    ```    data _null_;                                                                                                                                               ```
    ```      infile "d:/log/__log.txt";                                                                                                                               ```
    ```      input;                                                                                                                                                   ```
    ```      put _infile_;                                                                                                                                            ```
    ```    run;quit;                                                                                                                                                  ```
    ```  %mend utl_submit_pl64;                                                                                                                                       ```

