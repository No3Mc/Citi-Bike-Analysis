  <link rel="stylesheet" href="Readme.css">

# Citi-Bike-Analysis


Analysing Citi Bike
<h1>
<p align="center"><b>IMAT2214 Business Intelligence (BI)</b>

<p align="center"> Summative Assessment Task 2
</h1>
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
<h1>
<b>Use the following guidelines to apply SAS studio:</b>
</h1>

<b>1. Access CitiBike data CSV file available for download from [HERE](https://vle.dmu.ac.uk/webapps/blackboard/content/listContentEditable.jsp?content_id=_5672247_1&course_id=_601352_1)</b>
<b>2. Explore the data: </b>

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
      <h4>
      (citibike-tripdata):
      <h4>



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




<b>3. Analyse the data and develop reports and graphical charts that would be useful to Citi Bike, 
considering the following:</b>
<br>

`a. What are the total number of bikes collected/undocked per Station?` <br>

<ol style="list-style-type:lower-roman">
  <li>Start_station_name or Start_station_id</li>
</ol>

`b. What are the total number of bikes returned/docked per Station?`


<ul>
    <li>End_station_name or End_station_id </li>
</ul>

`c. What type of customer often uses Citi Bike`?
    
<ol style="list-style-type:lower-roman">
  <li>Customer</li>
</ol>

`d. What is the most common duration of bike use?`

<ol style="list-style-type:lower-roman">
  <li>Started_At and Ended_At (NB: Remember these fields will be split – see part 
2 b))</li>
</ol>

`e. Develop a map or two maps, showing the frequency of bike collection and return in different locations:`


<ol style="list-style-type:lower-roman">
  <li>Start_lat and Start_lng</li>
    <li>End_lat and End_lng
</li>
</ol>

`f. Which stations do Member Customers commonly collect bikes?`

<ol style="list-style-type:lower-roman">
  <li>Customer, Start_station_name</li>
</ol>

`g. Which stations do Casual Customers commonly collect bikes`

<ol style="list-style-type:lower-roman">
  <li>Customer, Start_station_name
</li>
</ol>

`h. At what time of the day (group in Morning, Afternoon, and Evening) do Member Customers commonly return or dock bikes they have used?`

<ol style="list-style-type:lower-roman">
  <li>Customer, Ended_at</li>
</ol>

`i. Add ONE (1) additional analysis that may provide insight for decision-making.`

<br>

<b>4. Design a Dashboard using MS Visio [NB: this is only a sketch):</b>
<ol type="a">
  <li>Using MS Visio or MS Powerpoint as a sketching tool, design a dashboard with images 
of charts and report summaries you developed in Step 3 above.</li>
  <li>Apply the principles of good dashboard design for business intelligence applications.
Access the videos on Linkedin Learning    
<a href="https://www.linkedin.com/learning-login/share?account=68130314&forceAccount=true&redirect=https%3A%2F%2Fwww.linkedin.com%2Flearning%2Fcollections%2F6782598689094438912%3Ftrk%3Dshare_collection_url%26shareId%3D6k8%252FQ7t9TFSXTCdQPPKhZQ%253D%253D">HERE</a>
 , for guidance.</li>
</ol>

<b>5. Write an individual report (500 words):</b> Submit a reflective report justifying your design 
decisions for the ETL and dashboard that you developed. This should be no more than 500 
words. This is an academic piece and <u>references are expected.</u>

<b> Deliverable Checklist: </b>
1. In a document:
o A print out of your SAS Studio code
o Print out of all graphs/charts that are proposed to provide insight to Citi Bike.
o A sketched design of your dashboard
o An Individual report (500 words) submitted to TurnItIn by the date specified.
2. A short 3-5 minute video, explaining your code, and running key elements of your SAS program 
using the Citi Bike data.


<br>


<b> Undergraduate Mark descriptors to guide tutor evaluations in written 
reports: <b>

| Attribute | Description |
| --- | ----------- |
| 90-100% | Responds to all of the assessment criteria for the task <br>• Displays exceptional degree of originality <br>• Exceptional analytical, problem-solving and/or creative skills <br>• No fault can be found with the work other than very minor errors, for example minor typographical issues |
| 80-89%  | • Responds to all of the assessment criteria for the task<br>• Work of outstanding quality, evidenced by an ability to engage critically and analytically with source material<br>• Likely to exhibit independent lines of argument• Highly original and/or creative responses<br>• Extremely wide range of relevant sources used where appropriate|
| 70-79% |• Responds to all of the assessment criteria for the task<br>• An extremely well developed response showing clear knowledge and the ability to interpret and/or apply that knowledge<br>• An authoritative grasp of the subject, significant originality and insight,<br>• Significant evidence of ability to sustain an argument, to think analytically, critically and/or creatively and to synthesise material• Evidence of extensive study, appropriate to task |
| 60-69%  | • Responds to most of the assessment criteria for the task<br>• A detailed response demonstrating a thorough grasp of theory, understanding of concepts, principles, methodology and content<br>• Clear evidence of insight and critical judgement in selecting, ordering and analysing content<br>• Demonstrates ability to synthesise material, to construct responses and demonstrate creative skills which reveal insight and may offer some originality<br>• Draws on an appropriate range of properly referenced sources |
| 50-59%  | • Responds to most of the assessment criteria for the task<br>• An effective response demonstrating evidence of a clear grasp of relevant material, principles and key concepts<br>• An ability to construct and organise arguments• Some degree of critical analysis, insight and creativity<br>• Demonstrating some conceptual ability, critical analysis and a degree of insight<br>• Accurate, clearly written/presented |
| 40-49%  | • Responds to some of the assessment criteria for the task<br>• A response demonstrating an understanding of basic points and principles sufficient to show that some of learning outcomes/assessment criteria have been achieved at a basic level<br>• Suitably organised work demonstrating a reasonable level of understanding<br>• Covers the basic subject matter and is appropriately presented but is rather too derivative and insufficiently analytical<br>• Demonstrates limited conceptual ability, levels of evaluation and demonstration of creativeskills<br>• Demonstrates adherence to the referencing conventions appropriate to the subject and/ortask |
| 30-39%  | • Overall insufficient response to the assessment criteria<br>• A weak response, which, while addressing some elements of the task, contains significant gaps and inaccuracies<br>• Indicates an answer that shows only weakly developed elements of understanding and/or other skills appropriate to the task<br>• May contain weaknesses in presentation that constitute a significant obstacle in communicating meaning to the assessor |
| 20-29%  | • Overall insufficient response to the assessment criteria<br>• A poor response, which falls substantially short of achieving the learning outcomes• Demonstrates little knowledge and/or other skills appropriate to the task<br>• Little evidence of argument and/or coherent use of material |
| 10-19%  | • Overall insufficient response to the assessment criteria<br>• A very poor response demonstrating few relevant facts<br>• Displays only isolated or no knowledge and/or other skills appropriate to the task•<br> Little adherence to the task |
| 0-9%  | • Overall insufficient response to the assessment criteria<br>• Displays virtually no knowledge and/or other skills appropriate to the task<br>• Work is inappropriate to assessment task given |










