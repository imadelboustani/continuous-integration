# continuous-integration with teamcity

## What is Continuous Integration?
>   Continuous Integration is a software development practice in which developers commit code changes into a shared repository several times a day. 
Each commit is followed by an automated build to ensure that new changes integrate well into the existing code base and to detect problems early.

## What is TeamCity?
>   JetBrains TeamCity is a user-friendly continuous integration (CI) server for developers and build engineers

## Basic CI Workflow in TeamCity

To understand the data flow between the server and the agents, what is passed to the agents, how and when TeamCity gets the results, let's take a look at a simple build lifecycle.

1. The TeamCity server detects a change in your VCS Root and stores it in the database.

2. The build trigger sees the change in the database and adds a build to the queue.

3. The server finds an idle compatible build agent and assigns the queued build to this agent.

4. The agent executes the Build Steps. While the build steps are being executed, the build agent reports the build progress to the TeamCity server sending all the log messages, test reports, code coverage results, etc. to the server on the fly, so you can monitor the build process in real time.

5. After finishing the build, the build agent sends Build Artifacts to the server.

## Build Configuration for cloud monitoring 
>  A Build Configuration is a collection of settings used to start a build and group the sequence of the builds in the UI, 
Build configuration settings include:

-	General settings

-	Version control settings, defining how the source code is retrieved from VCS, where it is checked out to, and so on

-	Build steps, that are sequentially run actions

-	Triggers, which are rules defining when to start a new build

-	Failure conditions specifying when a build will be marked as failed

-	Additional build features

-	Dependencies:

-	Parameters which allow sharing settings

-	Agent requirements specifying whether a build configuration can run on a particular build agent.

 ## Build Steps 
 
 #### 1-  Install Telegraf 
   to run powershell script to install telegraf service in windows 
   
   
 ### 2- unit test
   we confihure teamcity to execute powershell tests using pester to verify if the service is installed 
 > Pester is a Behavior-Driven Development (BDD) based test runner and mocking framework for PowerShell.
 
 TeamCity don't comme with built in support for pester tests so we should to configure it so the pester 
 powershell scripts are considered as unit tests in TeamCity to acheive that we use two Build Feature in Teamcity 
 
 >  A build feature is a piece of functionality that can be added to a build configuration to affect running builds or reporting build results. The Build Configuration Settings | Build Features page displays the configured features and allows you to manage them.
 
#### 2.1-  Build Feature – Test Results

