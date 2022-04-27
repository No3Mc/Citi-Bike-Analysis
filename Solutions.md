# 2

/* import */
 <code>
PROC IMPORT OUT=WORK.import 
        DATAFILE="/home/u60766313/my_shared_file_links/u50396654/citibike-tripdata.xlsx"
        DBMS=XLSX  REPLACE;
    GETNAMES=YES;
run;
 </code>

/* 2i */
 <code>
PROC SQL;
DELETE FROM import
where (end_station_id = '' AND end_station_name ='');
QUIT;
 </code>

/* 2ii */
 <code>
Data CitiBike;
set import ;

format started_at DATETIME16.;
format ended_at DATETIME16.;

Startdate= datepart(started_at);
Starttime=timepart(started_at);
Enddate= datepart(ended_at);
Endtime=timepart(ended_at);

Format Startdate mmddyy10.;
Format Starttime TIME8.;
Format Enddate mmddyy10.;
Format Endtime TIME8.;

if Starttime <'12:00't then Starttimes='Morning';
else if Starttime <'18:00't then Starttimes='Afternoon';
else Starttimes='Evening';

if Endtime <'12:00't then EndTimes='Morning';
else if Endtime <'18:00't then EndTimes='Afternoon';
else EndTimes='Evening';
run;


 </code>

# 3
## a
 <code>
/* proc freq data=work.citibike order=freq nlevels; */
/*  tables start_station_name / nocum; */
/*  format started_at monname.; */
/* run; */

proc freq data=work.citibike order=freq;
   tables start_station_name / 
       plots=freqplot(twoway=stacked orient=horizontal);
run;
 </code>
## b
 <code>
/* proc freq data=work.citibike order=freq; */
/*  tables end_station_name / nocum; */
/*  format ended_at monname.;  */
/* run; */

proc freq data=work.citibike order=freq;
   tables end_station_name / 
       plots=freqplot(twoway=stacked orient=horizontal);
run;
 </code>
## c
 <code>

/* Proc freq data = work.citibike; */
/*  Tables member_casual; */
/* Run; */

proc freq data=work.citibike order=freq;
   tables member_casual / 
       plots=freqplot(twoway=stacked orient=horizontal);
run;
 </code>

## d
 <code>

data work.citibiketime; 
set work.citibike; 
DurationMin = intck('minute',starttime,endtime); 
run;

/* Proc freq data = work.citibiketime ORDER=freq; */
/*  Tables DurationMin; */
/* Run; */

proc freq data=work.citibiketime order=freq;
   tables DurationMin / 
       plots=freqplot(twoway=stacked orient=horizontal);
run;
 </code>
## e
Working on

## f
 <code>

proc sort data=work.citibike;
by member_casual;
run;

/* proc freq data=work.citibike order=freq nlevels; */
/*  tables Start_station_name / out=Customers; */
/*  by member_casual; */
/* run; */

proc freq data=work.citibike order=freq;
   tables start_station_name / out=CustomersMem
       plots=freqplot(twoway=stacked orient=horizontal);
        by member_casual;
        where (member_casual = 'member' );
run;
 </code>


## g
 <code>

proc sort data=work.citibike;
by member_casual;
run;

/* proc freq data=work.citibike order=freq nlevels; */
/*  tables Start_station_name / out=Customers; */
/*  by member_casual; */
/* run; */

proc freq data=work.citibike order=freq;
   tables start_station_name / out=CustomersCas
       plots=freqplot(twoway=stacked orient=horizontal);
        by member_casual;
        where (member_casual = 'casual' );
run;
 </code>

## h
 <code>

proc sort data=work.citibike;
by member_casual;
where (member_casual = 'member' );

/* proc freq data=work.citibike; */
/* tables EndDate / out=CusDate; */
/* tables EndTimes / out=CusTime; */
/* run; */

proc freq data=work.citibike order=freq;
   tables EndDate / out=EndDate
       plots=freqplot(twoway=stacked orient=horizontal);
        by member_casual;
        where (member_casual = 'member' );
run;

proc freq data=work.citibike order=freq;
   tables EndTimes / out=EndTimes
       plots=freqplot(twoway=stacked orient=horizontal);
        by member_casual;
        where (member_casual = 'member' );
run;
 </code>
 
## i
working on
