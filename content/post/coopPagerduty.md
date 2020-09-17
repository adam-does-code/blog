+++
title =  "Co-op @ PagerDuty"
tags = ["coop", "internship"]
date = "2020-09-10"
+++

### Welcome to my final co-op report about my work term at PagerDuty. 

**"The world is always on. Let's keep it that way."**

Pagerduty is a digital operations company, it's a tool that helps customers maximize productivity, mitigate threats, and deliver amazing expieriences. Examples of customers of PagerDuty. Pagerduty offers a number of products from on-call management to event intelligence to visibility into your data and operations. 

Before we dive into this, let me define a few things: 

- Pagerduty service: 1 piece of a technical product (e.g. back-end server repo, front-end repo) (but also can be linked to multiple repos)

- An incident: something bad that happened that needs attending to (usually wakes up an  engineer if one gets triggered in the middle of the night)

- Major incident: an incident that usually has a lot of impact and takes down a lot of core product usage. 

### Experience [Data Science]

The first four months of my internship I was on the Data Science Core team as a data science intern. I was not expecting to be on the data science team nor did i have much data science experience. I had just taken our new data science course at the university though so i was excited and ready to learn even more. The DS core team operated way different than any other product team. We interviewed other teams within pagerduty (that were product facing) and brainstormed ways to help solve the problems they were running into. We called this a discovery sprint; we asked lots of questions and threw in a bunch of ideas regardless of how feasible they were. After we identified which projects we wanted to focus on for our program iteration, each data scientist took on a project. The project I picked was the Git Risk Prediction project, where I was trying to find correlations between our Github and Pagerduty data.


My goals: 

1. Documenting my semester: Implement a hype document + take notes of what i was doing every week, this helped me write documentation about the project I worked on and also help me reflect on how things were going. 

1. Give a lightning talk: I wasn't sure what I would talk about but we had monthly lightning talks about any topic and it would help me with my communication and presentation skills 

1. Get more comfortable with Python: I never really programmed in Python professionally at a job. A lot of times I felt like I wasnt writing code in the most pythonic way possible and I wanted to improve on it. 

1. Understand data science concepts in a more breadth (& depth for some): I wasn't sure if I liked data science yet what real data science is like in the tech world. I wanted to build up my toolkit with data science skills and learn more about what I was getting into. 

My project helped my reach lots of the goals that I set. In terms of data science concepts my project was divided into 3 parts, getting the data, trying to find correlation via time stamps and trying to find textual similaries.

We first started the Git Risk Prediction by using fuzzy matching to sync up all Github data with Pagerduty data. This helped us link all Github repos we (Pagerduty) own with our Pagerduty services. This was very straight forward since we mostly followed the same naming for teams both in Github and Pagerduty. We used a theshold of 85% and we found that the fuzzy matching was aroun 60% accurate. It was either a hit or miss since there were lots of PagerDuty services that didn't link to a direct Github repo

After we confirmed with a bunch of teams about our Github to PagerDuty mappings, we started to get all the data. The data we had on Github was a lot, like every commit, every PR, every code review comment. It was _awesome_. We decided to focus on one flow that we've seen during major incidents. The flow that an incident is triggered, someone realizes that a recent code deploy caused this, they end up reverting the PR to figure out what caused this, and then the incident is closed. 

This gives us four different time series to work with:

- incident triggered 
- incident resolved
- pull request opened
- pull request merged

Reverts usually happen very quickly and when something bad happens, and the time between these opening and merging a revert is very short. We ran a serial correlation against all these time series for all the repo mappings we collected. 

Next we decided to play around with textual data. A github PR has a lot of text, such as:

- branch name
- pull request name
- commit messages
- pull request body 
- all the reviewers 
- username and email of the contributers 

We didn't have as much textual data on the PagerDuty side, and a lot of that data was machine generated, but we were able to also collect who responded to the incident, and the names of the alerts. We didnt find much overlap between the sets of words that were extracted from both data sets. It taught me that dealing with macahine generated data is a lot harder to extract and understand vs human generated words.

Overall this project had a lot of data and to be able to get one specific clean up sight to see the correlation directly was super hard. It taught me a lot about research in the real world and how hard it can be. It taught me that things can fail and it doesn't mean you're a failure.

Alongside all the data science that happened, I learned and got to experience a handful of other things at the org. First, all the interns would intensely play foosball and my skills increased exponentially. Pagerduty also had hackdays (that were later turned into a hack week) and for my first hack day I changed a few things in the iOS app that we have. I got to get that small feature shipped and it was super exciting to contribute to a team I wasn't apart of. 

PagerDuty also runs Failure fridays, where on a nice friday afternoon we try to change things or see how something would fail. This shows us what procedures we have in place for when things fail, because things to do fail. I found the entire incident response stuff super interesting and I got to scribe and help out for one of the failure fridays. 

I also got to shadow support and sales calls, which was _super interesting_. This taught me a lot about how we help customers, and what customers need help with. Seeing the sales side of things showed me how people talk about our product and how we market ourselves. 

So, my goals.. 


### Hack Week!!

By the time hack week came along in late March, the entire company was already WFH. It did feel like a good start to adjusting by being able to just work on a hack for an entire week with people you dont usually get to work with. I ended up teaming with Dinna and Steve who are on the mobile team, and we tried to port our iPad app into a Mac app using project Catalyst. 


### Acknowledgements + Thanks

Wendy: 

Irena & Shaheen: 

DS Core Team:

Dileshni: 

Lyon: 

Leeor:

SI Team: 

Leena: 

