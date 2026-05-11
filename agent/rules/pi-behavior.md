# Pi Specific Behavior Rules

These rules apply specifically when executing within the `pi` coding agent harness. `pi` is a minimal, stateless terminal execution environment.

- **No Background Bash (Stateless Execution)** — Do NOT attempt to run blocking servers (e.g., `npm run dev`, `python -m http.server`, `cargo watch`), long-polling processes, or rely on hidden background bash state. Every tool execution in `pi` is purely stateless and transient.
- **Use Tmux for Servers** — If a persistent server or background process is required for a task, explicitly instruct the user to open a separate `tmux` pane or another terminal window to run it. Once the user confirms it is running, proceed by interacting with its external ports or outputs via standard stateless commands (e.g., `curl`).
- **Web Search Routing** — When the user asks to "search the web", "look up documentation", or asks about recent/current information, do NOT say you lack internet access. Immediately use the `brave-search` tool to find the information. If you need to interact with a complex webpage or take a screenshot, use `browser-tools`.
