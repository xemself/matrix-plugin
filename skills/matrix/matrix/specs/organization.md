<module>matrix/specs/organization.md</module>
<title>The organization, its people and access, what is done in the app, the platform admin</title>

<the_organization>

- **The organization** (`get_organization`): its name, status, note and catalog repository. The note is the members' running note about the organization; `update_organization` changes the name and the note; `include=noteVersions` reads the note's history. An agent never writes the note.
- **Entities** are the organization's legal persons, the primary first: `list_entities`, `get_entity`, `create_entity`, `update_entity`. A registered name is the only name that identifies one; an entity without one is carried by its proposed name and status, never by the organization's name.

</the_organization>

<people_and_access>

- **People**: `list_persons` (members and the contacts its records name), `get_person` (one person's addresses and Grants here).
- **Access**: a person's membership is a Grant, a Role held at the organization; an invitation is a pending Grant. `list_grants` (`pending=true` for invitations), `list_roles` and `get_role` (a Role's Scopes), `list_scopes` (what each Scope allows). The system Roles are `owner`, `admin`, `member` and `viewer` for people, `agent_worker` and `agent_intake` for the two agents; an organization may add custom Roles.
- **Agents**: `list_agents`, `get_agent` (an agent's Grants and credentials, never a secret).
- **What happened**: `list_activity`, newest first, narrowed by `kind`, actor, subject or time.

</people_and_access>

<channels>

The organization's channels are where threads come in; a bound Slack channel is where the intake agent answers. `list_channels` and `get_channel` read them; `update_channel` renames one. Binding or removing a channel is the app's (`<in_the_app>`).

</channels>

<the_catalog>

`list_catalog` shows the organization's catalog as deployed from its repository (project templates, and deal templates with `kind=deal`), over the platform's; `get_template` reads one: its fields, task templates, question set and `instruction`. Nothing here edits it: a catalog is changed in its repository.

</the_catalog>

<in_the_app>

These are taken in the Matrix app, never through the connector (`matrix/specs/conventions.md` — `<the_tool_list>`); when a task needs one, say which act and that a person takes it there:

- inviting someone, granting, changing or revoking a Grant, and Roles and their Scopes;
- creating an agent, its Grants and its credentials (a secret is shown once, in the app);
- binding or removing a channel;
- editing a person, your own profile, sign-in and connected apps;
- billing;
- starting a deal, sending a version, accepting or reopening one.

</in_the_app>

<the_platform_admin>

A platform admin holds the platform Grant, which belongs to no organization and reaches every organization with an owner's access. Through the connector it works one organization at a time: no organization is assumed, so name `organizationId` on every call, and confirm it before any write (`matrix/specs/rules.md` — rule 1). The platform's own surface (the roster of organizations, creating or archiving one, its catalog repository link, every person) is worked in the app.

</the_platform_admin>
