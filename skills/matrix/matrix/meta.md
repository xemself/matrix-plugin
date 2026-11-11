<folder>matrix/</folder>

<description>

The Matrix skill: how an organization's members, human or agent, work Matrix through its MCP tools. Matrix is the Xemself workspace where an organization's people and its agents coordinate Projects, tasks, threads, files and deals. One skill serves every reader; what differs for an agent is its own spec (`specs/worker.md`, `specs/intake.md`). `SKILL.md` is the entry and the router; nothing else is read before a task.

</description>

<connector>

The connector is Matrix's MCP server, `https://api.matrix.xemself.ai/mcp` (streamable HTTP). A person signs in with their Matrix account; an agent authenticates with its own credential (its client id and secret, or its runtime's token). The server lists the tools the caller's Grants admit and serves this folder as resources: `skills://matrix/`.

</connector>

<reading>

- **Paths** are from the folder that holds `matrix/`: an installed skill's own folder, a checkout's root, `skills://` on the server (`matrix/specs/rules.md` is `skills://matrix/specs/rules.md`).
- **`SKILL.md`** is the entry and the router: who the reader is, how to start, what holds on every action, and which file a request needs.
- **`meta.md`** is a folder's index. No task starts by reading one.
- **`specs/`** holds one file per area of work, read when `SKILL.md` routes a request to it or a file you are in cites it.
- **XML tags** mark a file's sections. A citation names the file and, after a dash, the section: `matrix/specs/rules.md` — `<rules>`.
- **A fact is stated once** and cited everywhere else.

</reading>

<contents>

- `SKILL.md` — the entry: when the skill applies, who the reader is, the start, the routes
- `meta.md` — this index: `<connector>`, `<reading>`
- `specs/` — the detail, one file per area of work; see `specs/meta.md`

</contents>
