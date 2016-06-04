---
layout: post
title:  "Infrastructure Automation at Synapticon"
date:   2016-04-23
categories: infrastructure automation
---
Over a year ago [Synapticon][synapticon] was running all of its web services and tools scattered accross several machines from various cloud infrastructure providers.

The process of managing these machines was manual and consisted of remote login followed by typing all the commands necessary until the machines are configured to a required state.

Due to increasing number of services with distinct runtime requirements the laborious undertaking of manual management was not viable anymore. It was to risky to upgrade a library or a service because it could influence the operation of other services. No single person in the organization knew all the services that a machine was running.

We were on a mission to bring sanity to the infrastructure management. Automation and isolation echoed through the halls. Buuuh-huuuuh...

For me personally the following two issues are more important than the others:

1. lack of isolation,
2. no insight into the current state.

Lack of isolation
-----------------

asdf

No insight into the current state
--------------------------------



There are many ways to solves this issue, like keeping track or reporting, but nothing beats the source code. Especially if it's versioned source code which gives you insight not only into the current state, but of any state that lead to a machine that you observe today.



Tools of choice
-----------------

Process
-------

Two branches, commit, build, test, create a docker image, push, run ansible, deploy

asdf

Tools as languages can influence the way you think.

asfasfd

Reason: World is on fire

Ansible:

Declarative No bullshit

Insight into the current state

We were onto a mision to solve two issues:
- lack of isolation
- lack of insight of the current state

Is this change going to break any service?
What has changed on the server and when?



all the code in one file


j
Lack of isolation


insight about the current state

system package manager, or downloaded, what version are you using, is it compatible with all the software 


compilers, nodejs, tomcat, rails, puma, apache, 

to build and run

no isolation

Identity management system
Revision Control System
Issue tracking and project management

[synapticon]: https://synapticon.com
