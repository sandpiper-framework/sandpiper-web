---
title: "Concepts"
linkTitle: "Concepts"
weight: 3
description: >
  The fundamental concepts of the Sandpiper framework
---

### Basic Terms

Before we go further, there are a few basic terms to introduce, since they're used so often. For more detailed explanations, you can refer to the later parts of the documentation.

In Sandpiper, individuals or individual systems involved in exchanging and hosting data are known as *Nodes*. When they're part of a data exchange, called a *Transaction,* these nodes are known as *Actors*.

Actors exchange data about *Products*. Products (or SKUs, units, items, parts, and so on) are usually goods -- though they can also be services. Sandpiper specializes in the core data that defines these products, which we call *Product Data*: information that, were it to change, would also mean the product or its use itself had changed.

The framework does not make special accommodations for other kinds of data, which we call *Non-Product Data*, even when it is product adjacent.
