# What is Fluent Bit?

**Fluent Bit:** is a Fast and Lightweight Logs and Metrics Processor and Forwarder for Linux, OSX, Windows and BSD family operating systems. It has been made with a strong focus on performance to allow the collection of events from different sources without complexity.
Fluent Bit is a CNCF sub-project under the umbrella of Fluentd

**Fluent Bit:** is an open source and multi-platform log processor tool which aims to be a generic Swiss knife for logs processing and distribution.
Handling data collection at scale is complex, and collecting and aggregating diverse data requires a specialized tool that can deal with:
- Different sources of information
- Different data formats
- Data Reliability
- Security
- Flexible Routing
- Multiple destinations


## Key Concepts:
There are a few key concepts that are really important to understand how Fluent Bit operates.
- Event or Record
- Filtering
- Tag
- Timestamp
- Match
- Structured Message

## Event or Record
Every incoming piece of data that belongs to a log or a metric that is retrieved by Fluent Bit is considered an Event or a Record.
As an example consider the following content of a Syslog file:
Jan 18 12:52:16 flb systemd[2222]: Starting GNOME Terminal Server
Jan 18 12:52:16 flb dbus-daemon[2243]: [session uid=1000 pid=2243] Successfully activated service 'org.gnome.Terminal'
Jan 18 12:52:16 flb systemd[2222]: Started GNOME Terminal Server.
Jan 18 12:52:16 flb gsd-media-keys[2640]: # watch_fast: "/org/gnome/terminal/legacy/" (establishing: 0, active: 0)

## Filtering
In some cases it is required to perform modifications on the Events content, the process to alter, enrich or drop Events is called Filtering.
There are many use cases when Filtering is required like:
- Append specific information to the Event like an IP address or metadata.
- Select a specific piece of the Event content.
- Drop Events that matches certain pattern.

## Tag
Every Event that gets into Fluent Bit gets assigned a Tag. This tag is an internal string that is used in a later stage by the Router to decide which Filter or Output phase it must go through.
Most of the tags are assigned manually in the configuration. If a tag is not specified, Fluent Bit will assign the name of the Input plugin instance from where that Event was generated from.

## Timestamp
The Timestamp represents the time when an Event was created. Every Event contains a Timestamp associated. The Timestamp is a numeric fractional integer in the format:
A timestamp always exists, either set by the Input plugin or discovered through a data parsing process.

## Match
Fluent Bit allows to deliver your collected and processed Events to one or multiple destinations, this is done through a routing phase. A Match represent a simple rule to select Events where it Tags matches a defined rule.

## Structured Messages
Source events can have or not have a structure. A structure defines a set of keys and values inside the Event message. As an example consider the following two messages:
**No structured message**
"Project Fluent Bit created on 1398289291"
**Structured Message**
{"project": "Fluent Bit", "created": 1398289291}
At a low level both are just an array of bytes, but the Structured message defines keys and values, having a structure helps to implement faster operations on data modifications.

Fluent Bit **always** handles every Event message as a structured message.







