---
layout: post
title:  "SCORM and progress tracking in Totara Learn"
date:   2020-12-02 17:54:29 +1000
categories: elearning
---

When implementing a Learning Management System (LMS), organizations often desire learner-facing dashboards with visual and numerical indicators of course progress.

Totara Learn offers progress bars as a [standard feature](https://help.totaralearning.com/display/TH14/Progress+bar), and it's easy from a web design standpoint to deliver a customized wheel or 'donut'. Progress tracking is straightforward when the course content and assessments are built natively within Totara as course activities.

[SCORM](https://scorm.com/)-based courses are a special case, and they're typically incompatible with Totara's granular progress tracking. It's common for learning designers to bundle everything into one SCORM package, including assessment, so Totara doesn't receive progress updates between commencement and completion.

When customers become aware of this limitation, their next question is how to design and build new SCORM content to accommodate progress reporting in Totara.  One option is to separate the [Shareable Content Objects](https://scorm.com/scorm-explained/scorm-resources/glossary/) (SCOs), create one package per SCO, and upload each as a separate activity in the course. While this solves the progress requirement, it prevents the learning designer from (easily) leveraging learner data as they progress from one SCO to the next.

Unfortunately, there is no short or easy answer to the overall problem. If you would like to read more, I produced a [knowledge base article](https://kathrynmarks.com.au/kb/doku.php?id=kb:totara:course_progress_tracking_in_totara_learn) to consolidate the fruits of my research and consultations with colleagues both in Australia and overseas.