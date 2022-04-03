---
layout: post
title:  "Moodle and Totara web services"
date:   2020-10-10 10:02:29 +1000
categories: software
---

The elearning platforms Moodle and Totara offer a library of integration functions out of the box as part of the web service API. Totara Learn includes all of the Moodle functions plus a few more developed by Totara.

The documentation built into the LMS is occasionally lacking in information such as required capabilities, and the context or scenario to which the web service applies. This article fills those gaps as I encounter them.

## Moodle and Totara's API documentation

The first port of call is always the LMS's API documentation. This article is designed to supplement that information, not act as a substitute.

### How do I access the documentation?

First you need to ensure the documentation is turned on.

1. In the Moodle or Totara site, navigate to `https://yoursiteaddress/admin/settings.php?section=webserviceprotocols`.
2. Ensure the checkbox is ticked for **Web services documentation**.
3. Navigate to Site administration > Plugins > Web services > API Documentation.

The URL for the documentation resembles `https://yoursiteaddress/admin/webservice/documentation.php`.

You can export the documentation to PDF but be warned: the documentation is so long that some browsers will struggle to do so. I personally found that the export worked from a PC but not a Mac, and the in-platform documentation is easier to use.

### What does the documentation describe? 

- The web service functions available in that system, and for each:
- the accepted arguments
- the accepted argument parameters (where applicable)
- the structure of the request, and
- the response(s) provided by the LMS to the external system. This includes success/fail messages and warnings.

## Unlisted capabilities and pre-requisites

The **Add functions to the service** page in the LMS for a given external service allows you to add or remove functions for that service. The page indicates which functions have been added (enabled), and for each lists the description and the required [capabilities](https://docs.moodle.org/38/en/Roles_and_permissions).

The URL for this page resembles `https://yoursiteaddress/admin/webservice/service_functions.php?id=n` where `n` is the id number for the service.

I've found numerous examples where the required capabilities are not cited on this page. In other cases, the capability is documented but there is some other requirement or caveat.

| Web service function | Moodle mobile app only | Undocumented capability | ws user must be enrolled to Course | Other notes |
| --- | --- | --- | --- | --- |
| `core_calendar_create_calendar_events|core_calendar_create_calendar_events` | Yes | – | – | – |
| `core_calendar_delete_calendar_events` | Yes | – | – | – |
| `core_calendar_get_calendar_events` | Yes | – | – | – |
| `core_completion_get_activities_completion_status` | No | https://docs.moodle.org/38/en/Capabilities/report/progress:view report/progress:view | Yes | – |
| `core_completion_get_course_completion_status`  | No | – | Yes | – |
| `core_user_get_users|core_user_get_users` | No | https://docs.moodle.org/38/en/Capabilities/moodle/user:viewalldetails moodle/user:viewalldetails to query by username or idnumber | – | – |
| `core_user_get_users_by_field|core_user_get_users_by_field` | No | https://docs.moodle.org/38/en/Capabilities/moodle/user:viewalldetails moodle/user:viewalldetails to query by username or idnumber | – | – |
| `core_user_update_users|core_user_update_users` | No | – | – | Cannot be used to update site admin accounts |
| `gradereport_overview_get_course_grades` | No | – | – | – | 
| `gradereport_user_get_grade_items` | No | – | – | Yes |
| `gradereport_user_get_grades_table|gradereport_user_get_grades_table` | No | No | Yes | Returns the data in a form intended for HTML table output. See `gradereport_user_get_grade_items`. |
| `mod_quiz_get_quizzes_by_courses` | No | – | Yes | Returns generic (config) information about the Course's quizzes—not learner data. |
| `mod_quiz_get_user_attempts` | No | https://docs.moodle.org/38/en/Capabilities/mod/quiz:viewreports mod/quiz:viewreports | Yes | – |
| `mod_quiz_get_user_best_grade` | No | – | Yes | – |
