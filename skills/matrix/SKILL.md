---
name: matrix
description: Use for work in Matrix, the Xemself workspace where an organization's people and agents coordinate, through its MCP connector. Bring it up for - what's waiting on me, my tasks, a Project and its tasks (start one, assign, change a status, reorder, archive); a thread or message, what someone said, routing a thread to a task, posting in the organization's Slack channel; finding, reading, uploading or filing a file, packages; a deal and where its negotiation stands; having the worker agent do something and checking what it did; the organization, its entities, people, addresses, channels, catalog, Roles, Grants, agents and activity; the hand-off note. The same skill serves a member and an agent (the worker agent on a turn, the intake agent in a channel).
compatibility: Requires the Matrix MCP connector named in matrix/meta.md, signed in with a Matrix account or authenticated by an agent's credential.
---

# Matrix

You work in Matrix as a member of an organization: a person holding a Role there (owner, admin, member, viewer or a custom one), or an agent acting under its own Grant (the worker agent, the intake agent, or an integration). This skill says which Matrix tool to use, when and in what order. A tool's own description says what it takes, returns and refuses; where the two disagree, the tool wins.

Every path here is from the folder that holds `matrix/`. A citation names a file and, after a dash, a section in it. Follow one when the task needs that fact; never fill it in from memory.

## Start

- **Call `get_me` first.** It says who you act as and the organizations your Grants cover. When it covers more than one and the task does not say which, ask once; then name that organization (`organizationId`) on every call, since nothing is remembered between calls.
- **Your tool list is your access.** A tool you do not see is one you cannot use: say so, never work around it (`matrix/specs/conventions.md` — `<the_tool_list>`).
- **If you are an agent**, your runtime says which one, and your procedure is its own file: the worker agent on a turn reads `matrix/specs/worker.md`, the intake agent in a channel reads `matrix/specs/intake.md`. An integration works as a member does, within its Grant.

## On every action

- **Before your first write, read `matrix/specs/rules.md`.** It is short, and a write can break its rules without any tool refusing it.
- **When you work an item**, pick up from its hand-off note and leave one before you end: `matrix/specs/hand_off.md`.

## What to read

Read the file the request is about. Read another only when that file sends you there for a fact the task needs.

| When the request is about | Read |
| --- | --- |
| what is waiting on you; a Project or a task: finding, starting, assigning, a status, the tree, archiving | `matrix/specs/work.md` |
| threads and messages: what someone said, routing a thread to a task, posting in the organization's Slack channel, senders and addresses | `matrix/specs/threads.md` |
| finding, reading, uploading or filing a file; packages | `matrix/specs/files.md` |
| a deal: its sides, versions and whose move it is | `matrix/specs/deals.md` |
| the worker agent: having it work, stopping it, reviewing what it did; the intake agent in a channel | `matrix/specs/agents.md` |
| the organization: its record and note, entities, people, channels, catalog, access, activity; what is done in the Matrix app; the platform admin | `matrix/specs/organization.md` |
| you are the worker agent, on a dispatched turn | `matrix/specs/worker.md` |
| you are the intake agent, in a bound channel | `matrix/specs/intake.md` |

## Reference, on demand

| When you meet | Read |
| --- | --- |
| an id or a status you do not recognise; a list that pages; a refused write; an error | `matrix/specs/conventions.md` |
| a question no row above covers, to find which tool answers it | `matrix/specs/tools.md` |
