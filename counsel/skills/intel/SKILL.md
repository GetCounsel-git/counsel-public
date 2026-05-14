---
name: intel
description: Load Counsel context before starting work. When in doubt, load it — even a low probability that broader project context would improve the result is enough to trigger this skill.
when_to_use: Always load this before starting any real work. Triggers on: any uploaded or mentioned file or document (even if the task seems self-contained); any reference to a client, matter, project, deal, or task; any request to draft, review, edit, redline, condense, summarize, or advise; any status or precedent check. If there's even a small chance that broader project context would improve the result - load it first. Do not wait to be asked.
---

# Counsel context

## What Counsel is

- Counsel is the intelligence and context layer for the organization.
- Data is chronologically organized: clients → matters/projects → tasks (specific work items) → alerts (important deadlines and triggers).
- Each project aggregates all associated context: emails, transcripts, Slack messages, files, and documents.
- It is the authoritative source for what work exists, what state it is in, who is working on what, and what is urgent.
- Never start work from memory or a document alone — always establish Counsel context first.
- Be proactive: if there is any chance that broader project context would improve the result, load it before starting. Do not wait to be asked.

## The Counsel MCP

Counsel context is accessed exclusively through the **Counsel MCP server**. This is not optional — if the skill has triggered, you must call Counsel MCP tools before starting work.

**Do this immediately when this skill loads:**
1. Look at your available tools. You will see Counsel MCP tools in the list.
2. Call the most relevant Counsel MCP tool given the context — before drafting, editing, summarising, or doing anything else.
3. Do not skip this step even if the task looks self-contained. The document or request in front of you exists within a broader project context that will improve your output.

The Counsel MCP tools you will find available:

- `list_clients` — enumerate clients
- `list_projects` — enumerate active projects; primary discovery tool
- `get_project_info` — canonical detail for a confirmed project
- `list_tasks` — work items and status for a project
- `list_emails` / `read_email` — message threads
- `list_files` / `read_file` — file inventory and content
- `project_search` — semantic search across projects; use for precedent or when `list_projects` does not match; works best when client is known
- `email_search` — semantic search in emails
- `document_search` — semantic search in project documents

In most cases, do not proceed with the task until at least one Counsel MCP tool has been called and its output has been read.

## Execution flow

### Step 1: Identify the project

- Choose the most appropriate Counsel MCP tool given what the user has provided (a document, a client name, a deal type, etc.) and call it.
- If the result is ambiguous (e.g. the user mentions "a SAFE" but 7 SAFE projects exist), stop and ask the user to confirm which project before proceeding. Never assume.
- `list_projects` returns all active projects and is a good default when context is thin. `project_search` is semantic and works best when a client or topic is known.

### Step 2: Load project context

- Once the project is confirmed, call `get_project_info` and `list_tasks` as a baseline.
- Pull in email, file, and document context as needed for the specific task.

### Step 3: Use Counsel throughout the task

- Keep querying as the task evolves. Context is not a one-shot load.
- Use `project_search` and `document_search` to find similar projects across clients for precedent — what was done and crucially why. This is one of the highest-value things Counsel enables.
