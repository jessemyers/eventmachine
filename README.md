# eventmachine

Opinionated, distributed, event-driven state machines


## Goal

[Event-Sourcing is hard](https://chriskiehl.com/article/event-sourcing-is-hard). [In practice](https://github.com/globality-corp/microcosm-eventsource), one way to succeed with event-sourcing is to use events to *drive* distributed state machines in a microservice architecture. Specifically:
 -  Events are **owned** by a relevant microservice. There is no single, global event log.
 -  Events are **broadcasted** through some PubSub framework. Separate microservices update their event logs in response to changes in other microservices.
 -  Events are **regulated** by a state machine. Events must have rules that dicate whether they may *follow* other events in the stream and logic that controls how they *aggregate* state over time.
 
All of the above is very workable as long as the state machine logic is consistent over time. `eventmachine` is an attempt to codify these rules and introduce versioning semantics that create maintanable coherency.
