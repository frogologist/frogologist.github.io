---
layout: post
title:  "Moodle and Totara web services"
date:   2020-10-10 10:02:29 +1000
categories: software
---

Moodle and Totara are Learning Management Systems (LMS). They offer a library of integration functions as part of the web service API. Totara Learn includes all of the Moodle functions, plus a few more developed by Totara.

This article fills some gaps in the built-in documentation, including explanatory context, supported use cases and required permissions (capabilities).

## Moodle and Totara’s API documentation

The first port of call is always the LMS’s API documentation. This article supplements that information.

### How do I access the documentation?

First, you must turn on the documentation.

1. In the Moodle or Totara site, navigate to https://`yoursiteaddress`/admin/settings.php?section=webserviceprotocols`.
2. Find the checkbox **Web services documentation** and toggle it on (so it’s ticked). Save changes.
3. Navigate to Site administration > Plugins > Web services > API Documentation.

The URL for the documentation resembles https://`yoursiteaddress`/admin/webservice/documentation.php.

You can export the documentation to PDF, but the in-platform documentation is more convenient. PDF export worked for me from a PC but not a Mac, perhaps due to the size of the document.

### What does the documentation describe? 

- The web service functions available in that system, and for each:
- the accepted arguments
- the accepted argument parameters (where applicable)
- the structure of the request, and
- the response(s) provided by the LMS to the external system, including success/fail messages and warnings.

## Unlisted permission requirements and pre-requisites

The **Add functions to the service** page in the LMS for a given external service allows you to add or remove functions for that service. The page indicates which functions have been added (activated), along with their descriptions and required [permissions](https://docs.moodle.org/38/en/Roles_and_permissions).

The URL for this page resembles https://`yoursiteaddress`/admin/webservice/service_functions.php?id=`n` where `n` is the id number for the service.

The following table outlines some undocumented requirements, including required permissions and caveats.

Please excuse the width of the table. Links in the first column take you to dedicated sections further down this page.

| Web service function | Moodle mobile app only | Undocumented permission | ws user must be enrolled to Course | Other notes |
| --- | --- | --- | --- | --- |
| [core_calendar_create_calendar_events](#core_calendar_create_calendar_events) | Yes | – | – | – |
| [core_calendar_delete_calendar_event](#core_calendar_create_calendar_events) | Yes | – | – | – |
| [core_calendar_get_calendar_events](#core_calendar_create_calendar_events) | Yes | – | – | – |
| core_completion_get_activities_completion_status | No | [report/progress:view](https://docs.moodle.org/38/en/Capabilities/report/progress:view) | Yes | – |
| core_completion_get_course_completion_status  | No | – | Yes | – |
| [core_user_get_users](#core_user_get_users-and-core_user_get_users_by_field) | No | [moodle/user:viewalldetails](https://docs.moodle.org/38/en/Capabilities/moodle/user:viewalldetails) to query by `username` or `idnumber` | – | – |
| [core_user_get_users_by_field](#core_user_get_users-and-core_user_get_users_by_field) | No | [moodle/user:viewalldetails](https://docs.moodle.org/38/en/Capabilities/moodle/user:viewalldetails) to query by username or idnumber | – | – |
| [core_user_update_users](#core_user_update_users) | No | – | – | Cannot be used to update site admin accounts |
| gradereport_overview_get_course_grades | No | – | – | – | 
| gradereport_user_get_grade_items | No | – | – | Yes |
| [gradereport_user_get_grades_table](#gradereport_user_get_grades_table) | No | No | Yes | Returns the data in a form intended for HTML table output. See gradereport_user_get_grade_items. |
| mod_quiz_get_quizzes_by_courses | No | – | Yes | Returns generic (config) information about the Course’s quizzes—not learner data. |
| mod_quiz_get_user_attempts | No | https://docs.moodle.org/38/en/Capabilities/mod/quiz:viewreports mod/quiz:viewreports | Yes | – |
| mod_quiz_get_user_best_grade | No | – | Yes | – |

### core_calendar_create_calendar_events

This Moodle web service function is for the Moodle mobile app (moodle_mobile_app).

It creates a Calendar Event for the user logged in via the Moodle mobile app, which explains why the arguments do not include `userid`.

Unfortunately, you cannot call this function from an external system.

The accompanying web services to delete (core_calendar_delete_calendar_events) and get (core_calendar_get_calendar_events) the Calendar Events are likewise specific to mobile. 

For more information, refer to [Moodle’s web service documentation](https://docs.moodle.org/dev/Web_service_API_function).

### core_user_get_users and core_user_get_users_by_field

These functions allow the external system to query the LMS about users based on one or more criteria, including the Moodle or Totara user id, email address, username and external ID number.

The capability [moodle/user:viewalldetails](https://docs.moodle.org/38/en/Capabilities/moodle/user:viewalldetails) is required to query the LMS by `username` or `idnumber` but not by `email` or `id`. It’s not indicated in the documentation but comes up in bug reports such as [MDL-42639](https://tracker.moodle.org/browse/MDL-42639) and [MDL-50639](https://tracker.moodle.org/browse/MDL-50639).

The LMS does not return a permissions error when the web service user lacks this capability. I should report this issue via [Moodle Tracker](https://tracker.moodle.org) if nobody has beaten me to it.

#### core_user_get_users

Criteria that work without moodle/user:viewalldetails:

- criteria[0][key]=email
- criteria[0][key]=id

Criteria that also need moodle/user:viewalldetails to work, otherwise you get an empty array:

- criteria[0][key]=idnumber
- criteria[0][key]=username

#### core_user_get_users_by_field

This function allows the external system to query the LMS about users by field, including the Moodle or Totara user id, email address, username and external ID number.

The capability [moodle/user:viewalldetails](https://docs.moodle.org/38/en/Capabilities/moodle/user:viewalldetails) is required to query the LMS by `username` or `idnumber` but not by `email` or `id`. It’s not indicated in the documentation but comes up in bug reports such as [MDL-42639](https://tracker.moodle.org/browse/MDL-42639) and [MDL-50639](https://tracker.moodle.org/browse/MDL-50639).

The LMS does not return a permissions error when the web service user lacks this capability. I have pondered whether to report this issue via [Moodle Tracker](https://tracker.moodle.org/secure/Dashboard.jspa).

Fields that work without moodle/user:viewalldetails are:

    field=id
    field=email

Fields that also need moodle/user:viewalldetails to work, otherwise you get an empty array:

    field=idnumber
    field=username 

### core_user_update_users

This Moodle function requires capability [moodle/user:update](https://docs.moodle.org/38/en/Capabilities/moodle/user:update), as documented.
 
Moodle’s response is literally `null` regardless of success or failure. If you supply an invalid parameter, you receive `invalid_parameter_exception`.

This function **cannot** be used to update site administrator accounts. Moodle performs the following check:

```
if ($existinguser->id != $USER->id and is_siteadmin($existinguser) and !is_siteadmin($USER))
{ continue; } 
```

You can review the Site Admin list via /admin/roles/admins.php.

### gradereport_user_get_grades_table

This Moodle web service function requires the capability [gradereport/user:view](https://docs.moodle.org/38/en/Capabilities/gradereport/user:view), as documented. You’ll have to enrol the web service user on the Course for it to work.

The function returns the data in a form intended for HTML table output. gradereport_user_get_grade_items returns the same data more concisely.
