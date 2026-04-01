---
title: "Creating Your First Project"
order: 2
---

# Creating a project
Time for some action, let's create a project to get an idea of how Jarvix works.

* Click on "Menu > New Project" or press `Ctrl + N`. This will open the new project dialog
* Choose a name for your project and where you want the project to live.
* The last part of this section is the brief. This is the prompt that will kickstart work on your project. We recommend you be descriptive with what you want and make sure you include everything you (or don't want) in there. For this test run we'll keep it simple and use "A web app that allows the user to upload a .CSV that includes their financial transactions over a period of time. The app should show the transactions in a list. How much they have now, how much they earned during so far, how much they've spend so far. What is the biggest three things they spend on (at least 2 recurring transactions per item). It also shows an over time graph depicting how much money they had. The app should look modern and sleek. Do not create a backend for this app." The reason we included the last line is to prevent the [agents](agents.md) from overcomplicating the task and setting up a server with a proper backend system for something like this.
* This shows the list of [agents](agents.md) currently available. Jarvix ships with a few [agents](agents.md) that simulates the SDLC. We're going to grab all of them and add them in this order Planner > Planner Reviewer > Architect > Architect Reviewer > Programmer > Programmer Reviewer > Fixer > QA.
* This screen allows you to choose commands the [agents](agents.md) are allowed to use. Commands are based on which tech stack the [agents](agents.md) will use. So if you want your project to use NodeJS for example, then you select NodeJS and it will whitelist commands related to `nmp` such as `npm audit` for example. For now, we'll pretend we don't know and not select anything.
> Note that Jarvix by default prevents all [agents](agents.md) except the _producer_ role [agents](agents.md) (in this case the Programmer) to run commands. Even if you do not select a stack, Jarvix will attempt to detect them automatically see [Security](security.md) page for more information.
* We'll press "Next" and that is it. You've created your first project.

> Note that if you want to change your brief at any point later you can either click on Menu > Open brief or navigate in you file system to your project folder > Context and then open brief.md with your favorite text editor.

## Anatomy of a project.
Now that we've created a project let's look at what a project is on our disk. First, navigate to your project's folder. You should see something similar to below:

There are three main things to note here:
1. Context folder; this is where your brief lives and later when [agents](agents.md) start working their context or output lives. 
2. Output folder; this is used by the [agents](agents.md) with _producer_ role (in this case the programmer) to create the artifacts (in this case the web app) necessary for the project
3. Pipeline folder; this is where your pipeline settings live. In other words, which [agents](agents.md) are in the pipeline, their state and their order.

Usually you won't need to change anything here but it is good to know where things live if you wanted to modify anything. For example, if you want to review the QA agent report then you can find it in context. If you want to add images for your web app (instead of spending tokens generating placeholder) then you can place them in the appropriate folder inside the Output folder. 


## Running your first pipeline.
Before we run our pipeline it is important to understand how the pipeline works. By default, Jarvix's pipeline works in sequence. This means one [agents](agents.md) does work, it hands the result to the next [agents](agents.md) and that second [agents](agents.md) hands their work to the following [agents](agents.md). It continues in one direction like this until the pipeline is completed. However, introducing an [agents](agents.md) with their role set to _reviewer_ changes this and introduces cycles. Right now, Jarvix supports only 2-agents loops. This means that one [agents](agents.md) will produce some work, another marked as _reviewer_ will review that work and then decide if it fulfills the criteria set out for this [agents](agents.md) or not. If it fulfills the criteria, it passes the work to the next [agents](agents.md) in the sequence. If not, then it returns the pipeline to the [agents](agents.md) to fix its mistakes. This is done through the context files. Each [agents](agents.md) creates a [agent-name].md context file (i.e. planner.md). It writes in it one of two things; first, what it did (i.e. the plan in case of the planner [agents](agents.md)) and a checkpoint check (i.e. done or not, whether it has errors or not). You are able to find those files as mentioned above in the "Context" folder. You can modify those files if you wish -- just remember if you do, it will affect the output of the next [agents](agents.md) consuming that file. 

> Note that this revision loop system has two types as will be mentioned in the [agents](agents.md) page and must be set manually for them to work. The sample [agents](agents.md) come pre-configured based on their roles and what we believe works best in general. You're free to modify them or create new ones.

Given Jarvix gives you control over how you run the pipeline, you can at any point pause the pipeline. Pausing the pipeline does not reset progress but stops the pipeline from progressing. That said, you can also abort the pipeline which will kill the current [agents](agents.md) aggressively and may result in loss of progress and data. When that happens you are given a choice when starting the pipeline again to either start from where you left off or you start fresh.

> Note that starting a pipeline fresh means that all context files created by [agents](agents.md) in the "Context" folder are deleted as well as any artifacts in the "Output" folder.

Now that we undersatnd how the pipeline works, let's start the pipeline:
* Click on the "Start" pipeline button at the top of the Pipeline Status bar. 

When the pipeline is running you can see the current [agents](agents.md) doing work highlighted in the Pipeline Graph as well as the Agents List pane. During the pipeline running you can check the Activity Log pane at the bottom for progress messages. It usually shows information such [agent] started or [agent completeted]. In case any issues occurred this is the window you should first look at. Jarvix outputs helpful warning and error messages in case of any issue that will help you understand what went wrong during your run. 

That said, if you've been following this guide without any changes from your end, then you have a QA [agents](agents.md) and this is where the pipeline will stop. It will tell you that the work has been done but it is time for you to review it to make sure the work matches what you want. The QA [agents](agents.md) ships with an MCP (Model Context Protocol) server that allows yout to communicate your feedback with the QA [agents](agents.md) and the _producer_ role [agents](agents.md) (in this case the programmer). Let's do that. 

* Open your project folder > Output 
* Given our brief gave a lot of agency to implement this, your implementation might be different from mine. However, the key thing is to find an "index.html" file and then double click it. That will launch the web app. 
* Now go back to Jarvix and click "Ready". It will show you instructions on how to grab a screenshot. After you've read it click OK.
* Navigate back to your web app and start using it. When you spot something wrong press `Shift + S` which will grab a screenshot. 

> Note that Jarvix takes a full screen capture. It is recommended that you try and make the artifact (in this case the web app) the dominant element on the screen so it reduces the noise for the [agents](agents.md) to detect what is wrong. That said, we're currently working on an update that would allow you to select a region when capturing screenshots.

* Navigate back to Jarvix to write a note explaining what you saw wrong with the screenshot and then press OK.
* Continue doing this until all issues have been pointed out. 
* When done, click on "Done -- write report" at the top just below the Pipeline Status toolbar.
* Now the QA [agents](agents.md) (_qa_ role) will write a report with what it saw wrong (in case you missed something) and including your screenshots and notes without modification and hand it over to the _fixer_ role [agents](agents.md) (Fixer [agents](agents.md) if you're using the sample [agents](agents.md)).
* After the fixer [agents](agents.md) is done fixing the issues, it will be handed over back to QA which will prompt you back to launch the artifact and press "Ready". Do that now.
* Check the changes and see if there are any issues. If there any, then repeat the steps we've been throw again. If not, then press on "Complete" and that will prompt the QA agent to finalize the pipeline. If you're using sample [agents](agents.md) that means this is the last [agents](agents.md) in the pipeline and no hand over will happen to any other [agents](agents.md).

Congratulations, you've just finished your very first project. You're free to grab the artifact from the "Output" folder and start using it as you see fit. If you've been following this tutorial then this means you can bookmark the page in your browser after you open it and it will launch from the bookmark every time. 

> Note that while it is possible to upload the web app online to a server and it will work, it is by no means set up for this. Not only it may not behave correctly but it is going to be a security liability given it deals with financial information. We recommend that you do NOT do this unless you know what you're doing.


Go back to [getting started](getting-started.md).
Go back to the [welcome page](welcome.md).
