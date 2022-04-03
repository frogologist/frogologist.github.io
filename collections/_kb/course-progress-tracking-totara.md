---
layout: post
title:  "Course progress tracking in Totara Learn"
date:   2020-10-10 11:49:29 +1000
categories: software
---

Organisations often desire learner dashboards with visual and numerical indicators of course progress in the Learning Management System (LMS).

It's easy to deliver the progress bars or wheels from a web design standpoint, but you may not have access to the required data.

Progress data must be available to Totara in order to represent it graphically and numerically within the app.

## What progress tracking is supported?

Totara provides percentage-based progress bars as a standard feature based on the [course completion settings](https://help.totaralearning.com/display/TH13/Course+completions). This functionality relies on the Course being made up of multiple Activities and assumes the Activities are of equal value, in terms of contribution towards completion.

The calculation method is described in Totara’s [documentation](https://help.totaralearning.com/display/TH13/Progress+bar) if you're interested.

You see this kind of progress tracking when undertaking Totara Academy courses as a learner.

Note that Totara does not support the display of time-based estimates. Totara cannot calculate or display the minutes remaining for a Course; you'll need a developer to build this for you.

## How should new SCORM content be built to harness Totara's progress tracking?

This recommendation applies to building [Sharable Content Object Reference Model](https://scorm.com/) (SCORM) content where granular progress tracking is required in Totara Learn. You can learn more about SCORM by checking out their [golf examples](https://scorm.com/scorm-explained/technical-scorm/golf-examples/)

- Build SCORM-based learning content for a given Course as a series of Standalone Shareable Content objects (SCOs), each packaged separately, with one topic or section per package.
- Upload each package to the Course as a separate SCORM Activity. See Totara's documentation for a [step-by-step guide](https://help.totaralearning.com/display/TH13/SCORM).
- Totara applies its standard progress calculation. Example: if you create a Course with 6 SCORM Activities, each Activity contributes 16.7% towards course completion (100% ÷ 6).

The topics-as-SCOs approach described here is considered best practice by some LMS vendors.

## How is existing SCORM content typically constructed?

SCORM content is often constructed as one SCO bundled into one SCORM package.

Content created in this way must be uploaded to a single SCORM Activity in Totara Learn. Where a given Course has only one such Activity, Totara's Activity-based calculations would see the progress jump from 0% to 100% with no intermediate value — even when the learner completed the SCORM content across multiple sittings.

## Can Totara Learn display granular progress data from single SCORM packages?

The short answer is no. Read on for more information.

### What are the limiting factors? What would we need to achieve this?

There are multiple factors to consider when attempting to display granular progress data from one SCORM package. They include the functionality and capabilities of:

- the LMS
- the Shareable Content Object Reference Model (SCORM) version
- content authoring tools such as Adapt and Articulate Rise

#### Totara Learn

Totara Learn supports SCORM 1.2. It does not support more recent iterations of the reference model, including SCORM 2004.

In terms of progress data, Totara is at the mercy of the information made available by the SCORM package.

#### SCORM 1.2

[SCORM 1.2](https://scorm.com/scorm-explained/technical-scorm/run-time/run-time-reference/) does not provide any explicit mechanism to indicate (to the LMS) the learner’s progress as a percentage value, nor minutes remaining.

When learning content is packaged as one SCO, the Learning Management System (LMS) such as Totara Learn receives the status of the SCO as a whole — it does not receive detailed information about the content or progress inside the SCO. At most, the LMS is aware whether a SCORM for a given learner is not started, in progress, or complete.

#### What about SCORM Objectives?

SCORM’s data model (CMI) includes learning objectives: `cmi.objectives`. It’s possible to set up a SCORM package so that each topic tracks to an objective.

Totara could, theoretically, be made to calculate progress based on the number of objectives completed and the total number in the SCORM. There are a few reasons why it’s not a compelling solution:

- `cmi.objectives` is not required for SCORM 1.2 compliance, so not all Learning Management Systems support it. You may prefer to create SCORM content that is well-supported, in case you decide to change your LMS software. On a side note, `cmi.objectives` is mandatory for SCORM 2004 compliance.
- Totara supports `cmi.objectives` and offers an Objectives Report, but the report is only available to system administrators, not learners.
- The field `cmi.objectives._count` holds the current number of objectives, not the total. This value represents the number of objectives recorded since the learner launched the SCORM, not how many to expect. The SCORM should declare to the LMS how many objectives there are at first launch, but it's not a requirement. Based on my experience, most packages do not provide this information.
- I am not aware of any SCORM authoring tools that support `cmi.objectives` out of the box.

#### Content authoring tools

While both Adapt and Articulate Rise both support the fundamental SCORM interactions, the two products are known to behave differently. A solution that might work for Adapt may not be supported by Articulate Rise, and vice versa. Other content authoring tools likewise would not necessarily support an approach utilised by Adapt or Articulate Rise.

#### What about xAPI?

In short, there is no progress tracking solution available via xAPI functionality.

You could design xAPI statements to collect more detailed tracking information from SCORM packages and submit it to an interfaced Learning Record Store (LRS).

Converting SCORM data models into xAPI is not recommended, though there are libraries to do so. SCORM Cloud might offer such libraries.

The general consensus is that SCORM should continue to handle the course’s session state and bookmarking, including tracking individual SCO completion. xAPI could be implemented to capture cross-SCO insights and support gamification features such as leaderboards, levels, triggers and badges within the LMS. Again, this is hypothetical functionality.