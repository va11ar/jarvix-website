---
title: "Sample Agents"
order: 3
---

When you first launch Wazear and go through the onboarding process, you will be asked whether or not you want to use the sample agents that ship with it. Wazear ships with a set of predefined agents that simulate the SDLC and they are in order:
1. Planner
2. Planner Reviewer
3. Architect
4. Architect Reviewer
5. Programmer
6. Programmer Reviewer
7. Fixer
8. QA

> Note that agent order is extremely important. If you place a reviewer type agent before its target, the pipeline may misbehave and you may end up with unwanted results.

Each of those agents has a distinct role in the pipeline and you are free to use them all, some of them or none of them. For general information on agents or how to create an agent check the [agents](agents.md) page. In this page we'll go through each agent and what it does:

## Planner
You can think of the planner agent as a lite task planner. It goes through your brief then comes up with a list of tasks that are required to finish the project. 

## Planner Reviewer
This agent's role is to review what the Planner came up with and then decide whether or not it is good enough for the Architect agent to execute its job. If it is not good enough, then it will return execution order in the pipeline to the Planner with commentary about what is wrong to help it fix its mistakes. 

## Architect
The Architect's role is to take the plan from the Planner agent and then determine what kind of tech stack would be suitable to execute this project and the overall architecture of the project. 

## Architect Reviewer
Similar to the Planner Reviewer, this one reviews the Architect's output. It goes through the tech stack and the entire architecture laid out and confirms whether it suits the project (based on the Planner and brief). If it finds the architecture inadequate it returns the execution order in the pipeline to the Architect with commentary so the Architect can fix it correctly. 

## Programmer
As the name implies, this agent writes code based on architecture laid out in the project. It takes that as an input and turns it into files and code forming the artifact (website, app, etc...) that your brief wants produced. 

## Progammer Reviewer
Another reviewer type agent, this one goes over the artifacts produced by the programmer and contrasts against the project requirements. If they don't execute the intention of the project it returns the execution order in the pipeline to the Programmer along with comments on what is wrong to be fixed. 

## Fixer
This is a clone of the Programmer agent with a few tweaks. This one focuses soleley on fixing bugs relayed to it by the QA agent. 

## QA
This agent has two main tasks. First it allows you to capture screenshots and feedback on issues you may spot in the project. The second, it adds its own comments and feedback critiquing the result compared to the produced artifacts. While the Programmer Reviewer strictle reviews code quality and architecture, this one reviews functionality. Once both tasks are done, it compiles everything into a report and sends it over to the Fixer agent to handle it.
