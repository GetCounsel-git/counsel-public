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

Discover Counsel MCP tools at runtime via `list_tools`, then choose tools by capability (project discovery, project details, task status, communications, files, and search) instead of relying on fixed names.

In most cases, do not proceed with the task until at least one Counsel MCP tool has been called and its output has been read.

## Execution flow

### Step 1: Identify the project

- Choose the most appropriate Counsel MCP tool given what the user has provided (a document, a client name, a deal type, etc.) and call it.
- If the result is ambiguous (e.g. the user mentions "a SAFE" but 7 SAFE projects exist), stop and ask the user to confirm which project before proceeding. Never assume.
- If context is thin, start with a broad listing/discovery/text search tool. If the user provides a client or topic, prefer a semantic search/discovery tool.

### Step 2: Load project context

- Once the project is confirmed, load canonical project details and current task/work-item status as a baseline.
- Pull in email, file, and document context as needed for the specific task.

### Step 3: Use Counsel throughout the task

- Keep querying as the task evolves. Context is not a one-shot load.
- Use cross-project and document-level semantic search to find precedent across clients — what was done and crucially why. This is one of the highest-value things Counsel enables.

### Step 4: Share source URLs when available

- The user may want to verify context at the source.
- Share URLs only when the Counsel MCP response includes valid canonical URLs.
- If no valid canonical URLs are present, do not invent or infer URLs; simply omit them.
