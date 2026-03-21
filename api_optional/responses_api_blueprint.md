# Optional OpenAI API Blueprint

This is the service-based version for teams that want to keep the workflow entirely on OpenAI infrastructure while using the API.

## Core ingredients
- Responses API for orchestration
- `web_search` for fresh market and building research
- `file_search` against uploaded project files for canonical state retrieval
- file uploads or a vector store containing the project docs and CSVs

## Suggested flow
1. Upload the canonical state files.
2. Attach them to a vector store.
3. For each stage, create a Responses API request with:
   - project instructions
   - the relevant user task
   - `file_search` enabled
   - `web_search` enabled when freshness matters
4. Save the model's structured output as the reviewed next state.
5. Re-upload the replacement state files.

## Recommended state discipline
- Keep the same normalized file split as the ChatGPT Project version.
- Treat the uploaded files as the source of truth.
- Avoid pushing exact state into memory-like system messages.
- Keep every update explicit and reviewable.

## Minimal object model
- `buildings.csv`: one row per building
- `units.csv`: one row per unit
- `evidence.csv`: one row per durable claim
- `decisions.csv`: one row per advance, reject, apply, or sign decision

## When to prefer API mode
- you want reproducible prompts
- you want tighter control over the tools used
- you want to build a lightweight internal operator without GitHub or Notion