<br><br><br><br><br><br>








<h1>Marking Grid</h1>


<table>

  <tr>
  <th>Criterion</th>
  <th>Weight</th>
  <th>0-19 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  <th>20-29 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  <th>30-39 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  <th>40-49 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  <th>50-59 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  <th>60-69 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  <th>70-79 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  <th>80-89&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  <th>90-100 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</th>
  </tr>











  <tr>
  <td>Data Access and Exploration in SAS</td>
  <td>20% </td>
  <td>Very weak or no attempt of any merit</td>
  <td>An attempt at ETL, but weak and lacking in effort.</td>
  <td>Some effort to use ETL evident, but weak overall.</td>
  <td>ETL used to a basic level, but with gaps/omissions/weaknesses.</td>
  <td>Generally sound ETL methods/codebut some weaknesses. </td>
  <td>Good use of ETL, significant effort, no major weaknesses.Some evidence of data validation/formatting.</td>
  <td>Excellent use of ETL, significant effort, very few weaknesses overall, basic validation/formatting present.
</td>
  <td>Outstanding use of ETL, with significant effort, very high standards and no weaknesses evident, basic validation/formattingpresent.</td>
  <td>Exceptional use of ETL, with highest levels of effort, standards and with no weaknesses evident. Data sources accessedwith complete validation/formatting present.
</td>
  </tr>



  <tr>
  <td>Data Analysis in SAS</td>
  <td>30%</td>
  <td>Very weak or no attempt of any merit</td>
  <td>An attempt, but weak and lacking in effort or analysis</td>
  <td>Some effort evident, but weak analysis overall</td>
  <td>A basic but useable analysis, but with gaps/omissions/weaknesses</td>
  <td>Generally sound analysis evident, but some weaknesses
</td>
  <td>Good analysis and graphs, significant effort, no major weaknesses</td>
  <td>Excellent analysis and graphs, significant effort, very few weaknesses overall </td>
  <td>Outstanding analysis and graphs, with significant effort, very high standards and no weaknesses evident</td>
  <td>Exceptional work, with highest levels of effort, standards and with no weaknesses evident </td>
  </tr>



  <tr>
  <td>DashboardDesign</td>
  <td>30% </td>
  <td>Very weak or no attempt of any merit</td>
  <td>An attempt, but weak and lacking in effort or design</td>
  <td>Some effort evident, but weak design overall</td>
  <td>A basic but useable dashboard, but with gaps/omissions/weaknesses</td>
  <td>Generally sound dashboard, but some weaknesses
</td>
  <td>Good dashboarddesign, significant effort, no major weaknesses</td>
  <td>Excellent dashboarddesign, significant effort, very few weaknesses overal</td>
  <td>Outstanding dashboard design, with significant effort, very high standards and no weaknesses evident</td>
  <td>Exceptional work, with highest levels of effort, standards and with no weaknesses evident</td>
  </tr>



  <tr>
  <td>Individual Reflective Report</td>
  <td>20% </td>
  <td>Very weak or no attempt of any merit</td>
  <td>An attempt, but weak and lacking in effort. Barely any work.</td>
  <td>Some effort evident, but weak overall. </td>
  <td>Sufficient and basic work, but with gaps/omissions/weaknesses.</td>
  <td>Generally sound, but some weaknesses
</td>
  <td>Good work, significant effort, no major weaknesses</td>
  <td>Excellent work, significant effort, very few weaknesses overall</td>
  <td>Outstanding work, with significant effort, very high standards and no weaknesses evident</td>
  <td>Exceptional work, with highest levels of effort, standards and with no weaknesses evident</td>
  </tr>



  <tr>
  <td>OVERALL</td>
  <td>100%</td>
  <td>Very weak or no attempt of any merit</td>
  <td>An attempt, but weak and lacking in effort</td>
  <td>Some effort evident, but weak overall</td>
  <td>Sufficient and basic work, but with gaps/omissions/weaknesses</td>
  <td>Generally sound, but some weaknesses
</td>
  <td>Good work, significant effort, no major weaknesses</td>
  <td>Excellent work, significant effort, very few weaknesses overal</td>
  <td>Outstanding work, with significant effort, very high standards and no weaknesses evident</td>
  <td>Exceptional work, with highest levels of effort, standards and with no weaknesses evident</td>
  </tr>





</table>