---
layout: default
title: TriQPAN
permalink: triqpan/
---

# TriQPAN (Trigger, Query, Process, Action, Notification)

## Intent
The intent of TriQPAN is to record the decision processes of the agent in order to allow the user to query the system and recieve explanations of why the agent made a specific decision.

## Problem
Explaining the decision process of event-driven systems.

## Solution
![triqpan](/patterns/triqpan/triqpan.png)

TriQPAN structures the steps of a decision-making process following the Sense-Deliberate-Act loop. Once the decision process has been triggered (e.g. by a perception), it will query its state or known information (e.g., its belief sets), compute or process this information to select the actions to perform, and finally, notify of its actions and completion to other modules of the agent. This observation and the steps are at the core of the TriQPAN pattern. All the components of the decision-making process are documented in the XAgentProcess event that is emitted when the process completes.

## Structure
'''Trigger''' are instances of events that begin a TriQPAN process. Perceptions are the most typical triggers of behaviours for most agent types, though they can take different forms depending on the specific architecture used for the agent. If the agent is using a goal-oriented architecture, events such as Goal Adopted, Goal Activated or Belief Updated, are candidates triggers.<p>
'''Query''' step retrieves information from the agent’s mental state. This can be as simple as data structures (e.g., variables) or as complex as querying an ontology knowledge base.<p>
'''Process''' step queries the data and the trigger to select the appro- priate actions to take (if any).<p>
'''Action''' step executes one or more actions in response to the trigger. Actions in this pattern should be interpreted as operations the agent is able to do in a broader sense. They can be internal (e.g. update beliefs ) or external (e.g., write to a file, move towards a location).<p>
'''Notify''' ends the TriQPAN process and is twofold. First, all actions
must notify of any effective change of state (e.g., belief up-
dates). Second, the TriQPAN should fire an event that informs
of all the components used. We term this event the XAgent-
Process event . (See Figure 5 for an example.) Note that the
notifications of one TriQPAN can be the trigger of another
TriQPAN , for chained decision processes (See Figure 3 for
an example).

## Pseudocode

## Applicability
TriQPAN is applicable for event driven systems; this isn't limited to goal-driven event driven systems, although it was initially designed with those in mind.

## How to implement
To implement TriQPAN two elements are required.

First, a system that commits all events to an event logger, such as our ... (link here)

Second, the code must be designed so that all state changes are done via events, such as our ... (link here)

## Pros and cons
### Pros

### Cons

## Use cases
When the types of enviroment change can be highly varied; for example, TriQPAN can even support a query like "Why was file paper.tex modified?" (why(FileWritten, paper.tex, t10)), as its event logging ensures that even this is tracked.

## Relations with Other Patterns
N/A
