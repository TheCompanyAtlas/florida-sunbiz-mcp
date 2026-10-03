# Florida Sunbiz Company & Officer MCP

Connect your AI assistant to [The Company Atlas](https://thecompanyatlas.com) for Florida company registry research through the Model Context Protocol.

This listing is a focused entry point for:

- Florida corporations, LLCs, partnerships and non-profits from the Division of Corporations (Sunbiz)
- Officers, managers, members and registered agents
- Company status, filing type, addresses, FEI/EIN and filing dates

The MCP connection is provided by The Company Atlas. This repository does not run a separate server.

## Connect

```
https://thecompanyatlas.com/mcp/florida
```

Add this URL as a custom MCP connector in Claude, Cursor, or any MCP-compatible client. Sign in with Google when prompted.

- Transport: Streamable HTTP
- Auth: Google OAuth (sign in once, stays authorized)
- Docs: [thecompanyatlas.com/mcp/connect/florida](https://thecompanyatlas.com/mcp/connect/florida)

## Tools

### `Florida_search_companies`

Search entities by name, filing type, status, city, ZIP, FEI/EIN or filing date. Filters are combined with AND logic; include at least one.

| Parameter | Type | Description |
|---|---|---|
| `q` | string, optional | Entity name substring, 3–120 characters |
| `entityType` | string, optional | Sunbiz filing type code, e.g. `FLAL`, `DOMP` |
| `active` | boolean, optional | Filter by active status |
| `city` | string, optional | Substring of the principal address |
| `zip` | string, optional | 5-digit principal ZIP |
| `feiNumber` | string, optional | Federal employer id as filed, e.g. `59-1234567` |
| `filedFrom` / `filedTo` | date, optional | Filing date range |
| `page` / `limit` | integer, optional | Pagination, `limit` up to 50 (default 20) |

### `Florida_get_company`

Full profile by Sunbiz document number (e.g. `L21000123456`): officers, registered agent, FEI number, mailing address, last transaction.

### `Florida_search_officers`

Find every entity a person or registered-agent firm is listed on, with their role and title. `name` is a substring of the name as filed, usually `LAST, FIRST M`.

## Example prompts

- Find active Florida LLCs with "solar" in the name registered in Miami since 2024
- Which Florida companies list a given person as manager or authorized member?
- Which companies use a given registered-agent firm?

## Data source

Florida Division of Corporations (Sunbiz) bulk export.
