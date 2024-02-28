---
layout: default
title: TriQPAN
permalink: pattern/triqpan/
---

# TriQPAN (Trigger, Query, Process, Action, Notification)

## Intent
The intent of TriQPAN is to record the decision processes of the agent in order to allow the user to query the system and recieve explanations of why the agent made a specific decision.

## Problem
Explaining the decision process of event-driven systems.

## Solution
![triqpan](/xag/patterns/triqpan/triqpan.png)
	
TriQPAN structures the steps of a decision-making process following the Sense-Deliberate-Act loop. Once the decision process has been triggered (e.g. by a perception), it will query its state or known information (e.g., its belief sets), compute or process this information to select the actions to perform, and finally, notify of its actions and completion to other modules of the agent. This observation and the steps are at the core of the TriQPAN pattern. All the components of the decision-making process are documented in the XAgentProcess event that is emitted when the process completes.

## Structure
<p><b>Trigger</b> are instances of events that begin a TriQPAN process. Perceptions are the most typical triggers of behaviours for most agent types, though they can take different forms depending on the specific architecture used for the agent. If the agent is using a goal-oriented architecture, events such as Goal Adopted, Goal Activated or Belief Updated, are candidates triggers.</p>
<p><b>Query</b> step retrieves information from the agent’s mental state. This can be as simple as data structures (e.g., variables) or as complex as querying an ontology knowledge base.</p>
<p><b>Process</b> step queries the data and the trigger to select the appro- priate actions to take (if any).</p>
<p><b>Action</b> step executes one or more actions in response to the trigger. Actions in this pattern should be interpreted as operations the agent is able to do in a broader sense. They can be internal (e.g. update beliefs ) or external (e.g., write to a file, move towards a location).</p>
<p><b>Notify</b> ends the TriQPAN process and is twofold. First, all actions
must notify of any effective change of state (e.g., belief up-
dates). Second, the TriQPAN should fire an event that informs of all the components used. We term this event the XAgent-Process event . Note that the notifications of one TriQPAN can be the trigger of another TriQPAN , for chained decision processes</p>

## Pseudocode

## Applicability
<p>Like any design pattern, TriQPAN must be adapted to the specific agent process it is applied to. We highlight some important considerations when adapting it:</p>
<ul>
	<li>Each TriQPAN must fire a XAgentProcess event that contains all relevant information about the TriQPAN components (i.e., trigger, queries and outputs, actions applied).</li>
	<li>Every action should fire an event that notifies other modules of effective state changes. For instance, when updating a belief a Belief Updated event should be fired. If actions do not directly affect the agent’s state (e.g. actions that affect the external environment only), changes will be captured later by the agent as perceptions as the environment changes.</li>
	<li>A TriQPAN must not contain Action-Query loops. Any process required as a response to an action a should be modelled as a separate TriQPAN using the notification of a’s TriQPAN as the trigger.</li>
	<li>A TriQPAN must be stateless. That is, it can only depend on the information contained in the trigger and the queries made. This stateless feature also means that, given the same trigger and the same query results, the process must apply the same actions ensuring reproducibility. Furthermore, if the XAgentProcess event is correctly constructed, every TriQPAN can be reproduced and verified against its XAgentProcess event . This feature is a result of TriQPAN ’s foundations and inspiration on well-established event-driven patterns such as Event Sourcing and CQRS.</li>
</ul>

## How to implement
<p>To implement TriQPAN the following is required</p>

<ul>
	<li>A event-stream database, such as EventStoreDB.</li>
	<li>A language that supports event-driven and goal-driven activity, such as SARL when the goal engine module is added</li>
	<li>A system that commits all events to an event logger, such as our <a href="https://github.com/hmteams/sarl-eventstoredb-connector" target="_blank">sarl-eventstoredb-connector</a></li>
	<li>Code designed so that all state changes are done via events. This involves stucturing all information as beliefs; an example of this can be seen in our <a href="https://github.com/srodriguez/aamas2024-triqpan-examples/blob/main/src/main/sarl/io/github/hmteams/aamas24/coffee/coffee-beliefs.sarl" target="_blank">coffee example</a></li>


## Pros and cons
### Pros
<p>TriQPAN allows developers to implements an agent system as per usual, with minimal overhead and being able to query the agent systems for information about its behaviours. Further, this enables requirements verification, and may be possible to extend further to enable <i>live</i> requirements verification.</p>

### Cons

## Use cases
When the types of enviroment change can be highly varied; for example, TriQPAN can even support a query like "Why was file paper.tex modified?" (why(FileWritten, paper.tex, t10)), as its event logging ensures that even this is tracked.

## Relations with Other Patterns
N/A
