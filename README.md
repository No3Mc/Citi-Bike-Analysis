  <link rel="stylesheet" href="Readme.css">

# -Citi-Bike-Analysis


Analysing Citi Bike

<p align="center"><b>IMAT2214 Business Intelligence (BI)</b>

<p align="center"> Summative Assessment Task 2

<p align="center">Practical Development & Individual Report (50% of module coursework mark)
  
<p align="right">
  <img 
    width="100"
    height="100"
    src="https://user-images.githubusercontent.com/41834061/163710405-a0b06e63-4d05-479d-8fe9-b72fdb435909.png"
  >
</p>

Imagine…

Your consulting firm has recently been hired by Citi Bike to support decision making around its bike 
sharing service in New York City. Citi Bike currently uses a system, for collecting data on the use of 
their bikes. They are quite enthusiastic about engaging with interested individuals, to provide insight 
on their data, using business intelligence and analytics to support decision-making. Business 
intelligence presents many opportunities for Citi Bike and its stakeholders through value added from 
data – turning insights into actions, and adopting this for change in the Citi Bike Service. As a Business 
Data Analyst, you have been asked to demonstrate how SAS Studio can be used to gain insight from 
the data they have collected on Citi Bike use. Visit the following page to learn more about Citi Bike: 

- https://www.citibikenyc.com/about

Use the following guidelines to apply SAS studio:

1. Access CitiBike data CSV file available for download from [HERE](https://vle.dmu.ac.uk/webapps/blackboard/content/listContentEditable.jsp?content_id=_5672247_1&course_id=_601352_1)
2. Explore the data: 

   -  Have a look at the CitiBike data in your main table ‘citibike-tripdata’ to 
understand the kind of data you will be dealing with.

   -  The data is fairly clean, as the data scientist at your consultancy has already made an 
effort in Excel to prepare the data for you to analyse. However, there are some 
additional changes and cleaning you need to do:

      -  Some bikes were not returned by customers. This is represented by empty or 
      incorrectly inputted data under the end_station_name and end_station_id 
    columns. You will need to remove/exclude these from your dataset, using 
    SAS Studio code (Hint: Use a SQL procedure (proc sql) with [delete from] 
    and [where] statements
    ii. You will need to split the following columns into date and time, and reformat 
    the date (Hint: consider [datepart] and [timepart] functions.

            - started_at
            - ended_at
   - The following table provides a description of each attribute in your dataset table<br>
   (citibike-tripdata):

        | Attribute | Description |
        | --- | ----------- |
        | ride_id  | The recorded instance of the bike use, by a customer or member.|
        | started_at  | The start date and time the bike is undocked for use by the customer/member |
        | ended_at  | The date and time, that the bike is returned to a docking station by a customer/member. |
        | start_station_name |  The street or location name that the biked is collected/undocked |
        | start_station_id | The ID or reference number of the start docking station, where the bike is first collected/undocked. |
        | end_station_name | The street or location name that the biked is returned/docked |
        | end_station_id  | The ID or reference number of the docking station where the bike is returned/docked. |
        | start_lat | The location latitude, where the bike is collected/undocked |
        | start_lng  | The location longitude, where the bike is collected/undocked. |
        | end_lat | The location latitude, where the bike is returned/docked. |
        | end_lng  | The location longitude, where the bike is returned/docked. |
        | customer | The person using the Citi Bike service can either be a casual customer, or a subscribed member customer. In this case: <br>• Casual = 24-hour pass or 3-day pass user;  <br>• Member = Subscribed annual member |

3. Analyse the data and develop reports and graphical charts that would be useful to Citi Bike, 
considering the following:



<ol type="consonants">
<li>start</li>




