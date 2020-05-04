---
title: "Data Processing, Input, and Output"
linkTitle: "Data Processing, Input, and Output"
weight: 1
type: docs
date: 2020-05-04
description: >
  Getting data in and out of Sandpiper and the processing the server undertakes
---

The Sandpiper server is focused on delivery and receipt of data to preserve one source for the unambiguous truth around what is available for use. It is both a repository for the product data and a mechanism for resolving differences between multiple repositories.

Because this is its focus, the server does not attempt to parse or understand the data it contains -- only its state. This means that the server itself will not be able to perform the rendering process to create grains.^[Splitting an XML file into grains, for example, is highly domain-specific, depending on its format, version, and content. Attempting to natively decode and securely implement this conversion would lead to unacceptable code and scope bloat in an otherwise tightly-specified program.]

For Level 1, which operates at the slice only, this makes no difference; the grain is never engaged. For Level 2 and higher, though, Sandpiper exposes commands to input grains, allowing external toolchains (for short, called *Granulators*) to parse full data into grains.

In these sections, we'll refer to the source of the original data as the *PIM:* the Product Information Manager.^[The word "PIM" is ambiguous; it could mean a single program that handles all product information, a combination of systems, or just a human being handling spreadsheets. We use it here as a convenient catch-all term.] The Sandpiper framework classifies PIMs in three tiers:

| Tier               | Description
| --                 | --
| Classic            | Output of single files that are communicated traditionally via email, FTP, or web portal
| Sandpiper-Aware    | Can execute Sandpiper commands and supporting tools externally, though not query the data or use the API directly
| Sandpiper-Capable  | Can transfer information directly into a Sandpiper server and query the data to make intelligent decisions about updates

### Granulation

Slices have one type of grain that they contain; either "full-file" to mean that it is a Level 1 full file slice, or another value that indicates the type of grains it contains.

<img src="/images/Granulation_ExampleMasterPIES.png" alt="Master Slice Linking Example" title="Master Slice Linked to Granulated Slices" width="50%" style="padding: 1em; float: right; clear: right;"/>

Once a full file slice has been created, additional slices can be added to contain different granulations of that data. These are connected to the main slice using a *Master Link*, a standard link object in the plan that specifies the system "Master" and keys to the slice ID of the full file.

In this way, a file with multiple segments can be broken out for processing at Level 2. An Auto Care PIES file, for example, contains segments that are very differently structured; the Items segment contains repeating Item elements containing the bulk of the product information, but the PriceSheets segment contains repeating PriceSheet elements that include pricing-specific information. The full file would be one slice with slice type "file", and two additional slices of slice type "pies-pricesheet" and "pies-item".

### Input Workflow

The capabilities of the data source will direct the workflow that's most efficient. Classic PIMs require some user intervention, and more modern PIMs reduce that need.

#### Classic PIM Input

<img src="/images/Input_ClassicPimL1.png" alt="Classic PIM Level 1 Input Workflow" title="Classic PIM - Level 1" width="40%" style="padding: 1em;"/>

Level 1, being file-based, is designed for classic PIMs that can't use or haven't yet been adapted to use the Sandpiper framework. The PIM outputs files, and the user loads them into the Sandpiper server using the commandline interface.

<img src="/images/Input_ClassicPimL2.png" alt="Classic PIM Level 2 Input Workflow" title="Classic PIM - Level 1" width="40%" style="padding: 1em;"/>

Level 2 introduces the ability to split complete datasets into grains. The server itself does not attempt to parse or interpret data, yet classic PIMs have no internal capacity to do this. Sandpiper is designed to support this scenario but to do so it will need an external, domain-specific tool to do so (called a *Granulator.*)

#### Sandpiper-Aware PIM Input

<img src="/images/Input_SandpiperAware.png" alt="Sandpiper-Aware PIM Input Workflow" title="Sandpiper-Aware PIM" width="40%" style="padding: 1em;"/>

Sandpiper-Aware PIMs are able to use Sandpiper commands to do basic import and launch other tools. This may take the onus off of the user to manually import the data, though the process is likely only semi-automated.

#### Sandpiper-Capable PIM Input

<img src="/images/Input_SandpiperCapable.png" alt="Sandpiper-Capable PIM Input Workflow" title="Sandpiper-Capable PIM" width="40%" style="padding: 1em"/>

Sandpiper-Capable PIMs can communicate directly with the Sandpiper server, so for day-to-day operations the user does not need to engage any external tools while updating data.

### Output Workflow

As with input, the capabilities of the PIM receiver will direct the most efficient workflow.

#### Classic PIM Output

<img src="/images/Output_ClassicPimL1.png" alt="Classic PIM Level 1 Output Workflow" title="Classic PIM - Level 1" width="40%" style="padding: 1em"/>

The classic PIM, without additional development, can make use of a purely Level 1 output process. The Sandpiper server, after synchronization with the primary Sandpiper node, outputs files via the CLI. The PIM then imports these using established processes.

<img src="/images/Output_ClassicPimL2.png" alt="Classic PIM Level 2 Output Workflow" title="Classic PIM - Level 1" width="40%" style="padding: 1em"/>

With an integration process, a classic PIM can also use the results of Level 2 transactions. More advanced recipients often already have a process to do something similar (for example, by comparing existing files to data in the PIM). Using the Sandpiper API and/or CLI, an external migration program can offload this change comparison to the deterministic Sandpiper framework, yet feed the PIM in the way it's already operating.

#### Sandpiper-Aware PIM Output

<img src="/images/Output_SandpiperAware.png" alt="Sandpiper-Aware PIM Output Workflow" title="Sandpiper-Aware PIM" width="40%" style="padding: 1em"/>

Sandpiper-Aware PIMs may not directly integrate Sandpiper into their logic, but can trigger regular loads and audits using external commands.

#### Sandpiper-Capable PIM Output

<img src="/images/Output_SandpiperCapable.png" alt="Sandpiper-Capable PIM Output Workflow" title="Sandpiper-Capable PIM" width="40%" style="padding: 1em"/>

Sandpiper-Capable PIMs speak directly to the Sandpiper server via the API, integrating the functions so that no external tooling or user intervention is required.
