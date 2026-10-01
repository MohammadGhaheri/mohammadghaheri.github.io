---
layout: post
title: "Elm Simple CRM: an open-source CRM built from a real operational need"
description: "How Elm Simple CRM grew out of real use at Mammut Connect, evolved through operational feedback, and became an open-source PHP CRM."
date: 2026-10-01
permalink: /en/articles/elm-simple-crm/
lang: en
alt_url: /fa/articles/elm-simple-crm/
tags:
  - CRM
  - Open Source
  - PHP
  - Product
  - Mammut Connect
---

A lot of software starts with a specification.

A list of features is written, development begins, and eventually a product is delivered that is expected to find its users later.

**Elm Simple CRM took a different path.**

It was built to be used first, and then improved through real usage.

The project started from an operational need at **Mammut Connect**, where customer relationship management meant much more than storing company names, phone numbers and a few notes.

We were dealing with customers, contacts, sales opportunities, meetings, follow-ups, contracts, renewals, support requests and tickets.

The problem was that parts of this information lived in files, some in messages and phone calls, and some simply in people's memory.

That is usually where things begin to break down.

A follow-up gets forgotten.

The status of a sales opportunity becomes unclear.

A contract approaches renewal without anyone noticing.

A customer needs support, but it is not clear who is responsible for responding.

Elm Simple CRM grew out of the need to solve exactly that problem.

## For me, a CRM is more than a customer list

The core of the system is built around a small number of concepts:

**Customer, Contact, Opportunity, Activity, Contract and Ticket**

A customer can have multiple contacts.

Sales opportunities are linked to customers.

Activities and follow-ups are assigned to specific users.

Contracts have start dates, end dates and renewal paths.

And customers can submit and follow support requests through their own portal.

The goal was to make it possible to follow a customer from the first interaction through sales, contract and support inside one coherent structure.

Not to open another spreadsheet, messaging group or notebook for every stage.

## What real usage added to the product

This is the part of the project I find most important.

Many of Elm Simple CRM's capabilities were not designed on day one.

Once the system entered daily use, real problems began to surface.

For example, the sales team did not just need a list of activities. They needed to know **what exactly they should do today**.

That need led to the "My Plan" view.

The support workflow revealed another issue.

It was not enough for a ticket to simply exist.

Everyone on the team needed visibility into the queue, while it still had to be clear **who was actually responsible for handling each ticket**.

So assignment and reassignment became part of the workflow.

Then another question appeared.

If a customer added a new message to a ticket and a colleague opened it only for context, should the "new" state disappear?

In practice, no.

A non-owner viewing the ticket should not make the responsible person believe that there is nothing new to review.

So the new-message logic evolved to reflect actual responsibility: the state is cleared when the responsible person sees it or when someone on the team genuinely responds to the customer.

These details may look small, but to me they are exactly what separates a record-keeping system from a **real operational tool**.

## Ticketing became a serious part of the system

Elm Simple CRM includes a separate customer portal.

Contacts with portal access can log in, create tickets, read team responses and continue the conversation.

Tickets can be assigned and reassigned between team members while keeping clear responsibility.

VIP customers can follow different support behavior, and the system can send SMS notifications.

Email delivery can also be configured, with support for both PHP Mail and SMTP.

Over time, this part of the product moved from being a simple "submit a request" form toward something much closer to a real support workflow.

## Sales, contracts and follow-up in one flow

On the sales side, the CRM does more than store customer information.

You can create opportunities, record value and probability, and calculate weighted opportunity value.

Activities such as calls, meetings and follow-ups can be assigned to users, while dates are shown in the Persian calendar in the user interface.

Contracts can also be recorded, including their end dates for renewal follow-up.

As a result, the CRM gradually became a place where the team could follow a meaningful part of this lifecycle:

**Lead / Customer → Contact → Opportunity → Activity → Contract → Support**

## Why I deliberately kept the system simple

One of the important product decisions was not to build it on top of heavy frameworks.

