---
layout: post
title:  "Data Science Workflows + Docker"
blurb: "DS workflows"
---

<img src="{{"/assets/img/content/post-example/docker.png" | absolute_url }}" alt="docker" width="350" height="350" class="post-pic"/>
<br />
<br />

Data analysis pipelines are tricky to manage for an individual Data Scientist, let alone a group of them. In a complete lifecycle, there are so many shifting components of the whole pipeline that tiny changes can cause trickle-down effects that warrant a scientist's whole day spent on just making sure that everything still runs smoothly at the end of it. That's why it's important to have a well-built pipeline which provides clarity and structure on where dependencies lie and what are the linkages of each component.

The fundamental building blocks of a typical ML/DS pipeline looks something like this:
1. Data exploration and analysis
2. Data cleaning and preprocessing  
3. Feature engineering
4. Machine Learning modelling and evaluation
5. Final product delivery

We can see that all these 5 steps are linked to one another, and each depends on the previous step's outputs. Now let's imagine that after several weeks of building this project, a team member wants to come back and make some changes by changing a feature at step 2 and would like to see how the performance will be at step 4 in evaluation stage as well as how the product looks at step 5. The person will have to look through all the old codes of each stage and figure out where exactly to focus on. This is going to be a challenging task without a proper pipeline and the person'll have to spend a few hours just refreshing his/her memory. And not to mention making sure what he/she does will not break the rest of the workflows.

A solution to this is to leverage a tool called GNU Make. This means to build a dependency tree and clearly identify the outputs of each step which will be fed as inputs of the next step. Then, separate these steps out as individual script files. Finally, build a make file which combines all the individual script commands which will then allow users to just call `make` command and voila, the files will all be dynamically created again. This not only ensures the integrity of the workflow, but also makes the users' lives easier by just focusing on what needs to be changed, and let the rest of the changes take place by themselves. For Small or Medium enterprises, the ability to develop this workflow process in-house is a key benefit for those companies without a big budget to spend on enterprise software for DS project management.

The Makefile method is convenient for the internal DS team which already has the right tools and dependencies. However, the business folks may also want to access the product themselves and find it difficult to install the programs and run Make. Here is where Docker comes in handy. This is basically like a pre-packaged self-contained executable program which allows anyone to run on any computer through combining source code with OS. So regardless of which OS the user has, he just needs to have docker installed and run a line of code to execute the entire workflow.

I worked on a [project](https://github.com/michelle-wms/DSCI_522_GROUP3_COFFEERATINGS) that leveraged exactly these tools with Make and Docker. The goal was to implement a complete data science workflow from data retrieval, cleansing/preprocessing, to analysis, ML modelling and report generation. The dependency diagram (structure of workflows) can be found [here](https://github.com/UBC-MDS/Coffee_quality_rating_predictor/blob/main/Makefile.png). The results were 1) A makefile consisting of all the script paths which can be triggered upon the command `make all` and 2) A dockerized image that lets user do the same thing by running Docker container, also through one line via `docker run`.

The experience with this project was invaluable as it taught me the power of building sustainable DS workflows and pipelines in solving many painpoints of a data science team. This is definitely an essential DS project skill to have and would prove to be a great addition for any DS team.