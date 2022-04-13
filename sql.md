## create a dataset in sas
DATA Students;
INPUT ID $ NAME $ CLASS SECTION $;
DATALINES;
1 Harsh 6 A
2 Gagan 7 B
3 Aman 8 C
4 Shiva 10 A
5 Ashish 9 B
6 Manoj 10 C
;
RUN;

# print the dataset
proc print data=Students;
run;

# test first sql query
PROC SQL;
CREATE TABLE Students_information AS
SELECT * FROM Students;
QUIT;

# printing database
PROC PRINT data = Students_information;
RUN;

# selecting all from database and print 
proc sql;
select * from Students_information;
quit;

# select name and class only, and print 
proc sql;
select NAME,CLASS from StudentS_information;
quit;

# filtering using where clause
proc sql;
select * from Students_information where SECTION = 'A';
quit;

# fetching name,class and filtering them using where clause
proc sql;
select NAME,CLASS from Students_information where SECTION = 'A' or CLASS = 10;
quit;

# use of group by
proc sql;
select NAME,CLASS from Students_information GROUP BY class;
quit;

proc sql;
select NAME,CLASS from Students_information GROUP BY Section;
quit;

# using where clause and group by
proc sql;
select ID,NAME from Students_information where section = 'A' GROUP BY ID;
quit;

# use of distinct
proc sql;
SELECT DISTINCT section FROM Students_information;
quit;

# use of order by
proc sql;
SELECT * FROM Students_information ORDER BY Class;
quit;

# ordering in ascending order (by class)
proc sql;
SELECT * FROM Students_information ORDER BY Class Asc;
quit;

# ordering in descending order
proc sql;
SELECT * FROM Students_information ORDER BY Class Desc;
quit;

proc sql;
SELECT Name,Section,Class FROM Students_information ORDER BY class Desc;
quit;

proc sql;
SELECT COUNT(class),section from Students_information group by section;
quit;
