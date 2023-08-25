---
layout: post
title:  "Moodle Quiz Attempts"
date:   2020-12-07 19:54:29 +1000
categories: elearning
published: false
---

Moodle allows you to limit the number of quiz attempts by each learner. Sometimes you need to give a learner another attempt, perhaps due to technical difficulties or compassionate reasons.

You can delete an existing attempt or manually override the limit to give the learner another go. The second option is better if you wish to preserve the existing attempt data.

## Delete selected attempts

When you invoke **Delete selected attempts** to reset the attempt for a given learner in Moodle 3.8, the following occurs:

- The attempt is deleted from the table `mdl_quiz_attempts`
- The quiz grade is deleted from `mdl_quiz_grades`
- The 'grade grade' rows are retained in `mdl_grade_grades`

## Override the number of attempts for a given user

The **User override** feature allows you to increase the number of attempts for a particular learner, e.g. from 1 to 2.

Existing attempts are not deleted.
