---
layout: post
title:  "Customizing language strings in Moodle and Totara"
date:   2020-10-10 09:40:29 +1000
categories: software
---

Moodle and Totara Learn support a range of languages in the form of language packs; see the documentation for [Moodle](https://docs.moodle.org/35/en/Language_settings) and [Totara](https://help.totaralearning.com/display/TL12/Site+Languages) respectively. Within a given language pack you can customize the wording and terminology so that the Learning Management System (LMS) reflects your organization's culture and feels more familiar to your learners and other users.

This article collates general advice about modifying language strings where the organization has a requirement to change the standard LMS wording or terminology. It is no substitute for the product documentation cited above.

## Before you begin

There are a few points to keep in mind before opening the site's language pack for editing.

### What and why?

- Document the scope of the planned changes: which page elements and pages are affected? What are you trying to achieve?
- Weigh up the value and impact of the configuration changes versus the maintenance overhead.
- Discourage stakeholders from trivial language customizations, and avoid customizing the language on site administration pages.

### Potential stumbling blocks

- Modifying the language pack may have unintended consequences.
- The string might appear in other places beyond the page you're looking at, and perhaps that change is not desired throughout the site.
- There is a risk of changing the incorrect string id.

### When applying the change

- Document the changes as they are implemented. That way, it's easier to resolve issues, and the configuration can be more readily replicated or adjusted.
- Consider testing language pack changes in a sandbox or staging site before applying the changes to the production (live) site.
- Promote changes to the production site only after thorough testing in staging.

## How to identify a particular language string id

Finding the correct language string id to change can be overwhelming as there are so many, and it can be difficult to tell them apart.

Mercifully, Moodle and Totara Learn both offer an admin utility that shows you, on the page, what each string is called in the language pack.

To use the admin utility:

1. Enable the yes/no toggle **Show origin of languages strings** (`debugstringids`) within the admin settings for the site.
2. Navigate to the page /admin/settings.php?section=debugging within the Moodle or Totara site in question.
3. Toggle the checkbox to ticked (Yes), if not already. Click **Save changes**.

With this feature on, language string components and identifiers are displayed when `?strings=1` or `&strings=1` is appended to the page URL.

1. Access the page containing the word or phrase you wish to change.
2. Examine the page URL in the browser's address bar. Does it include a question mark (?) after `.php` with one or more parameters, or end with `.php` alone, no parameters thereafter? Refer to the table below for examples.
3. Append `&strings=1` or `?strings=1` as appropriate, according to the page's existing URL.
4. Press the **Enter** key to reload the page with this new parameter.
5. The language string ids are now indicated on the page in {curly braces}.

| Original URL for page | Append | Revised URL |
| https://yoursiteaddress/course/view.php?id=45 | &strings=1 | https://yoursiteaddress/course/view.php?id=45&strings=1 |
| https://yoursiteaddress/my/teammembers.php | ?strings=1 | https://yoursiteaddress/my/teammembers.php?strings=1 |