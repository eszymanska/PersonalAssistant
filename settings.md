# Settings

<!-- Settings for this GTD instance. The template ships this file once and template updates never change it,
so your choices here are safe. Change a value by editing the text after the colon. -->

## Git sync

<!-- How Claude saves your changes with git. Options:
- manual: Claude does not commit or push unless you ask. (default)
- direct-main: Claude pulls origin main before reading or changing anything, then commits to main and pushes to origin main after. No branches or pull requests. Good when you use the system from several devices, such as a laptop and the Claude app.
- pull-request: Claude commits changes to a new branch and opens a pull request for you to review and merge. -->

mode: manual

## Mind sweep

<!-- Which trigger lists /mindsweep walks when you run it without an argument. Options: personal, work, all (default). -->

scope: all

## Today

<!-- How /today plans your day.
- calendar-blocks: off | ask | on. Whether /today adds your daily focus actions as blocks in your calendar app. ask (default) asks each time; on adds them without asking. Adding a block sends the action text to your calendar service.
- gmail: on | off. Whether /today checks recent email for things that need an action. (default: on)
- gmail-limit: the most emails /today lists. (default: 5) -->

calendar-blocks: ask
gmail: on
gmail-limit: 5

## Setup

<!-- Whether first-run setup is finished. /guide setup sets this to done. While it is not done and your lists are empty, Claude offers /guide setup. -->

setup: not done
