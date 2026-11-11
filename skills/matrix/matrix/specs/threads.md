<module>matrix/specs/threads.md</module>
<title>Threads, messages and a work item's activity</title>

<threads>

- `list_threads` finds threads, by work item (`subjectId`), channel, address, person or text; `get_thread` gives one thread's channel, attached work item and participants.
- `list_messages` reads one thread, newest first; `personId`, `since`, `before` and `q` narrow it.
- `create_message` writes into a thread, optionally carrying file versions (`versionIds`); `update_message` rewrites your own message and `delete_message` removes it (a copy already delivered through a channel stays).
- **What someone said**: search the threads before working an item and whenever someone refers to something not on it. What was said outside Matrix and its channels is not recorded: ask.

</threads>

<activity>

A work item's activity is every thread attached to it: a task's own thread and any channel thread attached to it. Nothing is copied between threads: `list_threads` narrowed to the item (`subjectId`) finds them and `list_messages` reads each, newest first.

</activity>

<routing>

- **To a work item**: `get_thread` may suggest the item a thread concerns; confirm it, then attach the thread with `update_thread` `subjectId`. From then it is part of that item's activity for everyone who reads the item. A wrong attachment shows the thread to that item's readers.
- **Nothing to route** (spam, a misdirected thread): `update_thread` `dismissed`.
- `update_thread` `title` names a thread.

</routing>

<the_slack_channel>

The organization's bound Slack channel is where the intake agent answers; Matrix posts there itself, so no Slack tool is needed.

- **A new post** at the top of the channel is `create_thread` with the channel (`list_channels`) and the text.
- **A reply in a channel thread** is `create_message` on that thread: a person's message is posted into the Slack thread.
- **Who reads it**: everyone in the channel, people outside the organization included (`matrix/specs/rules.md` — rule 2). A message is recorded whether or not Slack took the post, so never send it twice to be sure.

</the_slack_channel>

<senders_and_people>

A sender on a channel is an address; mapping it to a person makes their messages theirs.

- `list_addresses` with `mapped=false` is who is still unknown. Map one with `update_address` `personId`, or record a new contact with `create_address` and `person: {name, email?}`. Dismiss an address that is no one to track (`update_address` `dismissed`).
- `list_persons` finds the organization's members and the contacts its records name; `get_person` gives one, with their addresses and Grants.

</senders_and_people>
