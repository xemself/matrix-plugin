<module>matrix/specs/tools.md</module>
<title>Every tool by the question it answers</title>

<tools>

Reference: read it when a question fits no area the skill's `SKILL.md` routes, or to find which tool answers one. The last column names the file with the procedure. Your own list holds only what your Grants admit.

**Who, and the organization**

| Question | Tools | Detail |
| --- | --- | --- |
| Who am I acting as, in which organizations? | `get_me` | `SKILL.md` — Start |
| The organization, its note | `get_organization`, `update_organization` | `matrix/specs/organization.md` |
| Its legal persons | `list_entities`, `get_entity`, `create_entity`, `update_entity` | `matrix/specs/organization.md` |
| People | `list_persons`, `get_person` | `matrix/specs/organization.md` |
| Access: Grants and invitations, Roles and Scopes, agents | `list_grants`, `list_roles`, `get_role`, `list_scopes`, `list_agents`, `get_agent` | `matrix/specs/organization.md` |
| What happened | `list_activity` | `matrix/specs/organization.md` |
| The catalog | `list_catalog`, `get_template` | `matrix/specs/organization.md` |

**Work**

| Question | Tools | Detail |
| --- | --- | --- |
| Projects | `list_projects`, `get_project`, `create_project`, `update_project` | `matrix/specs/work.md` |
| Tasks | `list_tasks`, `get_task`, `create_task`, `update_task`, `delete_task` | `matrix/specs/work.md` |
| Follow an item | `add_pin`, `remove_pin` | `matrix/specs/conventions.md` |
| The worker agent's turns | `create_agent_turn`, `list_agent_turns`, `get_agent_turn`, `update_agent_turn` | `matrix/specs/agents.md` |
| Deals | `list_deals`, `get_deal` | `matrix/specs/deals.md` |

**Threads**

| Question | Tools | Detail |
| --- | --- | --- |
| What did someone say? | `list_threads`, `get_thread`, `list_messages` | `matrix/specs/threads.md` |
| Attach, dismiss or title a thread | `update_thread` | `matrix/specs/threads.md` |
| Post, edit or delete a message; start a thread in the channel | `create_message`, `update_message`, `delete_message`, `create_thread` | `matrix/specs/threads.md` |
| Senders on a channel | `list_addresses`, `create_address`, `update_address` | `matrix/specs/threads.md` |
| Channels | `list_channels`, `get_channel`, `update_channel` | `matrix/specs/organization.md` |

**Files**

| Question | Tools | Detail |
| --- | --- | --- |
| Find, read, upload, file and revise files | `list_files`, `get_file`, `create_upload`, `create_file`, `create_file_version`, `update_file` | `matrix/specs/files.md` |
| Packages | `list_packages`, `get_package`, `create_package`, `update_package` | `matrix/specs/files.md` |

</tools>
