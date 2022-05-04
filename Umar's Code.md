# Initial Querty

    PROC IMPORT OUT=WORK.Assignment 
    DATAFILE="/home/u60748473/my_shared_file_links/u50396654/citibike-tripdata.xlsx"
    DBMS=XLSX  REPLACE;
    GETNAMES=YES;
        
        
    PROC SQL;
        DELETE FROM Assignment
        where (end_station_id = '' AND end_station_name ='');
    QUIT;


    Data File;
    set Assignment ;

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


    run;


# Main Query

## 3a

    title bold "3a";
    proc freq data=work.file order=freq;
    tables start_station_name;
    run;

    proc gchart data=work.file;
    pie start_station_name / detail=start_station_name
    detail_percent=best
    detail_value=none
    detail_slice=best
    detail_threshold=3
    legend
    ;
    run;
    quit;


## 3b

    title bold "";
    proc freq data=work.file order=freq;
    tables end_station_name;
    run;

## 3c

    title bold "3c";
    proc freq data=work.file order=freq;
    tables member_casual;
    run;

    proc SGPLOT data=work.file;
    vbar member_casual /
    stat=percent
    group=member_casual
    groupdisplay=cluster;
    vline member_casual /
    stat=percent
    group=member_casual
    groupdisplay=cluster
    lineattrs=(thickness=0px)
    datalabel;
    run;


## 3d

    title bold "3d";
    data work.filetimings; 
    set work.file; 
    DurationMin = intck('minute',starttime,endtime); 
    run;

    proc freq data=work.filetimings order=freq;
    tables DurationMin;
    run;

## 3e





## 3f
    title bold "3f";
    proc sort data=work.file;
    by member_casual;
    run;

    proc freq data=work.file order=freq;
    tables start_station_name / out=Members;
            by member_casual;
            where (member_casual = 'member' );
    run;


## 3g
    title bold "3g";
    proc sort data=work.file;
    by member_casual;
    run;

    proc freq data=work.file order=freq;
    tables start_station_name / out=Casuals
        plots=freqplot(twoway=stacked orient=horizontal);
            by member_casual;
            where (member_casual = 'casual' );
    run;


## 3h

    Data File3hwork;
    set File ;
    if Starttime <'12:00't then Starttimes='Morning';
    else if Starttime <'18:00't then Starttimes='Afternoon';
    else Starttimes='Evening';

    if Endtime <'12:00't then EndTimes='Morning';
    else if Endtime <'18:00't then EndTimes='Afternoon';
    else EndTimes='Evening';

    run;

    title bold "3h";
    proc sort data=work.File3hwork;
    by member_casual;
    where (member_casual = 'member' );

    proc freq data=work.File3hwork order=freq;
    tables EndDate / out=MemberEDates;
            by member_casual;
            where (member_casual = 'member' );
            
    run;

    proc gchart data=work.File3hwork;
    pie EndDate / detail=EndDate
    detail_percent=best
    detail_value=none
    detail_slice=best
    detail_threshold=3
    legend
    ;
    run;
    quit;

    proc freq data=work.File3hwork order=freq;
    tables EndTimes / out=MemberETimes;
            by member_casual;
            where (member_casual = 'member' );
    run;

    proc gchart data=work.File3hwork;

    pie EndTimes / detail=EndTimes
    detail_percent=best
    detail_value=none
    detail_slice=best
    detail_threshold=3
    legend
    ;
    run;
    quit;