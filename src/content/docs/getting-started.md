---
title: "Getting Started"
order: 1
---

# What is Wazear?
Wazear is a local, desktop AI orchestrator that allows you to set up [agents](agents.md)s that could simulate the Software Development Life Cycle (SDLC). In other words, it is an app that allows you to create multiple AI [agents](agents.md)s, each with its distinctive role to execute a set of specific tasks. These [agents](agents.md)s can be ordered (chained) to produce an artifact (the product which can be a website, an app, an article, etc...).

# Installing Wazear
Wazear on its own doesn't need anything to run. It only uses [Qwen Code](https://qwen.ai/qwencode) under the hood to create the various [agents](agents.md). When you launch the app for the first time you'll see the onboarding flow which will instruct you to install NodeJS (a requirement of Qwen Code) and Qwen Code. 

# Setting up Wazear
Given Wazear requires [Qwen Code](https://qwen.ai/qwencode) to create its [agents](agents.md), it will need to be setup correctly. The main thing you need to worry about is authentication; how will [Qwen Code](https://qwen.ai/qwencode) access an LLM. There are two ways you can do this:
1. OAuth.
2. API Key

During the onboarding flow, you will be asked to setup your authentication method as seen the first screenshot below. However, you can access the authentication settings by clicking Menu > Preferences > Authentication which will show the authentication setup as seen in the second screenshot below.

## OAuth
This is the simplest method. It requires that you have a [Qwen Chat](https://chat.qwen.ai/) account. You authenticate with your account login and you're done. 

> As of the writing of this document (March 2026) you get 1000 requests per day free. 

That said, sometimes [Qwen Code](https://qwen.ai/qwencode) loses the connection and you will have to relogin again. This method locks you into using the Qwen LLM models only.

## API Key
This requires a bit more setup but offers the most freedom. Since you're using an API key to connect to an LLM provider, you can virtually use any LLM with [Qwen Code](https://qwen.ai/qwencode). To set up your API key:

1. Click on "Menu".
2. Next click on "Preferences"
3. Next click on the "Authentication" tab.
4. From the drop down menu, choose your AI provider. Wazear supports OpenAI, Anthropic, Gemini and OpenRouter. The latter opens up virtually all LLM providers for you.
5. Next, paste your API key in the API field.
6. Type in the name of the LLM model you want to use. For example, if you're using OpenRouter and want to use Z.ai GLM 4.5 then you'd type `z-ai:glm-4.5-air` in that field.
7. Click on "Test Connection" to verify everything is correct. If something is wrong, the error message will tell you what exactly is wrong.
8. If all is well, the "OK" button will be enabled, click on it to save everything.

If you encounter any issues with the authentication process feel free to [Contact Us](https://Wazear.site/contact-us).

## Exploring Wazear
Wazear is made up of 5 main sections; the Pipeline Status bar at the top, the Agents pane, the Pipeline Graph, the Agent Details pane and the Activity Log. 

### Pipeline Status bar
This bar allows you to manipulate the whole pipeline. Clicking on "Start" will start the pipeline and spawn [agents](agents.md) to start working on your project based on their role. You can pause the pipeline and you can also abort it. The pause option is only available when the pipeline running. 

The status text sitting next to the "Start" button can be one of values:
1. Idle; the pipeline hasn't started yet. This is the state when a project has just been opened.
2. Running; the pipeline is currently running and [agents](agents.md) are working on your project producing output based on their roles. 
3. Paused; the pipeline was paused and appears when you pause the pipeline.
4. Waiting_For_User_Input; this appears only when the QA [agents](agents.md) role is currently active and signals you to jump in and provide feedback on the artifacts produced via screenshots and comments.
5. Completed; this appears when all [agents](agents.md) complete their work 

### Agents pane
This sidebar is responsible for displaying your [agents](agents.md). Both the [agents](agents.md) that are in the library; these are [agents](agents.md) that are available to you to pick and choose from. The top part of the pane displays the list of [agents](agents.md) that are currently in the pipeline. Dragging and dropping an [agents](agents.md) from the pipeline [agents](agents.md) section in this pane will reorder them and will reflect in the Pipeline Graph. To manipulate an [agents](agents.md), right click on it.

> Note that [agents](agents.md)' order in Wazear is important. A review [agents](agents.md) (an [agents](agents.md) that reviews work of another [agents](agents.md)) can not exist before the [agents](agents.md) doing the work.

### Agent details pane
By default this pane is hidden and appears whenever you select an [agents](agents.md) either in the Agents pane or the Pipeline Graph. It displays more information about the [agents](agents.md) you selected such as their name, their UUID, their role, etc...

### Pipeline Graph
This is the visual representation of your pipeline. Each [agents](agents.md) hands over their work to the next one building up towards the production of the artifact you want. To manipulate any of the [agents](agents.md) you can right click an [agents](agents.md)'s box and more options will display. 

### Activity Log
Here is where Wazear will communicate with you; it shows helpful messages that portray the state of the pipeline. From when an [agents](agents.md) starts to when an error occurs and what kind of error is it. If something is wrong with your pipeline, this is the first place to check. 

Next we'll [create our first project](creating-first-project.md)
Go back to the [welcome page](welcome.md)
