# Contribution Guidelines

This document outlines what you need to know before **[creating tickets](#issues-tickets-however-you-may-call-them)**
or **[creating pull requests](#pull-requests)**.

## Contents

  * [Issues, Tickets, however you may call them](#issues-tickets-however-you-may-call-them)
  * [How to file a bug report](#how-to-file-a-bug-report)
    * [What should I do before submitting a bug report?](#what-should-i-do-before-submitting-a-bug-report)
    * [What should I include in a bug report?](#what-should-i-include-in-a-bug-report)
    * [Where can I find which version and branch I'm on?](#where-can-i-find-which-version-and-branch-im-on)
    * [Where can I find those log files you keep talking about?](#where-can-i-find-those-log-files-you-keep-talking-about)
    * [Where can I find my browser's error console?](#where-can-i-find-my-browsers-error-console)
  * [Setting up a development environment](#setting-up-a-development-environment)
  * [Pull requests](#pull-requests)
  * [What do the branches mean?](#what-do-the-branches-mean)
  * [How OctoPrint is versioned](#how-octoprint-is-versioned)
  * [History](#history)
  * [Footnotes](#footnotes)

## Issues, Tickets, however you may call them

Please read the following instructions fully and follow them. You can
help the project tremendously this way: not only do you help the maintainers
to **address problems in a timely manner** but also keep it possible for them
to **fix bugs, add new and improve on existing functionality** instead of doing
nothing but ticket management.

![Ticket flow chart](https://i.imgur.com/cw19qHX.png)

- **[Read the FAQ](https://faq.octoprint.org)**
- If you want to report a **bug**, [read "How to file a bug report" below](#how-to-file-a-bug-report)
  and *[use the provided template](#what-should-i-include-in-a-ticket)*.
  You do not need to do anything else with your ticket.
- If you want to post a **feature request** or a **documentation request**, add `[Request]`
  to your issue's title (e.g. `[Request] Awesome new feature`). A question on how to run/change/setup
  something is **not** what qualifies as a request here, use the
  [community forum at community.octoprint.org](https://community.octoprint.org) for
  such support issues.
- If you are a **developer** that wants to brainstorm a pull request or possible
  changes to the plugin system, please get in touch on the 
  [community forum at community.octoprint.org](https://community.octoprint.org/c/development).
- If you need **support**, have a **question** or some **other reason** that
  doesn't fit any of the above categories, the issue tracker is not the right place.
  Consult the [community forum at community.octoprint.org](https://community.octoprint.org/c/support) instead.

No matter what kind of ticket you create, never mix two or more "ticket reasons"
into one ticket: One ticket per bug, request, brainstorming thread please.

> 👉 **Note**
> 
> A bot is in place that monitors new tickets, automatically
> categorizes them and checks new bug reports for usage of the provided template.
> That bot will only bother you if you open a ticket that appears to be a bug (no
> `[Request]` in the title) without the complete template, and it
> will do that only to ensure that all information needed to solve the issue is
> available for the maintainers to directly start tackling that problem.

## How to file a bug report

If you encounter an issue with OctoPrint, you are welcome to
[submit a bug report](https://github.com/foosel/OctoPrint/issues/new).

Before you do that for the first time though please take a moment to read the
following section *completely* and also follow the instructions in the
"new issue" form. Thank you! :)

### What should I do before submitting a bug report?

1. **Make sure you are at the right location**. This is the bug tracker
   of the official version of OctoPrint, which is the 3D print server and
   corresponding web interface itself.
   
   **OctoPrint doesn't manage your network connection or your webcam nor
   can it fix your printer not getting detected as a serial interface** - 
   if you have any kinds of problems with that, get in touch on the 
   [community forum](https://community.octoprint.org).
   
   **This is not the bug tracker of OctoPi**, which is the preconfigured
   Raspberry Pi image including OctoPrint among other things - that one can be found
   [here](https://github.com/guysoft/OctoPi). If you have any kind of specific
   issue with how the OctoPi system is setup, go there please.

   **This is also not the bug tracker of any OctoPrint Plugins you
   might have installed**. Report any issues with those in their corresponding
   bug tracker (probably linked to from the plugin's homepage).

   Finally, **this is also not the right bug tracker if you are running a
   forked version of OctoPrint**. Seek help for such unofficial versions from
   the people maintaining them instead.

2. Please make sure to **test out the current version** of OctoPrint to see
   whether the problem you are encountering still exists, and **test without
   any third-party plugins enabled** to make sure it's not a misbehaving
   plugin causing the issue at hand. For that please restart OctoPrint in
   **safe mode**, either by selecting "Restart OctoPrint in safe mode" from
   the "System" menu, or by starting OctoPrint from the command line with
   `octoprint serve --safe`. Then try to reproduce your issue. Find out
   more about safe mode in the [docs](http://docs.octoprint.org/en/master/features/safemode.html).

   You might also want to try the current development version of OctoPrint
   (if you aren't already). Refer to the [FAQ](https://faq.octoprint.org)
   for information on how to do this.

3. The problem still exists? Then please **look through the
   [existing tickets](https://github.com/foosel/OctoPrint/issues?state=open)
   (use the [search](https://github.com/foosel/OctoPrint/search?q=&ref=cmdform&type=Issues))**
   to check if there already exists a report of the issue you are encountering.
   Sorting through duplicates of the same issue sometimes causes more work than
   fixing it. Take the time to filter through possible duplicates and be really
   sure that your problem definitely is a new one. Try more than one search query
   (e.g. do not only search for "timelapse" if you happen to run into an issue
   with your webcam, also search for "recording" etc). Do not only read the subject lines
   of tickets that look like they might be related, but also read the ticket itself!

   **Very important:** Please make absolutely sure that if you find a bug that looks like
   it is the same as your's, it actually behaves the same as your's. E.g. if someone gives steps
   to reproduce his bug that looks like your's, reproduce the bug like that if possible,
   and only add a "me too" if you actually can reproduce the same
   issue. Also **provide all information** as [described below](#what-should-i-include-in-a-bug-report)
   and whatever was additionally requested over the course of the ticket
   even if you "only" add to an existing ticket. The more information available regarding a bug, the higher
   the chances of reproducing and solving it. But "me too" on an actually unrelated ticket
   makes it more difficult due to on top of having to figure out the original problem
   there's now also a [red herring](https://en.wikipedia.org/wiki/Red_herring) interfering - so please be
   very diligent here!
   
If in doubt about any of the above - get in touch on the [community forum](https://community.octoprint.org)
instead of opening a ticket here. If you are actually running into a bug, we'll figure it out together 
there.
   
### What should I include in a bug report?

First of all make sure your use **a descriptive title**. "It doesn't work"
and similar unspecific complaints are NOT descriptive titles.

**Always use the following template, even if only adding a "me too" to an 
existing ticket**:

```
<!--
READ THE FOLLOWING FIRST:

If not already done, please read the the Contribution Guidelines that
are linked to the right under "Helpful resources" > "Contributing".

Also read the FAQ: https://faq.octoprint.org

This is a bug and feature tracker, please only use it to report bugs
or request features within OctoPrint (not OctoPi, not any OctoPrint
plugins and not unofficial OctoPrint versions).

Do not seek support here ("I need help with ...", "I have a
question ..."), that belongs on the community forum at 
community.octoprint.org, NOT here.

Mark requests with a "[Request]" prefix in the title please. For bug
reports fully fill out the bug reporting template (if you don't know
where to find some information - it's all described in the Contribution
Guidelines linked up there in the big yellow box).

When reporting a bug do NOT delete ANY lines from the template.

Make sure any bug you want to report is still present with the CURRENT
OctoPrint version and that it does not vanish when you start OctoPrint
in safe mode - how to do that is also explained in the Contribution
Guidelines linked up there in the big yellow box.

Thank you!
-->

#### What were you doing?

<!-- 
Please be as specific as possible here. The maintainers will need to
reproduce your issue in order to fix it and that is not possible if they
don't know what you did to get it to happen in the first place.

Ideally provide exact steps to follow in order to reproduce your problem:
-->

1. ...
2. ...
3. ...

<!--
If you encountered a problem with specific files of any sorts, make sure
to also include a link to a file with which to reproduce the problem.
-->

#### What did you expect to happen?

#### What happened instead?

#### Did the same happen when running OctoPrint in safe mode?

<!-- 
Test if you can reproduce your problem in safe mode. You can find information
on how to enable safe mode in the Contribution Guidelines.

If you can't reproduce in safe mode, this is a bug with one of your
installed third party plugins. Don't open a ticket here!

If you can't test this in safe mode, state why.
-->

#### Version of OctoPrint

<!--
Can be found in the lower left corner of the web interface. ALWAYS INCLUDE.
-->

#### Operating System running OctoPrint

<!--
OctoPi, Linux, Windows, MacOS, something else? With version please.
OctoPi's version can be found in /etc/octopi_version or in the lower left
corner of the web interface.
-->

#### Printer model & used firmware incl. version

<!--
If applicable, always include if unsure.
-->

#### Browser and version of browser, operating system running browser

<!--
If applicable, always include if unsure.
-->

#### Link to octoprint.log

<!--
On gist.github.com or pastebin.com. ALWAYS INCLUDE and never truncate.

The Contribution Guidelines tell you where to find that.
-->

#### Link to contents of terminal tab or serial.log

<!--
On gist.github.com or pastebin.com. If applicable, always include if unsure or
reporting communication issues. Never truncate.

serial.log is usually not written due to performance reasons and must be
enabled explicitly. Provide at the very least the FULL contents of your
terminal tab at the time of the bug occurrence, even if you do not have
a serial.log (which the Contribution Guidelines tell you where to find).
-->

#### Link to contents of Javascript console in the browser

<!--
On gist.github.com or pastebin.com or alternatively a screenshot. If applicable -
always include if unsure or reporting UI issues.

The Contribution Guidelines tell you where to find that.
-->

#### Screenshot(s)/video(s) showing the problem:

<!--
If applicable. Always include if unsure or reporting UI issues.
-->

I have read the FAQ.
```

Copy-paste this template **completely** (or use the version that gets pre-filled
into the "new issue" form). Do not skip any lines or the bot *will* complain! Provide
all requested information or your ticket will be closed.

### Where can I find which version and branch I'm on?

Please refer to [this FAQ entry](https://community.octoprint.org/t/how-can-i-find-out-the-version-of-octoprint-or-octopi-i-am-running/204/1).

### Where can I find those log files you keep talking about?

Please refer to [this FAQ entry](https://community.octoprint.org/t/where-can-i-find-octoprints-and-octopis-log-files/299/1).

### Where can I find my browser's error console?

See [How to open the Javascript Console in different browsers](https://webmasters.stackexchange.com/questions/8525/how-to-open-the-javascript-console-in-different-browsers)

## Setting up a development environment

See [the corresponding chapter in the documentation](http://docs.octoprint.org/en/master/development/index.html#setting-up-a-development-environment).
This also includes information on how to run the test suite and how to build 
the documentation.

## Pull requests

1. If you want to add a new feature to OctoPrint, **please always first
   consider if it wouldn't be better suited for a plugin.** As a general rule
   of thumb, any feature that is only of interest to a small sub group should
   be moved into a plugin. If the current plugin system doesn't allow you to
   implement your feature as a plugin, create a "Brainstorming" ticket to get
   the discussion going on how best to solve *this* in OctoPrint's plugin
   system - maybe that's the actual PR you have been waiting for to contribute :)
2. If you plan to make **any large or otherwise disruptive changes to the
   code or appearance, please get in touch on the 
   [forums](https://community.octoprint.org/c/development)** first so
   that we can determine if it's a good time for your specific pull
   request. It might be that we're currently in the process of making
   heavy changes to the code locations you'd target as well, or your
   approach doesn't fit the general "project vision", and that would
   just cause unnecessary work and frustration for everyone or
   possibly get the PR rejected.
3. Create your pull request **from a custom branch** on your end (e.g.
   `dev/myNewFeature`)[1].
4. Create your pull request **only against the `maintenance` or `devel` branch**:
     * if it's a bug fix for a bug in the current stable version, an improvement of existing functionality or a 
       *small* new feature (e.g. a new hook, a new config flag, ...): `maintenance` branch
     * otherwise: `devel` branch
5. Create **one pull request per feature/bug fix**.
6. Make sure there are **only relevant changes** included in your PR. No
   changes to unrelated files, no additional files that don't belong (e.g.
   commits of your full virtual environment). Make sure your PR consists
   **ideally of only one commit** (use git's rebase and squash functionality).
7. Make sure you **follow the current coding style**. This means:
     * Tabs instead of spaces in the Python files[2]
     * Spaces instead of tabs in the JavaScript sources
     * English language (code, variables, comments, ...)
     * Comments where necessary: Tell *why* the code does something like it does
       it, structure your code
     * Following the general architecture
     * If your PR needs to make changes to the Stylesheets, change the
       ``.less`` files from which the CSS is compiled.
     * Make sure you do not add dead code (e.g. commented out left-overs
       from experiments).
8. Ensure your changes **pass the existing unit tests**. PRs that break
   those cannot be accepted. You can run the unit tests locally (after
   [initial development environment setup with "develop" dependencies](http://docs.octoprint.org/en/master/development/index.html#setting-up-a-development-environment)) 
   by running
   
   ```
   nosetests --with-doctest
   ```
   
   in the OctoPrint checkout folder. A [travis build](https://travis-ci.org/foosel/OctoPrint) 
   is also setup so that if the tests should fail, your PR will be marked 
   accordingly.
9. **Test your changes thoroughly**. That also means testing with usage
   scenarios you don't normally use, e.g. if you only use access control, test
   without and vice versa. If you only test with your printer, test with the
   virtual printer and vice versa. State in your pull request how you tested
   your changes. Ideally **add unit tests** - OctoPrint severely lacks in that
   department, but we are trying to change that, so any new code already covered
   with a test suite helps a lot!
10. In your pull request's description, **state what your pull request does**,
    as in, what feature does it implement, what bug does it fix. The more
    thoroughly you explain your intent behind the PR here, the higher the
    chances it will get merged fast. There is a template provided below
    that can help you here.
11. Don't forget to **add yourself to the [AUTHORS](./AUTHORS.md)
    file** :)

Template to use for Pull Request descriptions:

```
#### What does this PR do and why is it necessary?

#### How was it tested? How can it be tested by the reviewer?

#### Any background context you want to provide?

#### What are the relevant tickets if any?

#### Screenshots (if appropriate)

#### Further notes
```

## What do the branches mean?

There are three main branches in OctoPrint:

  * `master`: The master branch always contains the current stable release. It
    is *only* updated on new releases. Will have a version number following
    the scheme `<x>.<y>.<z>` (e.g. `1.2.9`) or - if it's absolutely necessary to
    add a commit after release to this branch - `<x>.<y>.<z>.post<commits since x.y.z>`
    (e.g. `1.2.9.post1`).
  * `maintenance`: Improvements and fixes of the current release that make up
    the next release go here. More or less continuously updated. You can consider
    this a preview of the next release version. It should be very stable at all
    times. Anything you spot in here helps tremendously with getting a rock solid
    next stable release, so if you want to help out development, running the
    `maintenance` branch and reporting back anything you find is a very good way
    to do that. Will usually have a version number following the scheme
    `<x>.<y>.<z+1>.dev<commits since increase of z>` for an OctoPrint version of `<x>.<y>.<z>`
    (e.g. `1.2.10.dev12`).
  * `devel`: Ongoing development of new features that will go into the next bigger
    release (MINOR version number increases) will happen on this branch. Usually
    kept stable, sometimes stuff can break though or lose backwards compatibility
    temporarily. Can be considered the "bleeding edge". All PRs should target
    *this* branch. Important improvements and fixes from PRs here are backported to
    `maintenance` as needed. Will usually have a version number following the
    scheme `<x>.<y+1>.0.dev<commits since increase of y>` for a current OctoPrint version
    of `<x>.<y>.<z>` (e.g. `1.3.0.dev123`).
  * `rc/maintenance`: This branch is reserved for future releases that have graduated from
    the `maintenance` branch and are now being pushed on the "Maintenance"
    pre release channel for further testing. Version number follows the scheme
    `<x>.<y>.<z>rc<n>` (e.g. `1.2.9rc1`).
  * `staging/maintenance`: Any preparation for potential follow-up RCs takes place here.
    Version number follows the scheme `<x>.<y>.<z>rc<n+1>.dev<commits since increase of n>` (e.g.
    `1.2.9rc1.dev3`) for a current Maintenance RC of `<x>.<y>.<z>rc<n>`.
  * `rc/devel`: This branch is reserved for future releases that have graduated from
    the `devel` branch and are now being pushed on the "Devel" pre release channel
    for further testing. Version number follows the scheme `<x>.<y+1>.0rc<n>` (e.g. `1.3.0rc1`)
    for a current stable OctoPrint version of `<x>.<y>.<z>`.
  * `staging/devel`: Any preparation for potential follow-up Devel RCs takes place
    here. Version number follows the scheme `<x>.<y>.0rc<n+1>.dev<commits since increase of n>` (e.g.
    `1.3.0rc1.dev12`) for a current Devel RC of `<x>.<y>.0rc<n>`.

Additionally, from time to time you might see other branches pop up in the repository.
Those usually have one of the following prefixes:

  * `fix/...`: Fixes under development that are to be merged into the `maintenance`
    and `devel` branches.
  * `improve/...`: Improvements under development that are to be merged into the
    `maintenance` and `devel` branches.
  * `dev/...` or `feature/...`: New functionality under development that is to be merged
    into the `devel` branch.

There is also the `gh-pages` branch, which holds OctoPrint's web page, and a few
older development branches that are slowly being migrated or deleted.

## How OctoPrint is versioned

OctoPrint follows the [semantic versioning scheme](http://semver.org/) of **MAJOR.MINOR.PATCH**.

The **PATCH** version number is the one increasing most often due to OctoPrint's maintenance releases.
Releases that only change the patch number indicate that they contain bug fixes and small improvements
of existing functionality. Example: 1.2.8 to 1.2.9.

The **MINOR** version number increases with releases that add a lot of new functionality and
large features. Example: 1.2.x to 1.3.0.

Finally, the **MAJOR** version number increases if there are breaking API changes that concern any of the
documented interfaces (REST API, plugin interfaces, ...). So far this hasn't happened. Example: 1.x.y to 2.0.0.

OctoPrint's version numbers are automatically generated using [versioneer](https://github.com/warner/python-versioneer)
and depend on the selected git branch, nearest git tag and commits. The generated version number
should always be [PEP440](https://www.python.org/dev/peps/pep-0440/) compatible. Unless a git tag
is used for version number determination, the version number will also contain the git hash within
the local version identifier to allow for an exact determination of the active code base
(e.g. `1.2.9.dev68+g46c7a9c`). Additionally, instances with active uncommitted changes will contain
`.dirty` in the local version identifier.

## History

  * 2015-01-23: More guidelines for creating pull requests, support/questions
    redirected to Mailinglist/G+ community
  * 2015-01-27: Added another explicit link to the FAQ
  * 2015-07-07: Added step to add yourself to AUTHORS when creating a PR :)
  * 2015-12-01: Heavily reworked to include examples, better structure and
    all information in one document.
  * 2016-02-10: Added information about branch structure and versioning.
  * 2016-02-16: Added requirement to add information from template to existing
    tickets as well, explained issue with "me too" red herrings.
  * 2016-03-14: Some more requirements for PRs, and a PR template.
  * 2016-06-08: New `prerelease` and `rc` branches explained.
  * 2016-09-09: New `rc/*` branches explained.
  * 2016-09-23: Some more work on "How to file a bug report" based on recent
    experiences
  * 2017-01-25: Fixed a typo
  * 2017-03-09: Allow PRs against `maintenance` branch for bugs in stable.
  * 2017-03-10: Reproduce bugs in safe mode to make sure they are really caused
    by OctoPrint itself and not a misbehaving plugin.
  * 2017-03-27: Added safe mode section to ticket template.
  * 2017-11-22: Added note on how to run the unit tests
  * 2018-03-15: Link to new community forum and some clarifications re bug
    reporting
  * 2018-03-29: "Where to find version numbers" is now located on the FAQ
  * 2018-10-18: Allow PRs against `maintenance` branch for improvements and small
    new features, suggest getting in touch on the forum for larger changes

## Footnotes
  * [1] - If you are wondering why, the problem is that anything that you add
    to your PR's branch will also become part of your PR, so if you create a
    PR from your version of `devel` chances are high you'll add changes to the
    PR that do not belong to the PR.
  * [2] - Yes, we know that this goes against PEP-8. OctoPrint started out as
    a fork of Cura and hence stuck to the coding style found therein. Changing
    it now would make the history and especially `git blame` completely
    unusable, so for now we'll have to deal with it (this decision might be
    revisited in the future).
