java c
DAT 560G: Database Design and SQL 
Fall 2024, Mini A 
Assignment #3: SQL Part 2
Instructions 
1. This is an   individual   assignment.   You may   not   discuss your   approach to   solving these   questions   with anyone (or Generative AI), other than the instructor   or   TA.
2. Please include   only   your   Student   ID   on the   submission.
3. The only allowed material is: 
a. Class notes 
b. Content posted on the LMS 
c. Textbook 
4. You   are not permitted to use other   online resources.
5. There will be TA office hours. See the course schedule. 
Background The North   American Disasters Database is a comprehensive repository designed to document   and   analyze various   disasters that have occurred   across North America. From   natural   calamities   such   as   hurricanes,   earthquakes,   and   wildfires   to   human-made   incidents   like   industrial   accidents   and   environmental crises, this database aims to provide a detailed record of   significant events that have   impacted North America.
Types relation contains the following information about   each type   of   disaster   in the   database:
• Type of   each   disaster. This   is   the primary   key.
• Natural indicates   whether   this   type   of   disaster   is   natural   or   caused   by   people   (man-made)
• Mode: what   causes   this   type   of   disaster
• Size: the typical   size   of   the disaster,   in   square miles
• Frequency: Every   how   many   years   the   event   can   be   expected.
Types (Type, Natural, Mode,   Size, Frequency)Places relation   describes   the   cities   where   disasters   may   occur.   It   captures   information   about   the   cities   and   states   where   disasters   occur,   including   geographic,   demographic,   and   economic   data.   NOT all cities have disasters. It includes the following   attributes.
• City: Name   of   the   city. This   is   the   primary   key.
• State: Name   of   the   state.
• Region: Name   of   the   region   within   the   US.
• Size: Geographic   size   of   the   city   in   square   miles.
• Population: Number   of   people   living   in   the   city.
• Income:   Average income of   the residents in the   city,   in   dollars.
• Homeowners: Percentage   of   houses   that   are   owned   by   the   occupants   rather   than   rented.
• Budget: The   city's   annual budget.
• FoundingDate: The   date   when   the   city   was   founded.
• ManagerFirstName: The   first   name   of   the   emergency   manager   in   the   city.
• ManagerLastName: The   lastname   of   the   emergency   manager   in   the   city.
• Gender: Gender   of   the   emergency   manager.
• Salary:   Annual   salary   of   the   emergency   manager.
• StartingDate: The date when the emergency manager   started their position.
Places (City,   State, Region,   Size,   Population, Income, Homeowners, Budget, FoundingDate,
ManagerFirstName, ManagerLastName, Gender,   Salary,   StartingDate, Environmental, Quality)Teams relation records   details   about   the   response   teams,   including   their   budget,   size,   and   the   demographics of   their members. There can be more than one response team for a city. If   a city has   disasters, then it must have at least one team. Some of   the cities that do not have disasters may not   have any response teams.
• Team: Unique identifier for the response team.
• City: Name of   the city where the response team is based. This   is   a   foreign   key, to the places relation
• Organization: The   organization   to   which   the   response   team   belongs.
• Budget: The   annual   budget   of   the   response   team, in   dollars
• FirstDate: The   date   when   the   response   team   was   first   established.
• Employees: The   number   of   employees   in   the   response   team.
• ManagerFirstName: The   first   name   of   the   manager   of   the   response   team.
• ManagerLastName: The   lastname   of   the   manager   of   the   response   team.
• Gender:   Gender   of   the   manager.
• Salary: Annual   salary   of   the   manager   in   dollars.
• Female: Percent   of   the   team   that   is   female.
• Minority: Percent   of   the   team   that   is   minorities.
• ServiceArea: This   is   the   part   of   the   city   that   this   team   serves.   Can   have   values   of   either:   All,   North,   South, East, West.
Teams (Team, City, Organization, Budget, FirstDate, Employees, ManagerFirstName,   ManagerLastName, Gender,   Salary, Female, Minority,   ServiceArea)TeamSkills relation lists the   specific   skills possessed by   these teams,   providing   insight   into   their   capabilities. Not all teams need to have skills. Some teams can have several skills. Different teams   will   have   different   numbers   of   skills.
• Team: Unique identifier for the response team. This is   a   foreign key.
• Skill:   Specific   skill   possessed   by   the   response   team. This   is   part   of   the   multi-attribute   keyTeamSkills (Team, Skill)
Disasters relation documents the details of   each disaster event, including the type,   location, response team involved, and the impact in terms of   duration, casualties, property   damage,   and   the   number   of   responders. It   includes   the   following   information:
• Type: The type of   disaster. Foreign Key that refers to the Type   in the   CauseTypes table.
• City: Name of   the city where the disaster occurred.   This   is   a   foreign   Key   referring to   Places.
• Team: Unique identifier for the response team that responded to the disaster.   Foreign   key   referring to Teams relation.
• Name:   A   unique name or identifier for the disaster. This   is part   of   the multi-attribute   key.
• Date: The   date   when   the   disaster   occurred.
• Year: The year when the disaster occurred.
• Month: The   month   when   the   disaster   occurred.
• Duration: The   duration   of   the   disaster,   in   hours.
• Casualties: The   number   of   casualties   resulting   from   the   disaster.
• PropertyDamage: The estimated property damage caused by the disaster,   in   US   dollars.
• Responders: The   number   of   responders   involved   in   addressing   the   disaster.
Disasters (Type, City, Team, Name, Date, Duration, Casualties, PropertyDamage, Responders,   Year, Month)
Relations 
Types (Type, Natural, Mode,   Size, Frequency)Places (City,   State,   Region,   Size,   Population,   Income,   Homeowners,   Budget,   FoundingDate,
ManagerFirstName,   ManagerLastName,   Gender,   Salary,   StartingDate,   Environmental,   Quality)Teams (Team, City,          Organization,       Budget,          FirstDate,       Employees,          ManagerFirstName,
ManagerLastName, Gender,   Salary, Female, Minority, ServiceArea)TeamSkills (Team,   Skill) Disasters (Type, City, Team,    Name,   Date,    Duration,   Casualties,   PropertyDamage,   Responders,
Year, Month)
Assignment 
Each of these questions is 10 points. Submit answers to these online on Canvas, by 6 am the day of the lab. They are automatically graded. 
1)       Find all cities that have more than 2 disasters. List the cities that have the most disasters first down to those who only have the fewest. 
2) List all of the skills related to teams that responded to Dam failures after 2010. Please only list the skill once. 
3)       In order to compare gender differences in manager salaries, please list the average salary for team managers by gender. Only include teams with average budgets greater than $5 million for teams established after 2010, and not in the state of California. Do not include teams with null values for their team manager’sgender. 
4) In order to find an experienced team manager with spills,find all managers who have experience with 2 or more disasters with an oil spill, train spill, or truck spill. Include the manager’sfirst and lastname, team, and the number of disasters the manager has overseen. Sort the list with the most experienced first. 
5) List the cities in this database that have NOT been affected by disasters. 
6) Find the types of disasters with six or fewer occurrences in this database. 
Each of these questions is 5 points. Submit answers to these on Canvas before the next lab session. They will be graded by TAs. 
For each question, submit your SQL code and a screenshot of the results. If the results are too long, partial results are fine. Include relevant attributes for each result, to explain that the result is correct. Do NOT include many unnecessary attributes. Do NOT use SELECT *.
7) Find the cities with less than 5 disasters. Include the population, state, region, and number of disasters. 
8)       Is there a city that has a population over 900,000 and has had both natural as well as man-made disasters? List it then. In your query results, make sure each row contains a unique city/Natural- type combination. Also list the city name and population. 
9) Are there any pairs of teams that have responded to the same type of disaster and the same city? List team pairings only once and include the city name in your results. 
10) Find teams with less than 150 employees and more than 70 females. List the team, the number of disasters, and the average number of responders. 
11) Find cities with more than two disasters, populations greater than 500,000, and disaster recovery teams led by female managers. List the name of the city only once in your results. 
12) Please identify how many disasters happened in each city ofCalifornia that occurred in October or January, had populations LESS THAN 500,000, and casualties above 900. Include the city, number of casualties, the population, and the date of the disaster in your answer. 
13) Find the minimum population and the average budget for states with less than five disasters. List the state, number of disasters, minimum population, and average budget—order by state name. 
14) How much time did you spend on this assignment? 









         
加QQ：99515681  WX：codinghelp
