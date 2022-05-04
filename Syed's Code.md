# 2

/* import */

    PROC IMPORT OUT=WORK.import 
            DATAFILE="/home/u60766313/my_shared_file_links/u50396654/citibike-tripdata.xlsx"
            DBMS=XLSX  REPLACE;
        GETNAMES=YES;
run;


/* 2i */

    PROC SQL;
    DELETE FROM import
    where (end_station_id = '' AND end_station_name ='');
    QUIT;



/* 2ii */

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



# 3
## a

    proc freq data=work.citibike order=freq;
    tables start_station_name / 
        plots=freqplot(twoway=stacked orient=horizontal);
    run;


## b

    proc freq data=work.citibike order=freq;
    tables start_station_name / 
        plots=freqplot(twoway=stacked orient=horizontal);
    run;


## c


    proc freq data=work.citibike order=freq;
    tables member_casual / 
        plots=freqplot(twoway=stacked orient=vertical);
    run;



## d

    data work.citibiketime; 
    set work.citibike; 
    DurationMin = intck('minute',starttime,endtime); 
    run;

    proc freq data=work.citibiketime order=freq;
    tables DurationMin / 
        plots=freqplot(twoway=stacked orient=horizontal);
    run;


## e

    proc sgplot data=work.citibike;
    scatter x=start_lat y=start_lng;
    run;
    proc sgplot data=work.citibike;
    scatter x=end_lat y=end_lng;
    run;

    pattern c=black v=e r=62;
    proc gmap
    data=maps.counties 
    map=maps.counties;
    id county;
    choro county / nolegend;
    where state eq 36;
    run;

    proc sgplot data=work.citibike noborder noautolegend;
    polygon x=Start_lat y=Start_lng id=Start_Station_name / fill outline tip=none lineattrs=(color=gray99) fillattrs=(color=cxe8edd5);
    scatter x=Start_lat y=Start_lng /
    markerattrs=(symbol=circlefilled size=13)
    markerfillattrs=(color=yellow)
    markeroutlineattrs=(color=purple);
    xaxis display=none;
    yaxis display=none;
    run;


    proc sgplot data=work.citibike noborder noautolegend;
    polygon x=end_lat y=end_lng id=End_Station_name / fill outline tip=none lineattrs=(color=gray99) fillattrs=(color=cxe8edd5);
    scatter x=end_lat y=end_lng /
    markerattrs=(symbol=circlefilled size=13)
    markerfillattrs=(color=yellow)
    markeroutlineattrs=(color=purple);
    xaxis display=none;
    yaxis display=none;
    run;


## f

    proc sort data=work.citibike;
    by member_casual;
    run;

    proc freq data=work.citibike order=freq;
    tables start_station_name / out=CustomersMem
        plots=freqplot(twoway=stacked orient=horizontal);
            by member_casual;
            where (member_casual = 'member' );
    run;



## g


    proc sort data=work.citibike;
    by member_casual;
    run;

    proc freq data=work.citibike order=freq;
    tables start_station_name / out=CustomersCas
        plots=freqplot(twoway=stacked orient=horizontal);
            by member_casual;
            where (member_casual = 'casual' );
    run;



## h


    proc sort data=work.citibike;
	by member_casual;
	where (member_casual = 'member' );

    proc freq data=work.citibike order=freq;
    tables EndDate / out=EndDate
    plots=freqplot(twoway=stacked orient=horizontal);	
    by member_casual;
    where (member_casual = 'member' );
    run;

    title 'Frequency for ending times';
    proc freq data=work.citibike order=freq;
    tables EndTimes / out=EndTimes
    plots=freqplot(twoway=stacked orient=horizontal);
    by member_casual;
    where (member_casual = 'member' );
    run;

    title 'Histogram for Ending Dates';
    proc sgplot data=work.citibike;
    histogram EndDate;
    density EndDate;
    run;

 
## i
    working on
