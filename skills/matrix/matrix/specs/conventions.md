<module>matrix/specs/conventions.md</module>
<title>How every tool behaves</title>

<the_tool_list>

- **The tool list is your access**: a tool is listed when one of your Grants admits it, and every call is decided again at its own organization. A tool you cannot see is one you cannot use: say what the list cannot do, never work around it.
- **Some acts are never a tool**, for anyone, because a document in a model's context could steer them: granting or changing access (an invitation, a Grant, a Role, an agent and its credentials), creating or removing a channel, editing a person, your own profile and security, billing, moving a file's bytes outside an upload ticket, and writing a deal. They are taken in the Matrix app (`matrix/specs/organization.md` — `<in_the_app>`).
- **`organizationId`** defaults only when your Grants name exactly one organization; otherwise pass it on every call (`get_me`, `add_pin`, `remove_pin` and `list_scopes` take none).

</the_tool_list>

<ids_and_statuses>

- **An id says what it names**: `org_` an organization, `prj_` a Project, `tsk_` a task, `thr_` a thread, `msg_` a message, `fil_` a file, `ver_` a version, `pkg_` a package, `chn_` a channel, `adr_` an address, `prs_` a person, `ent_` an entity, `dea_` a deal, `trn_` an agent turn, `agt_` an agent, `rol_` a Role, `gra_` a Grant. A `subjectId` names a Project or a task.
- **One status vocabulary** for Projects and tasks: `not_started`, `in_progress`, `waiting` (stuck on another party's action), `completed`, `canceled`. Completed and canceled are resolved; the rest are open. Who a waiting item waits on is read from its threads.

</ids_and_statuses>

<lists>

- **Lists summarize.** Fetch detail only for the record the task needs.
- **Paging.** A list answers `nextCursor`; pass it back as `cursor`, with the same filters, for the next page; null means the last page.
- **A filter narrows, never widens**: a list holds only what your access covers. `q` searches, best match first.
- **Pins** (`add_pin`, `remove_pin`) mark the Projects and tasks you follow; a list with `pinned=true` shows them.

</lists>

<writes>

- **A write answers the record's id and new revision, not the record.** Read again before a write that needs the current state.
- **Revisions guard concurrent edits.** A write against a stale `expectedRevision` changes nothing and is refused 409: read again, then decide again; never resend the same write blindly.
- **Never repeat a write that succeeded**, and never retry a refused one unchanged.

</writes>

<errors>

- An error reads `code: message` and says whether it is retryable; only a retryable one is worth retrying.
- **Not found is opaque.** An unknown, foreign or malformed id answers the same not-found: it confirms nothing, and guessing other ids is pointless.

</errors>
