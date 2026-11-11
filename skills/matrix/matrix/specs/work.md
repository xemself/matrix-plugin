<module>matrix/specs/work.md</module>
<title>Projects and tasks</title>

<the_model>

- **A Project** is a piece of the organization's work started from a project template in its catalog: a title, status, assignee, participants, fields and a tree of tasks. It keeps a snapshot of its template; a later template change never rewrites it.
- **A task** is a node of one Project's tree: status, assignee, participants, fields, dependencies, and a thread of its own. A task with no children is a step; a parent's status is derived from its steps.
- **Work is held by people.** An assignee is a person; an agent never holds work and acts only through turns (`matrix/specs/agents.md`).

</the_model>

<your_work>

- **What is waiting on you**: `list_tasks` and `list_projects` narrowed to you as `assigneeId` (your person id is in `get_me`) and to open statuses; `pinned=true` for what you follow.
- **Which Project**: the one the request names, found with `list_projects` (`q` searches titles). A request that names a step instead is found with `list_tasks`, which answers each step with its Project. When more than one matches, ask which, naming the candidates; never pick one.
- **One item**: `get_project` with `include=tasks` (the only read with the tree, each task with its derived `blocked` and `progress`) or `get_task`; then its activity (`matrix/specs/threads.md` — `<activity>`) and its latest hand-off note (`matrix/specs/hand_off.md`).

</your_work>

<starting>

- **A Project**: `list_catalog` for the organization's project templates, `get_template` for one's fields and task templates, then `create_project` from it (`templateKey`), titled as the person names the work, with the fields they gave, in their words. It creates the template's tasks.
- **A task**: `create_task` under its Project (`parentId` for a place in the tree): with a task template's `taskKey` it brings that template's subtree and fields; with a `title` alone it brings nothing else.

</starting>

<the_writes>

Each write changes the item for everyone who works it, so it is made on a person's word or as the work plainly requires. A status, an assignee and an archive are a person's: an agent's write of one is refused.

- **Take or assign**: `update_task` or `update_project` with `assigneeId`: yourself, another member (`list_persons`), or null to release it.
- **Who works on it**: `update_task` `participants` (`add`, `remove`); `update_project` `participants` (the whole list).
- **Fields, title, due date, status**: `update_task`, `update_project`.
- **The tree**: `update_project` `structure` is the whole live tree as `get_project` `include=tasks` reads it, so a move, an order or a dependency is that tree read, changed and written back; an omitted task is refused.
- **Archive** a finished Project, or restore it: `update_project` `archived`.
- **A task added by mistake**: `delete_task` removes it with its subtree and links. Work that is no longer needed is canceled, not deleted.

</the_writes>

<order_and_status>

- **Order is guidance.** In an ordered list a later step may start or finish first. A real prerequisite is a dependency; `blocked` is derived for people to read and refuses no write.
- **A status is a label**, any to any on a step. A task with children serves a status derived from its steps and takes only `canceled`, which cancels its open steps. Nothing completes a Project but a person.

</order_and_status>
