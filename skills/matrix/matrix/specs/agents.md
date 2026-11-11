<module>matrix/specs/agents.md</module>
<title>Working with the worker agent and the intake agent</title>

<the_worker_agent>

Each organization has one worker agent: a member that works one dispatched turn at a time, on a Project or a task. Its turns run one at a time, oldest first. It records its work as messages and file versions on the subject, never posts outside Matrix, holds no work, sets no status and dispatches nothing. How it works a turn is `matrix/specs/worker.md`; what follows is the dispatching member's side.

</the_worker_agent>

<dispatching>

`create_agent_turn` on a Project or a task (`subjectId`) queues the worker agent. Its `instruction` is your whole brief: nothing comes back through the call, and the work lands later on the subject.

- **On a task** it does the task's work; **on a Project**, its open tasks in the order the tree gives.
- **To continue its work**, post your direction in the item's thread or put it in the instruction, and dispatch again: a message alone queues no turn.
- **A turn queued or running** is stopped with `update_agent_turn` `canceled`.
- **A refused dispatch** (`budget_exhausted`, `no_worker_agent`) leaves the work with you.

</dispatching>

<reviewing>

1. Read the turn: `list_agent_turns` on the subject, `get_agent_turn` for one (its status, outcome, cost, instruction and summary, which is its hand-off note).
2. Read what it recorded: its messages in the item's thread (`list_messages`) and the versions it filed (`get_file`).
3. A **Stop** message says exactly what a person must decide before the work goes on: answer it in the thread and dispatch again, or take the work yourself.
4. Anything that leaves the organization is yours to send (`matrix/specs/rules.md` — rule 2).

</reviewing>

<the_intake_agent>

The intake agent answers in the organization's bound Slack channel. It takes a request in as a Project or a task, or attaches the thread to existing work, dispatches the worker agent or leaves the item to the members, and replies in the thread. Its procedure is `matrix/specs/intake.md`; the organization's own practice, when it has one, decides where it speaks.

- **Bring it in** with an @-mention, or a `:matrix:` or 🛎️ reaction on a message (a full member of the Slack workspace only); from then it sees every message in that thread. 🏁 on a message steps it out; an @-mention brings it back. ⚠️ means its turn failed: check the item, or ask again.
- **One of you answers a thread at a time**: when a member takes the thread, it steps out.
- What it opened, attached and dispatched is on the records: read the item's activity and its turns.

</the_intake_agent>
