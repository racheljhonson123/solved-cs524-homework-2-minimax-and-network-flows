Download Link: https://assignmentchef.com/product/solved-cs524-homework-2-minimax-and-network-flows
<br>



<ol>

 <li><strong>Doodle scheduling. </strong>Doodle Inc. is interviewing a candidate for a software engineer position at their company. It works like this: the interview (10 AM to 3 PM) is divided into a number of 20-minute time slots that may be used for 1-on-1 meetings with the candidate. The first 20-minute slot at 10 am should include two employees, one of which needs to be either Mirjam or Matt. There is also a one-hour time slot in the middle of the day where 3 employees take the candidate out for lunch.</li>

</ol>

The goal is that all the senior employees to meet with the candidate at some point during the day, and that the candidate has someone to meet in every time slot (but never meets anyone more than once). However, everybody has a busy schedule so it’s not clear whether this will be possible. A doodle poll (obviously) was sent to the senior employees to figure out their availability. Here is the data:

<table width="0">

 <tbody>

  <tr>

   <td width="61"> </td>

   <td width="42">10:00</td>

   <td width="42">10:20</td>

   <td width="42">10:40</td>

   <td width="42">11:00</td>

   <td width="42">11:20</td>

   <td width="42">11:40</td>

   <td width="45">Lunch</td>

   <td width="35">1:00</td>

   <td width="35">1:20</td>

   <td width="35">1:40</td>

   <td width="35">2:00</td>

   <td width="35">2:20</td>

   <td width="35">2:40</td>

  </tr>

  <tr>

   <td width="61">Mirjam</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

  </tr>

  <tr>

   <td width="61">Matt</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Manuel</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Luca</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">0</td>

   <td width="35">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Jule</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="45">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

  </tr>

  <tr>

   <td width="61">Michael</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="45">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Malte</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Chris</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">0</td>

   <td width="35">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Spyros</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="45">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Florian</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Josep</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Joel</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="45">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

  </tr>

  <tr>

   <td width="61">Tom</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="45">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

  </tr>

  <tr>

   <td width="61">Daniel</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Christian</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="45">0</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">1</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

  <tr>

   <td width="61">Anne</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="42">0</td>

   <td width="42">0</td>

   <td width="42">1</td>

   <td width="42">1</td>

   <td width="45">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

   <td width="35">0</td>

  </tr>

 </tbody>

</table>

In the table, a 1 means that the employee is available at the indicated time, while a 0 means that they are unavailable.

As Doodle Inc’s hiring manager, it is your task to determine whether a feasible interview schedule exists. If so, print out a calendar for the candidate that lists who they will be meeting at each time slot. See hw3data.ipynb for the data.

Some questions to help you get started:

<ul>

 <li>What are the decision variables of this problem?</li>

 <li>How many meetings can each person have?</li>

 <li>How many people should be there for each time slot?</li>

 <li>Is there an objective function in this problem?</li>

 <li>…</li>

</ul>

Make sure to write down the mathematical model of the optimization problem and comment your code well.

1 of 3

CS/ECE/ISyE 524                                                 Introduction to Optimization                                      L. Roald,     Spring 2020

<ol start="2">

 <li><strong>[3 points] Building a stadium. </strong>A town council wishes to construct a small stadium in order to improve the services provided to the people living in the district. After the invitation to tender, a local construction company is awarded the contract and wishes to complete the task within the shortest possible time. All the major tasks are listed in the following table. Some tasks can only start after the completion of certain other tasks, as indicated by the “Predecessors” column. See ipynb for the data.</li>

</ol>