The technical core of Elm Simple CRM is intentionally straightforward:

- PHP 8+
- MySQL or MariaDB
- PDO
- HTML
- CSS
- Vanilla JavaScript

There is no Laravel dependency.

There is no heavy frontend framework either.

That is not an argument against frameworks.

The goal was different: **the code should remain understandable, installable and modifiable.**

For a team or developer that wants to adapt the CRM to its own workflow, being able to understand the project structure quickly has real value.

## Persian-first does not just mean translating the UI

Elm Simple CRM was designed for a Persian-speaking operational environment from the beginning.

The interface is right-to-left and dates are presented in the Jalali calendar.

In the database, however, dates are stored in standard Gregorian form.

This gives Iranian users a familiar date experience while keeping the underlying data model conventional.

Many display labels and reference options can also be changed from settings, avoiding the need to edit code for every small business-specific adjustment.

## Security has been part of the design from the start

The project is lightweight, but simplicity is not intended to mean ignoring basic security.

The system uses measures including:

- Session-based authentication
- PDO and prepared statements
- `password_hash`
- CSRF tokens
- Escaped output
- Role-based controls
- Protection of internal pages
- Automatic installer lockout after installation

The real database configuration file is also excluded from Git.

## Then I decided to open-source it

Once the system reached a point where it could be useful outside its original environment, I decided to make the source public.

Elm Simple CRM is now available on GitHub as an open-source project under the MIT License:

**[View Elm Simple CRM on GitHub](https://github.com/MohammadGhaheri/Simple-CRM)**

You can inspect the code, clone it, fork it and adapt it to your own processes.

That is the part of open source I find most valuable.

Not every company should follow exactly the same workflow we had.

But if the core of the system is useful, another team can take it and shape it around the way they work.

## How to install Elm Simple CRM

You need an environment with **PHP 8+** and **MySQL or MariaDB**.

Start by cloning the repository:

```bash
git clone https://github.com/MohammadGhaheri/Simple-CRM.git
```

In the recommended setup, the web server document root should point to:

```text
crm/public
```

Then open the installer in your browser:

```text
https://your-domain.com/install.php
```

If the project is placed inside a subdirectory, the address may instead look like:

```text
https://your-domain.com/crm/public/install.php
```

The installer asks for database information, the administrator account and the initial application settings.

You can optionally create sample data so that you can explore the CRM before entering real information.

After installation, an `install.lock` file is created and the installer is disabled.

Full installation details and project structure are documented in the **[project README](https://github.com/MohammadGhaheri/Simple-CRM#readme)**.

## Where do you start after installation?

The everyday flow is intentionally straightforward.

Create a customer.

Add that company's contacts.

If there is an active sales conversation, create an opportunity.

Record calls, meetings and follow-ups as activities.

If the deal becomes a contract, store the contract and its important dates.

And when the customer needs support, they can use the portal to open a ticket.

I wanted the workflow to resemble the natural flow of the work itself rather than forcing users to first learn the internal logic of the software.

## Who is Elm Simple CRM for?

Elm Simple CRM is not intended to replace Salesforce, Microsoft Dynamics or large enterprise CRM platforms.

That is not the goal.

It is more relevant for teams that:

- Want a simple CRM they can control
- Prefer to host the system themselves
- Need a Persian interface and Jalali dates
- Want access to the source code
- Need to customize the CRM around their own processes
- Do not want to start with the complexity of a large enterprise platform

## What I learned from building it

For me, Elm Simple CRM is more than a PHP project.

It is a small example of how a product can take shape.

Many of the good decisions were not made while sitting around a table imagining future features.

They happened when someone genuinely used the system and said:

"Something is missing here."

Or when we discovered that a workflow that looked correct on paper created friction in daily use.

That is why the best description of the project may be the lesson that emerged from building it:

**This system was built for use first, and improved afterward.**

If you want to inspect, install or extend the project:

**[github.com/MohammadGhaheri/Simple-CRM](https://github.com/MohammadGhaheri/Simple-CRM)**
