---
layout: post
title:  "Plugins for Moodle LMS and Totara"
date:   2020-10-15 10:39:29 +1000
categories: elearning
published: false
---

This article summarizes what I know about a few plugins for the Learning Management Systems (LMS) Moodle and Totara.

## Summary

| Plugin        | Type              | Moodle<span>.</span>org    | GitHub      |  Author     | Compatibility |
| -----------   | -----------       | -----------   | ----------- | ----------- | -----------   |
| H5P | [Course Activity](https://docs.moodle.org/310/en/Activities) | [mod_hvp](https://moodle.org/plugins/mod_hvp) | [moodle-mod_hvp](https://github.com/h5p/moodle-mod_hvp) | [h5p.org](https://h5p.org) | Moodle and Totara |
| OJT | [Course Activity](https://help.totaralearning.com/display/TH14/Adding+course+content) | N/A | [totara-mod-ojt](https://github.com/catalyst/totara-mod-ojt) | [Catalyst IT](https://github.com/catalyst) | Totara |
| Adminer | Database utility | [local_adminer](https://moodle.org/plugins/local_adminer) | [moodle-local_adminer](https://github.com/grabs/moodle-local_adminer) | [Andreas Grabs](https://github.com/grabs) | Moodle, ?Totara |

## More information

### H5P

The H5P plugin (mod-hvp) allows you to create and add rich, interactive content such as videos, quizzes, collages, and timelines.

The HTML5 Package (H5P) is a free and open-source content collaboration framework based on JavaScript. Its goal is to allow anyone to create, share and reuse interactive HTML5 content.

### OJT

The OJT plugin (totara-mod-ojt) allows you to define, track and sign off learning activities in the workplace. The concept of 'on-the-job training' often leads people to refer to the plugin as OTJ.

This plugin includes:

- The learner interface.
- A separate manager interface.
- Reporting functionality.

OJT supports the [learning while working approach](https://www.google.com/search?q=learning+while+working).

Learn more by checking out these third-party resources:

- [Blog post](https://www.sproutlabs.com.au/blog/learning-while-working-with-totaras-on-the-job-activity/) by Sprout Labs
- [YouTube video](https://www.youtube.com/watch?v=a-GatbCdqWY) posted by Creative Leap

### Adminer

[Adminer](https://www.adminer.org/) is a database management tool. The Adminer plugin (local_adminer) allows you to run a version of Adminer from within a Moodle instance. I haven't tried the plugin with Totara Learn but suspect the two are compatible.
