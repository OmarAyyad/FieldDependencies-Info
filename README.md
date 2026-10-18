# Field Dependencies

**Dynamics 365 & Dataverse Field Dependency Analyzer for XrmToolBox**

Made by Omar Mohamed Ayyad

![Field Dependencies](assets/field-dependencies-128.png)

Field Dependencies is a tool for [XrmToolBox](https://www.xrmtoolbox.com/). You select a table and a field,
choose where to search, and it lists the places in your organization that reference the field, how each of
them uses it, and the evidence for it. It helps you understand where a field is used before you change or
remove it.

This page describes the tool. It holds no source code: Field Dependencies is free to use, and its source code
is not published.

## Install

Open XrmToolBox, choose **Tool Library**, search for **Field Dependencies** and install it.

The package the Tool Library installs is `OmarAyyad.XrmToolBox.FieldDependencies` on nuget.org. It is meant to
be installed from XrmToolBox, not referenced from a project.

## What it does

- Searches the components you select: forms, views, charts, business rules, classic workflows, business
  process flows, reports, JavaScript web resources, plug-in steps and images, plug-in and custom workflow
  activity code, custom actions, and what the platform itself reports as dependent.
- Says for every reference how the field is used (displayed, read, written, used as a trigger or a filter,
  and more) and shows the evidence. References in compiled plug-ins and custom workflow activities are shown
  as decompiled C#, with the statement that touches the field. Decompilation runs on your computer.
- Checks every reference against the selected table, because the same column name can exist on many tables.
  Only references that are verified for the table are counted; the others are listed separately.
- Says whose component a reference belongs to as far as the tool can tell (the organization's, Microsoft's,
  or unknown). Components Microsoft ships are kept out of the way unless you ask for them; a workflow or a
  business rule of your own is not hidden because a class of the platform runs it.
- States its coverage: which search targets were searched completely, partially, not at all, or failed.
- Exports to CSV, JSON, Excel or a self-contained HTML report. Every export states what it holds.

## What to know before relying on it

- No static analysis can prove that a field is unused. Integrations outside the organization and field names
  that are built at run time are not visible to it. An empty result means that nothing was found in what was
  searched; read the coverage of every analysis.
- Results can be incomplete or wrong. Verify them before you change or remove anything.
- The tool was developed and tested for Dynamics 365 Customer Engagement 9.1 on-premises. Dataverse /
  Dynamics 365 online has not been tested.
- Searching plug-in and custom workflow activity code downloads the custom assemblies of the organization once
  per connection. On a large organization an analysis can take several minutes.

## Safety

The tool only reads. It never creates, updates, deletes or publishes anything in the organization it is
connected to. Assemblies are read as data and are never run; scripts are parsed, never executed; nothing is
sent to any service other than the organization you connect to.

## Requirements

XrmToolBox 1.2025.10.74 or later, and .NET Framework 4.8.

## License

Field Dependencies is free to install and use, for personal and commercial work. It is proprietary software:
copyright (c) 2026 Omar Mohamed Ayyad, all rights reserved. The license terms are delivered with the tool
(`LICENSE.txt` in its folder), together with the notices of the third-party components it ships with
(`THIRD-PARTY-NOTICES.txt`), which keep their own licenses.

## Contact

Questions about the tool or its license: open an issue on this page. Do not post data, names or screenshots
of your organization in an issue; issues are public.

Field Dependencies is an independent tool. It is not affiliated with, endorsed by or sponsored by Microsoft or
by the XrmToolBox project. Microsoft, Dynamics 365 and Dataverse are trademarks of the Microsoft group of
companies.
