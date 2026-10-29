# Repository agent instructions


<!-- BEGIN LOCAL AI HUB TOOL POLICY -->
## Local AI Hub

- Use the host-level `local-ai` MCP registration. It serves all repositories; do not add machine-specific absolute launchers to this repo.
- `local_ai_repo` supports `search`, `code_index`, `context`, `solve`, `review_diff`, `callers`, and `dead_code`. `local_ai_artifact` provides exact source/evidence slices.
- `local_ai_coord` supports `claim`, `release`, `memory_record`, `memory_find`, `context_compile`, `task_create`, `task_checkpoint`, `ask`, and `answer`. `local_ai_status` supports compact `brief`/`models` readiness. Follow only actions and fields in the active schema.
- Run tests, builds, lint and security checks with the host-native command tool after gathering repository evidence. Keep output bounded.
- For substantial work, create a task contract, query relevant memory and checkpoint meaningful phase changes. Use `review_diff` after edits where relevant. Never synthesize verification receipts.
- Native fallback after Hub failure requires `terminal=true` and `retryable=false`; unknown commands also require `native_fallback_allowed=true` and host authorization. Do not repeat operations with `outcome_unknown`. Keep work inside the authorized repository root.
On first work in each stable repository root, resolve the absolute Git root and inspect `.local-ai.toml` plus any applicable `.local-ai.worktree.toml`. If project settings are missing or incomplete, derive only evidence-backed repo-specific `exclude_paths` and `[preprocess].exclude_paths`, `[custom_extensions].text` and `.binary`, `pinned_context`, and `entry_points`; preserve existing settings, rely on Hub defaults when they already cover the repo, and never guess ignore patterns, extensions, or absent documentation paths. Then call `local_ai_repo(action="preprocess", root=ABS_ROOT)` once to idempotently register the project. Do not force-refresh an existing registration or poll asynchronous preprocessing; continue with the needed bounded repository action.
<!-- END LOCAL AI HUB TOOL POLICY -->
