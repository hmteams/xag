---
layout: default
title: XAgProcess
permalink: stream/xagprocess/
---

# XAgProcess Event Overview

The XAgProcess proposes a uniform format to notify XAg decision processes.
The initial format was proposed as part of the [TriQPAN]({{ site.baseurl }}/pattern/triqpan) pattern.



# Message Format

## Version 0: SARL implementation

```sarl
event XAgentProcess {
	val implementation : Class<? extends AgentTrait>
	val name : String
	val trigger : Event
	val triggerClass : Class<? extends Event>

	val criteria : Map<String, Object> = newHashMap
	val queries : Map<String, Object> = newHashMap
	val actions : Map<String, Object> = newHashMap
	
	new(name: String, impl : Class<? extends AgentTrait>, trigger : Event) {
		this.implementation = impl
		this.trigger = trigger
		this.triggerClass = this.trigger.class
		this.name = name
	}
}

```

## Version 1: Standard Protobuf

A new version of the XAgProcess event based on [Protobuf](https://protobug.dev) is being develop.

Definition and APIs are located in its own repository [XAgProcess Protobuf](https://github.com/hmteams/xagevents)

Version 1 is still under development. To have early access, please contact [Sebastian Rodriguez](http://sebastianrodriguez.com.ar)


# Streams

Streams are provided for researchers to explore query languages and explanation engines; human-machine interfaces; and (improved) XAg notification event formats.

## Version 0 Message Format

~~ Instructions to import streams in Event Store ~~


### Agents in the City example

### Drone example

### Coffee example
