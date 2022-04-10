---
layout: post
title:  "Totara's HR Import"
date:   2020-10-21 10:39:29 +1000
categories: elearning
---

This article collates various notes about HR Import and its usage. It is not substitute for Totara's [product documentation](https://help.totaralearning.com/display/TL12/HR+Import).

## Multiple HR Import data sources

HR Import can accommodate multiple data sources, but from an automation perspective, it's really designed to accept only one.

In general, I recommend collating the HR Import data into one source for consumption by Totara Learn.

Consider the following before implementing multiple HR Import feeds:

- Set **Source contains all records** to `no`.
- Import files would have to contain the column `deleted`, with `1` or `0` specified per user (row) as appropriate.
- The site administrator could set up a scheduled import from the main data source and perform manual uploads from the other source. Switch the settings to `upload` and back again with each manual upload.
- It's possible but difficult to schedule consumption of HR Import files from multiple sources. It would require careful configuration of the import schedule so that Totara uploads the file from the first source, allows it to import, then uploads the file from the second source.

## Job Assignments persist after user suspension

When a staff member leaves the organization the site administrator should consider whether to deactivate the user's Job Assignment(s) in addition to suspending their user account.

Suspension of a user account in Totara does not automatically remove or revoke the Job Assignment(s).

Former employees with lingering Job Assignments continue to appear in their manager's reports unless the reports are specifically returning only active user accounts.