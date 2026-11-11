<module>matrix/specs/deals.md</module>
<title>Deals</title>

<deals>

A deal is a negotiation the organization keeps between two parties it names, on a question set from a deal template in its catalog: each side writes its terms as a new version until both agree. The organization's members write for a side; each side's outside persons act through links emailed to them.

- **Read**: `list_deals`, most recently updated first, each with whose move it is; `get_deal` for one, with its versions, history, agreement and each side's persons. `side` reads it as that side does.
- **Its template**: `list_catalog` with `kind=deal`, `get_template` with `kind` for its question set.
- **Writing a deal is never a tool.** Starting one, sending a version, accepting and reopening are a person's acts, taken in the Matrix app (`matrix/specs/organization.md` — `<in_the_app>`): say which, and where. Reading where a deal stands, and answering questions about it from what `get_deal` shows, is yours.

</deals>
