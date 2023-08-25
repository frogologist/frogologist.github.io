---
layout: post
title:  "StopDialog requests in AGS 3.1"
slug: stopdialog-requests-ags
date:   2010-01-18 10:39:29 +1000
categories: programming
published: false
---

I'm helping a friend to make a LucasArts-style adventure game with [Adventure Game Studio](https://www.adventuregamestudio.co.uk/) (AGS). My friend is responsible for the design, art, and media; I'm the coder behind the scenes.

AGS 3.1 is straightforward to use, though I couldn't find a documented explanation for a particular error message:

> Error: NewRoom: two NewRoom/RunDialog/StopDialog requests within dialog.

I encountered this error while trying to code multiple commands in the `dialog_request` function.

The culprit was `StopDialog()` placed inside the first `if` clause, ahead of `ChangeRoom` statements.  `StopDialog()` is not required and trips the error.

The following `Dialog:dName1` code follows the relevant return dialog:

```
run-script 1
stop
```

The following `Dialog:dName2` code follows the relevant return dialog:

```
run-script 2
stop
```

The contents of `GlobalScript.asc`:

```
function dialog_request(int xvalue)
{
  if (xvalue == 1) {
    cBob.Walk(5, 287, eBlock, eWalkableAreas);
    cBob.ChangeRoom(2, 120, 300);
    cBen.ChangeRoom(0);
    cCorpse.ChangeRoom(2);
    cCorpse.Baseline = 120;
    // This replaces Ben with his dead body.
    }

  if (xvalue == 2) {
    cGuy.ChangeRoom(3);
  }

  else{}
}
```

Multiple instances of `run-script` can exist, but be wary of ill-placed `StopDialog()` commands.
