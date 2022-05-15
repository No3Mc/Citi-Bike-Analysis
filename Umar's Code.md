# Initial Query

        /* Importing data from excel file */
    PROC IMPORT OUT=WORK.Assignment DATAFILE="/home/u60748473/my_shared_file_links/u50396654/citibike-tripdata.xlsx" 
            DBMS=XLSX REPLACE;
        GETNAMES=YES;
    run;

    /*  Deleting empty station id and name */
    PROC SQL;
        DELETE FROM Assignment where (end_station_id='' AND end_station_name='');
    QUIT;

    /*  reformating and spliting datepart and timepart */
    Data File;
        set Assignment;
        format started_at DATETIME16.;
        format ended_at DATETIME16.;
        Startdate=datepart(started_at);
        Starttime=timepart(started_at);
        Enddate=datepart(ended_at);
        Endtime=timepart(ended_at);
        Format Startdate mmddyy10.;
        Format Starttime TIME8.;
        Format Enddate mmddyy10.;
        Format Endtime TIME8.;
    run;

# Main Query

## 3a

    /* Start station ID */
    title bold "3a - Start Station ID";
    proc freq data=work.file order=freq;
        tables start_station_id;
    run;

    ods graphics / reset width=6.4in height=8in imagemap;

    proc sgplot data=WORK.ASSIGNMENT;
        title height=14pt "Start Station ID";
        hbar start_station_id / fillattrs=(color=CX5084d3) datalabel fillType=gradient 
            stat=percent;
        xaxis max=0.1 grid;
    run;

ods graphics / reset;
title;
## 3b
    /* End Station ID */
    title bold "3b - End Station ID";
    proc freq data=work.file order=freq;
        tables end_station_id;
    run;

    ods graphics / reset width=6.4in height=8in imagemap;

    proc sgplot data=WORK.ASSIGNMENT;
        title height=14pt "End Station ID";
        hbar end_station_id / fillattrs=(color=CXd9261c) datalabel fillType=gradient 
            stat=percent;
        xaxis grid;
    run;

    ods graphics / reset;
    title;
## 3c
    /* Casual & Member Customer */
    title bold "3c - Casual & Member Customer";
    proc freq data=work.file order=freq;
        tables member_casual;
    run;

    ods graphics / reset width=6.4in height=4.8in imagemap;

    proc sgplot data=WORK.ASSIGNMENT;
        title height=14pt "Casual & Members";
        vbar member_casual / fillattrs=(color=CX5084d3) datalabel fillType=gradient 
            stat=percent;
        yaxis max=1 grid;
    run;

    ods graphics / reset;
    title;
## 3d
    /* Duration */
    title bold "3d - Duration";
    data work.filetimings;
        set work.file;
        DurationMin=intck('minute', starttime, endtime);
    run;

    data work.filetime; 
    set work.filetimings; 
    DurationMin = intck('minute',starttime,endtime); 
    run;

    proc freq data=work.filetime order=freq;
    tables DurationMin / 
        plots=freqplot(twoway=stacked orient=horizontal);
    run;


## 3e
    /* maps */
    title bold "3e - Maps";

    proc sgplot data=work.file noborder noautolegend;
        polygon x=Start_lat y=Start_lng id=Start_Station_id / fill outline tip=none 
            lineattrs=(color=gray99) fillattrs=(color=cxe8edd5);
        scatter x=Start_lat y=Start_lng / markerattrs=(symbol=circlefilled size=13) 
            markerfillattrs=(color=yellow) markeroutlineattrs=(color=purple);
        xaxis display=none;
        yaxis display=none;
    run;

    proc sgplot data=work.file noborder noautolegend;
        polygon x=end_lat y=end_lng id=End_Station_id / fill outline tip=none 
            lineattrs=(color=gray99) fillattrs=(color=cxe8edd5);
        scatter x=end_lat y=end_lng / markerattrs=(symbol=circlefilled size=13) 
            markerfillattrs=(color=yellow) markeroutlineattrs=(color=purple);
        xaxis display=none;
        yaxis display=none;
    run;

## 3f
    /* Member Start Station Name */
    title bold "3f - Member Start Station Name";
    proc sort data=work.file;
        by member_casual;
    run;

    proc freq data=work.file order=freq;
        tables start_station_name / out=Members plots=freqplot(twoway=stacked 
            orient=horizontal );
        by member_casual;
        where (member_casual='member');
    run;



# Final Query


## 3g
    /* Start Station Name of Casual Customer */
    title bold "3g-Casual Customer StartStationName";
    proc sort data=work.file;
        by member_casual;
    run;

    proc freq data=work.file order=freq;
        tables start_station_name / out=Members plots=freqplot(twoway=stacked 
            orient=horizontal);
        by member_casual;
        where (member_casual='casual');
    run;
## 3h
    /* 3h - end time for members */
    Data File3hwork;
        set File;

        if Starttime <'12:00't then
            Starttimes='Morning';
        else if Starttime <'18:00't then
            Starttimes='Afternoon';
        else
            Starttimes='Evening';

        if Endtime <'12:00't then
            EndTimes='Morning';
        else if Endtime <'18:00't then
            EndTimes='Afternoon';
        else
            EndTimes='Evening';
    run;

    title bold "3h- End time for members ";

    proc freq data=work.File3hwork order=freq;
        tables EndTimes / out=MemberETimes;
        by member_casual;
        where (member_casual='member');
    run;

    proc template;
        define statgraph SASStudio.Pie;
            begingraph;
            entrytitle "Members End Time" / textattrs=(size=14);
            layout region;
            piechart category=EndTimes / group=PERCENT groupgap=2% stat=pct start=90 
                categorydirection=clockwise datalabellocation=inside;
            endlayout;
            endgraph;
        end;
    run;

    ods graphics / reset width=6.4in height=4.8in imagemap;

    proc sgrender template=SASStudio.Pie data=WORK.MEMBERETIMES;
    run;

    ods graphics / reset;

## 3i
    /* Additional analysis */
    ods graphics / reset width=6.4in height=8in imagemap;
    title bold "3i-Additional Analysis";
    proc sgplot data=WORK.FILETIMINGS;
        title2 height=11pt "End Station ID";
        hbar start_station_name / group=member_casual groupdisplay=cluster datalabel 
            fillType=gradient stat=percent;
        xaxis min=0.1 max=0.1 grid;
        keylegend / location=inside;
    run;

    ods graphics / reset;
    title;



