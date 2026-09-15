---
name: kleap-builder
description: Build, inspect, edit, publish, and maintain websites, apps, internal tools, and other web products with Kleap. Use when the user asks to work on a product hosted or created with Kleap.
---

# Kleap builder

Use the Kleap MCP tools as the source of truth for Kleap projects and their deployment state.

## Operating rules

1. Identify the intended project before changing anything. If the user provides a domain or published address, use `find_app`; otherwise use `list_apps`. Do not guess an app ID.
2. Begin existing-project work by inspecting the current state. Use `list_app_files` and `read_files` as appropriate; reserve `get_app` for the final preview.
3. For a precise change, read the current file and use `edit_files` with the smallest exact replacement. Preserve every unrelated byte, page, section, image, link, and setting.
4. Use `write_files` for new files or a replacement the user explicitly requested. Never overwrite an existing file blindly.
5. Use `create_app` for a new product and `modify_app` when the user requests a broader change that Kleap's builder should implement. Do not repeat a slow or apparently stalled call; inspect its task state first.
6. Treat creation, editing, publication, domain connection, and deletion as separate actions. Perform only the actions the user requested. Before publishing, connecting a domain, deleting files, or changing a live production product, make sure the user's instruction clearly authorizes that specific action.
7. For a create or modify task, verify both completion and deployment with `check_task`. After a requested source publish, call `get_publish_status`. Do not describe a product as live from a queued task, an old URL, or an assumption.
8. End successful work with one `get_app` call so the user receives the current project, screenshot, and address. If the action failed, explain the failure and do not claim completion.

## Data and safety

- Never place passwords, API keys, OAuth tokens, customer data, or private URLs in project source, chat instructions, plugin files, or logs.
- Use the client's OAuth flow for authentication. Do not ask the user to paste credentials into chat.
- When reading form submissions or other personal data, return only the fields needed for the user's request. Never copy submissions into project files or logs.
- Do not delete source files, publish, connect a domain, purchase anything, send a message, or change billing unless the user directly requested that action.
- For forms, authentication, accounts, payments, or stored records, use Kleap's supported first-party components and backend paths. Do not substitute browser-only storage for durable user data.
- Separate what was read, what was changed, what was published, and what still requires approval.

## Useful request pattern

Ask for the outcome, the project or domain, the content that must remain unchanged, and whether the result should be saved as a draft or published. If these are already clear from the conversation, proceed without asking again.
