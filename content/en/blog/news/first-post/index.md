---
date: 2020-05-02
title: "Sandpiper Framework Launched"
linkTitle: "Announcing Sandpiper"
description: "An efficient new way to exchange auto care product and application data."
author: "The Sandpiper Authors"
resources:
- src: "connected-aftermarket.png"
  title: "The Connected Aftermarket"
  params:
    byline: "Jason Riegel, ACP, AAP (ACPN 2019)"
---


# Motivation

This time last year, [Jason Riegel](https://www.linkedin.com/in/jasonriegel/) (then chairman of [ACPN](https://www.autocare.org/who-we-are/segments/acpn/automotive-content-professionals-network/)) challenged our industry to do better. While comparing the disruptive effect of the telegraph for delivering messages across the country to what could happen to us if we didn't act quickly, he famously stated, "our industry is stuck somewhere between the stage coach and the pony express". Clearly, we don't want to be the pony express!

{{< imgproc connected Resize "400x" >}}
{{< /imgproc >}}

Out of that challenge, a seed was planted. There had to be a better way to exchange product data than delivering full files every month!

#  {{< icon >}} The Lightbulb Moment

What if we could use a unique ID to identify each application... that would help, wouldn't it? Yes, but it couldn't ensure we always had a "complete set" of information. If you delete an ID, does that mean you need to replace it with something else? How do we know if we missed an update?

Every "net-change" system we came up with (where adds were matched with deletes), was inherently brittle. We had to make this bullet-proof. How could we ensure that trading partners always remained in sync without exchanging full files, if even occasionally?

The answer turned out to be very simple. It comes down to the basic idea of managing a set of syncable objects. If your set matches my set, then we are in sync. Once an object is assigned a unique ID and placed in a set, it cannot be changed. It can be removed, but never changed.

So now, we don't really care what we're delivering, as long as we can uniquely identify it! This means we can handle ACES, PIES, PartsPRO, Techdoc... virtually *anything* that can be identified and delivered separately.

This simple concept is the basis of Sandpiper.

# Real-Time Delivery

Now we **had the formula** for a reliable delivery mechanism. The engineers in the group immediately moved to the "napkin-drawing phase". It became clear from the start that we didn't need some central hub-and-spoke design. Just like the World Wide Web, all we needed were two servers to talk with each other. If you were a supplier, for example, you'd set up a "subscription" with each company your wanted to share data with (e.g. retailers, ecats, WDs, etc.).

Whenever a change was made to your data, it would alert everyone subscribed to that data, and perform a little dance (a "sync") to make sure your information was up to date.

While the napkin-drawing was impressive, we realized it was a pretty massive jump from where we are today. While (near) "real-time" delivery remains the ultimate goal, it was clear that we needed to walk before we ran.

# Compliance Levels & Adoption

As everyone in our industry knows, one of the biggest challenges with the Data Standards has always been adoption. If a customer wasn't demanding it, it just wasn't seen as a priority. As much as we expect great ideas to be like the movie *Field of Dreams*, "if you build it, they will come", it almost never works out that way.

We knew we needed a super-simple system that would have an immediate benefit, zero disruption, and save time over existing processes. So we came up with the idea of Sandpiper compliance levels:

* **Level-1.** Continue to exchange full-files, but automate the process.
* **Level-2.** Exchange smaller "grains" of information, but make them logically complete such as "pies-item" (all PIES segments for an Item) or "aces-part" (all ACES applications for a part number).
* **Level-3.** Near real-time delivery of atomic grains. The Holy Grail.

# Project Status

We've made great strides in the last several months, but we're really just getting started. We've solved many of the difficult problems (like reference-versioning and data-syncing), but we have much more to do.

This is a **purely volunteer-driven** effort, with many hundreds of hours already contributed. Several companies have graciously allowed resources to be spent on this project during working hours, but we need your help. We need developers, testers, writers, translators... If you see a need, please jump in to fill it!

At the very least, please join our [mailing list](https://mailchi.mp/172fd6548eee/sandpiper). This simple act shows the industry you understand the importance of this initiative.
