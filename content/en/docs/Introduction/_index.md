---
title: "Introduction"
linkTitle: "Introduction"
weight: 1
description: >
  The Sandpiper Project
---

{{% pageinfo %}}
An overview of the Sandpiper Project's goals and origins.
{{% /pageinfo %}}

### About

Sandpiper establishes a common, decentralized method to classify, distribute, and synchronize product data between a canonical sender and a derivative receiver. To do this it defines, as unambiguously as possible, both a model for interaction and shared vocabulary to describe the many moving pieces involved.

Sandpiper tries to do this one thing well, and does not attempt to branch into other realms better handled by dedicated tools.

### Background

This is the reference documentation for v0.8 of the Sandpiper Framework, a cross-platform, open-source product data synchronization initiative by members of the automotive aftermarket. Increasingly, product data resides in more systems, is more difficult to update, is less verifiable, and requires increasingly variable and proprietary methods to deliver.

The founding members of the team come from the automotive aftermarket industry, where the broad range of products sold (from consumer electronics to pistons and everything between) combine with stringent certifications of fitment and detail to create massive catalogs of data that must be updated regularly. A medium-sized aftermarket supplier will have tens of thousands of SKUs, hundreds of thousands of pictures, and millions of rows of fitment data to communicate to dozens of receivers monthly. To complicate matters further, no unambiguous standard for partial data delivery exists, meaning all of this data has to be sent in full to propagate even a single change.

Yet while this project began in the automotive world, the problem is one that extends to all product data, regardless of industry; though various industry and partner-specific standards and formats exist to describe products, there's no standard way to actually *send* them, to change just one piece of one product's data, or to make sure that what *was* sent actually covers what was requested. This applies as much to T-shirts as it does to spark plugs.

We believe the Sandpiper framework can make this process a little less painful for everyone who has to get information about their products into the world.