<table width="0">

 <tbody>

  <tr>

   <td width="50">Task</td>

   <td width="195">Description</td>

   <td width="74">Duration (in weeks)</td>

   <td width="87">Predecessors</td>

   <td width="78">Maximum reduction(in weeks)</td>

   <td width="64">Cost of reduction ($1k/wk)</td>

  </tr>

  <tr>

   <td width="50">1</td>

   <td width="195">Installing the construction site</td>

   <td width="74">2</td>

   <td width="87">none</td>

   <td width="78">0</td>

   <td width="64">–</td>

  </tr>

  <tr>

   <td width="50">2</td>

   <td width="195">Terracing</td>

   <td width="74">16</td>

   <td width="87">1</td>

   <td width="78">3</td>

   <td width="64">30</td>

  </tr>

  <tr>

   <td width="50">3</td>

   <td width="195">Constructing the foundations</td>

   <td width="74">9</td>

   <td width="87">2</td>

   <td width="78">1</td>

   <td width="64">26</td>

  </tr>

  <tr>

   <td width="50">4</td>

   <td width="195">Access roads and other networks</td>

   <td width="74">8</td>

   <td width="87">2</td>

   <td width="78">2</td>

   <td width="64">12</td>

  </tr>

  <tr>

   <td width="50">5</td>

   <td width="195">Erecting the basement</td>

   <td width="74">10</td>

   <td width="87">3</td>

   <td width="78">2</td>

   <td width="64">17</td>

  </tr>

  <tr>

   <td width="50">6</td>

   <td width="195">Main floor</td>

   <td width="74">6</td>

   <td width="87">4,5</td>

   <td width="78">1</td>

   <td width="64">15</td>

  </tr>

  <tr>

   <td width="50">7</td>

   <td width="195">Dividing up the changing rooms</td>

   <td width="74">2</td>

   <td width="87">4</td>

   <td width="78">1</td>

   <td width="64">8</td>

  </tr>

  <tr>

   <td width="50">8</td>

   <td width="195">Electrifying the terraces</td>

   <td width="74">2</td>

   <td width="87">6</td>

   <td width="78">0</td>

   <td width="64">–</td>

  </tr>

  <tr>

   <td width="50">9</td>

   <td width="195">Constructing the roof</td>

   <td width="74">9</td>

   <td width="87">4,6</td>

   <td width="78">2</td>

   <td width="64">42</td>

  </tr>

  <tr>

   <td width="50">10</td>

   <td width="195">Lighting of the stadium</td>

   <td width="74">5</td>

   <td width="87">4</td>

   <td width="78">1</td>

   <td width="64">21</td>

  </tr>

  <tr>

   <td width="50">11</td>

   <td width="195">Installing the terraces</td>

   <td width="74">3</td>

   <td width="87">6</td>

   <td width="78">1</td>

   <td width="64">18</td>

  </tr>

  <tr>

   <td width="50">12</td>

   <td width="195">Sealing the roof</td>

   <td width="74">2</td>

   <td width="87">9</td>

   <td width="78">0</td>

   <td width="64">–</td>

  </tr>

  <tr>

   <td width="50">13</td>

   <td width="195">Finishing the changing rooms</td>

   <td width="74">1</td>

   <td width="87">7</td>

   <td width="78">0</td>

   <td width="64">–</td>

  </tr>

  <tr>

   <td width="50">14</td>

   <td width="195">Constructing the ticket office</td>

   <td width="74">7</td>

   <td width="87">2</td>

   <td width="78">2</td>

   <td width="64">22</td>

  </tr>

  <tr>

   <td width="50">15</td>

   <td width="195">Secondary access roads</td>

   <td width="74">4</td>

   <td width="87">4,14</td>

   <td width="78">2</td>

   <td width="64">12</td>

  </tr>

  <tr>

   <td width="50">16</td>

   <td width="195">Means of signalling</td>

   <td width="74">3</td>

   <td width="87">8,11,14</td>

   <td width="78">1</td>

   <td width="64">6</td>

  </tr>

  <tr>

   <td width="50">17</td>

   <td width="195">Lawn and sport accessories</td>

   <td width="74">9</td>

   <td width="87">12</td>

   <td width="78">3</td>

   <td width="64">16</td>

  </tr>

  <tr>

   <td width="50">18</td>

   <td width="195">Handing over the building</td>

   <td width="74">1</td>

   <td width="87">17</td>

   <td width="78">0</td>

   <td width="64">–</td>

  </tr>

 </tbody>

</table>

<ol>

 <li>What is the earliest possible date of completion for the construction? Note that the last two columns of the table are not relevant for this part of the problem.</li>

 <li>The town council wants the builder to expedite the project. As an incentive, the council will pay a bonus of $30k/week for each week the work finishes early. To accomplish this, the builder may employ additional workers and rent more equipment to cut down on the total time. The last two columns of the table show the maximum number of weeks that can be saved per task and the associated additional cost per week incurred by the extra work. When will the project be completed if the builder is acting in a way that maximizes his profit?</li>

</ol>

<ol start="3">

 <li><strong>[3 points] Museum site planning. </strong>A site is being investigated as a potential location for a new museum. An aerial plan of the site is shown in the figure below (in units of feet). The museum will have a circular footprint and law mandates that there be at least 50 feet of clearance between the building and any edge of the site. If we want the largest possible museum, where should it be located? What is its optimal radius? Re-plot the figure below along with the optimally designed museum.</li>

</ol>

2 of 3