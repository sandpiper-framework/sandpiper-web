---
title: "Object Model"
linkTitle: "Object Model"
weight: 4
type: docs
description: >
  The Sandpiper conceptual object model
---

### Object Model

<img src="/images/Object_Model_Links.png" alt="Sandpiper model diagram showing links on persistent objects" title="The Sandpiper Object Model" width="50%" style="float: right; clear: right; padding: 1em"/>

The object model for Sandpiper defines a set of common abstractions for the product data each node stores. There are just four persistent objects (*Node*, *Pool*, *Slice*, and *Grain*) and two reference objects (*Link* and *Subscription*). All Sandpiper objects have a universally unique ID that will be used for actions exclusively whenever possible.

The node represents the root of one self-contained Sandpiper environment, with one controller. It contains pools of product data, each with one owner. These pools are further subdivided into slices, each representing one set of the same type of data and specifying how it is internally organized. That data is finally broken into grains by the method of organization named on the slice.

To structure this data and aid the creation of shared scope between actors, the persistent object types can employ links: references to additional systems, descriptions, and data. To create the bond between actors, the secondary actor establishes subscriptions to the slices available.

#### Persistent Objects

##### Nodes

The node is a single Sandpiper instance or system^[While a server might run multiple concurrent copies of the Sandpiper software and thus represent multiple nodes, for simplicity we just refer to the node as a system, as this is the most common use case.]. It has a *Controller* responsible for, though not necessarily the originator of, its operation and contents.


{{% alert title="Note" %}}

A human interacting at Level 1-1 is technically a node, though their data state is unknown after retrieval.

{{% /alert %}}

##### Pools

Within each Sandpiper node, product data is stored in broad banks called *Pools*. These represent a business or management-level division, so that a single node might contain product data spanning multiple business approaches yet being coordinated within one system.

While a node has a controller, a pool has a *Creator*, the owner of the product data within. In some cases this will be the same as the controller, and in others it will be different. For example, if the node operator works for a shared services provider that offers data synchronization for multiple customers, the controller will be the provider, and the creator will be the customer.

Pools can be one of two types: *Canonical* or *Snapshot*.

A node's canonical pools contain the data that it owns and controls; changes made to a local node's canonical pools can be transferred to external Sandpiper nodes, with the local node as the origin point.

A node's snapshot pools contain copies of the data in other nodes' canonical pools transferred in this way. A snapshot pool is just that: a snapshot of some or all of the data in a canonical pool from an external node, at its last-known state.

##### Slices

<img src="/images/SliceGrain.png" alt="Slices and grains" title="Slices and grains" width="40%" style="float: right; clear: right; padding: 1em"/>

A pool is divided into *Slices*. The slice is the fundamental unit of Sandpiper; basic transactions are expected to operate only on the slice, and it provides the context for all more complex transactions as well. It can be thought of as the file level of the data.

A slice defines the single type, format, and version of the data it contains (e.g. "Fitment", "ACES XML", "3.0"). It also defines a URI to access the data, a filename for Level 1 transactions, and a slice type that indicates how the file is granulated.

##### Grains

A slice is broken into *Grains*, each representing one unit of meaning or scope. It can be thought of as the element level of the data.

Grains have a *Grain Key* containing a single text value, to safely and atomically operate on the data in pieces smaller than a whole slice. This value must be a single unicode key that directly references one key value within the data, e.g. a part number or a UUID. It must not be an artificially packed or delimited set of values referring to more than one key within the data.

The grain is the smallest unit on which a Sandpiper node can act, and can only be directly addressed in Level 2 and higher transactions.

#### Reference Objects

##### Links

Links are references that allow slices to be tied to other systems and tagged with nonstandard metadata.

The link is the primary means of attaching overarching structure to slice data. Every partnership will have a different preferred method for establishing things like line codes, hierarchies, and sets, so the link provides a few standard methods to do this and an extensible category for what it doesn't define.

The link is also the way Sandpiper connects slice data to description or validation frameworks like reference database versions, business identities, and so on.

##### Subscriptions

The secondary actor in a Sandpiper relationship can subscribe to a slice, stating its intention to mirror that data and keep it synchronized with the primary actor.

This subscription includes the secondary actor's stated preference for receipt of the data, particularly the frequency of synchronization. In future versions, this may also include whether it should be pushed or pulled, what methods should be employed, what schedule should be followed, and what credentials will be used.
