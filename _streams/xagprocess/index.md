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
To import streams to EventStore, follow the following steps:
<ol>
	<li>Download the streams</li>
	<li>Download the <a href="https://github.com/hmteams/eventstore-transfer-tool" target="_blank">Event Store Transfer Tool</a> (Python 3.6 or higher and the `requests` library are required)</li>
	<li>Ensure your intended EventStore is online.</li>
	<li>Run the tool. This can be done through interactively (eg `python access-stream.py`) or through the command line (eg `python access-stream.py -m import -sn coffee-example -f coffee_example.tar.xz`)</li>
</ol>

### Examples
<ul>
	<li><a href="https://github.com/hmteams/xag/tree/main/_streams/xagprocess/agent_cities_example.tar.xz" target="_blank">Agent cities example</a></li>
	<li><a href="https://github.com/hmteams/xag/tree/main/_streams/xagprocess/coffee_example.tar.xz" target="_blank">Coffee example</a></li>
	<li><a href="https://github.com/hmteams/xag/tree/main/_streams/xagprocess/drone_example.tar.xz" target="_blank">Drone example</a></li>
</ul>
