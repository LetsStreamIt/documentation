---
sidebar_position: 3
---

# Event Storming

The knowledge crunching session has been carried out using the [Event Storming](https://www.eventstorming.com/) approach. It is a workshop-based method where developers and domain experts work together to identify the domain of the project. Using sticky notes with different colors, the method iteratively asks the team members to include different information, such as domain events, command and reactions. Finally, the chart with the bounded contexts is produced.
All the different steps are delighted in the following sections.

## Unstructured exploration

The first step of the Event Storming approach is defining the main domain events that can happen in the system. The sticky notes should be put in a whiteboard, without any specific order.

![Unstructured Exploration](/img/ddd/event_storming/unstruct_expl.jpg)

## Timeline

The domain events defined in the previous sections are ordered by time and arrows are drawn to indicate their dependency.


![Timeline](/img/ddd/event_storming/timeline.jpg)


## Pan Points

The team members should spot potential problems that can occur in the system and may need special attention.


![Pan Points](/img/ddd/event_storming/pan_points.jpg)


## Pivotal points

Pivotal points are points where the system could be split in multiple bounded context.


![Pivotal Points](/img/ddd/event_storming/pivotal_points.jpg)


## Commands

The team identifies the commands that trigger the domain events, and their respective actor.


![Commands](/img/ddd/event_storming/commands.jpg)


## Policies

Policies are commands without an actor, that are executed in the system.


![Policies](/img/ddd/event_storming/policies.jpg)

## Aggregates

The team members identify the aggregates of the system. They are defined as clusters of domain objects that can be treated as a single unit.


![Unstructured Exploration](/img/ddd/event_storming/aggregates.jpg)


## Bounded Contexts

Finally, the bounded contexts of the system are identified. Each one works with its internal representation of the domain. For different bounded context same concepts may have completely different models. In such cases, a mapping between these models is needed,  whenever they should be integrated. 

The domain of this project is however rather simple and the separation between the bounded context is complete. This means that they don't share any common concept.


![Bounded Contexts](/img/ddd/event_storming/bounded_context.jpg)

The bounded contexts of the system are:
- `Auth`: manages everything concern user authentication;
- `Profile`: manages everything concern user profile;
- `Session`: manages everything concern a streaming session;