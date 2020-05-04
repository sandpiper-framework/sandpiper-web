---
title: "Interaction Model"
linkTitle: "Interaction Model"
weight: 5
type: docs
description: >
  The Sandpiper model of the interactions between actors
---

Sandpiper's main goal is to facilitate repeatable, deterministic data transfer, and to do this it lays out a model for node interaction.

<img src="/images/Interaction_Model_Overview.png" alt="Sandpiper model diagram showing the division of objects" title="The Sandpiper Object Model" width="90%" style="padding: 1em"/>

1. A system or human connecting to another through Sandpiper is known as an *Actor*.
2. Any information transfer between actors is known as an *Exchange*.
3. Exchanges are established and next steps are unlocked through *Negotiation*.
4. Transferring product data and resolving pools as part of an exchange is known as *Synchronization*.
5. Two Actors’ operations and communications during synchronization are part of a single *Transaction*.
6. After synchronization, actors communicate about the data exchanged and sign off on the results during *Confirmation*.

Data transfer is only one-way: in any transaction only one actor will receive product data.

### Actors

In the context of a transaction, nodes, humans, and systems assume a role as an actor. Any transaction has only two actors: a *Primary Actor* and a *Secondary Actor.*

The primary actor is the sender of data, responsible for providing information about and issuing updates from its canonical pools.

The secondary actor is the recipient of data. This actor can be a human or a full Sandpiper node. The former is known as *Basic Secondary Actors*, because it cannot engage in a true Sandpiper exchange, and the latter are known as *Advanced Secondary Actors*. Advanced secondary actors are responsible for providing information about their snapshot pools as well as processing updates provided by the primary actor.

### The Plan

The *Plan* is the foundational document that establishes the actors involved, the types and shapes of data available, and how the actors are able to proceed.

### Levels

Sandpiper defines common minimum thresholds of capability for systems, so that simple needs can be met easily by basic implementations, and advanced needs can be met with more advanced implementations. In Sandpiper, these capabilities are grouped into *Levels*, with the lower levels having less functionality and the higher more.

Higher levels inherit the capabilities of the lower levels, and are aware of the elements defined in them. However, to maintain sanity, they cannot normally modify the data of lower levels; as the interaction proceeds, Sandpiper conceptually steps up and down the levels, so that a Level 1 interaction is the first initiated.

Some levels may have sub-levels; these will be written in the format L-n, where L is the level and n is the sub-level. For example, Level 1-1.

#### Level 0

<img src="/images/Level0.png" alt="Level 0 Conceptual Diagram" title="Level 0" width="40%" style="float: right; clear: right; padding: 1em"/>

Though not actually actionable within Sandpiper, the framework defines a prototypical Level 0 to represent uncontrolled product data exchange. Level 0 represents human-to-human interaction where actual files are sent between humans operating computers, who make agreements between themselves about how these files should be processed, their scope, and so on.

The only mechanism for this exchange is human-to-human.

#### Level 1

Level 1 is the first and simplest method of communicating product data. Information is exchanged in complete collections as files, which must replace all of the data stored at the recipient.

Level 1 is equivalent to sending full files between partners manually, but with the benefits of the Sandpiper framework's metadata, automation and validation.

This level is periodic and delivery-based. It has two sub-levels to serve either human-machine or machine-machine interaction; this must be chosen during negotiation.

##### Level 1-1: Basic Exchange

<img src="/images/Level1-1.png" alt="Level 1-1 Conceptual Diagram" title="Level 1-1" width="40%" style="float: right; clear: right; padding: 1em"/>

A Level 1-1 basic exchange begins with the plan but never proceeds into synchronization; it allows a human to connect to a machine, complete the plan, and retrieve full files. Currently the only supported method for Level 1-1 is a human connecting to a Sandpiper server's web UI as a data portal.

##### Level 1-2: Advanced Exchange

<img src="/images/Level1-2.png" alt="Level 1-2 Conceptual Diagram" title="Level 1-2" width="40%" style="float: right; clear: right; padding: 1em"/>

Level 1-2 advanced exchanges can only occur between two Sandpiper nodes, machine-to-machine. They do not not use portal-driven delivery; rather, nodes transfer files directly between nodes using the Sandpiper transport.

##### Level 1 Negotiation

To start, in Level 1, nodes declare themselves, define their capabilities, and agree on their actions. The chief mechanism for this definition is the plan, as an XML file passed back and forth, with the actors filling in their proposed states and accepting or rejecting the changes.

All subscriptions occur at the slice, using its unique ID. It is not possible to retrieve data at any higher or lower position in the object model at Level 1; for that, Level 2 and beyond must be engaged.

A secondary actor cannot subscribe to or see snapshot pools held by the primary actor.

##### Level 1 Delivery

Through its subscriptions, the secondary actor indicates its preference for delivery of files containing all the data contained in one or more slices within the primary actor's canonical pools. It will receive or retrieve this data on a set schedule and via methods both defined in the plan.

##### Level 1 Integration

The secondary actor's node *must* archive or delete all previous data associated with the unique ID of the slices it received, replacing it in full with the new data received.

#### Level 2

<img src="/images/Level2.png" alt="Level 2 Conceptual Diagram" title="Level 2" width="40%" style="float: right; clear: right; padding: 1em"/>

Level 2 provides the ability to use an interface-driven mode where data may be modified in more targeted pieces, still in the periodic subscription paradigm but at a lower level.

The primary means of this interaction is via the Sandpiper protocol. This and further interactions must be performed machine-to-machine.

Level 2 will be defined in more detail as part of Sandpiper 1.0.

#### Level 3

Level 3 opens realtime communication of changes via a push mechanism.

Level 3 is not currently defined in detail; it will be part of Sandpiper 2.0.
