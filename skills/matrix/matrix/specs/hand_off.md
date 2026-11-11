<module>matrix/specs/hand_off.md</module>
<title>The hand-off note</title>

<hand_off_note>

Work on a Project or a task is picked up by whoever comes next, person or agent, from its hand-off note. Members and the worker agent keep it; the intake agent leaves none.

- **Before working an item**, read its latest note and pick up from its Next step. A member's note is the newest message starting `**Hand-off note**` in the item's activity (`matrix/specs/threads.md` — `<activity>`); the worker agent's is its latest completed turn's summary (`get_agent_turn`). Read both and take the newer.
- **Before ending**, leave one. A member posts it with `create_message` in the own thread of the task worked (`get_task` names it; for a Project, the task the work ended on), never in a channel thread, which posts to Slack. The worker agent writes it as its turn's summary.

```
**Hand-off note** · <YYYY-MM-DD> · <your name> via <the assistant or agent used>

**Done**
- …

**Decisions and why**
- …

**Files and versions**
- <name>: file <fileId>, version <versionId>

**Open questions / waiting on**
- …

**Next step**
- …
```

Keep it short; write "None" under an empty heading rather than dropping it.

</hand_off_note>
