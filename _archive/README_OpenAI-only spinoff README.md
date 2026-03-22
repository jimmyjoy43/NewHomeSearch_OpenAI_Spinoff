# New Home Search: OpenAI-Only Spinoff

This version removes GitHub, Notion, and Claude from the operating model.
It is designed to run entirely inside OpenAI products and services.

## Recommended deployment modes

### 1. ChatGPT Project mode (best default)
Use a single ChatGPT Project as the workspace.
Upload the files in `state/` and `docs/`, then paste `chatgpt_project/project_instructions.md` into the Project instructions field.

### 2. Custom GPT mode (optional)
If you want a one-click operator, paste `custom_gpt/gpt_instructions.md` into the GPT builder and upload the files listed in `custom_gpt/knowledge_manifest.md`.

### 3. Agent-assisted mode (optional)
If your ChatGPT plan includes agent capabilities, you can use the same project files while having ChatGPT browse, research, and work with files in one place.

### 4. API mode (optional)
If you want a service-driven workflow inside OpenAI infrastructure, use the blueprint in `api_optional/responses_api_blueprint.md`.

## Source of truth rule
The canonical state is always the files in `state/`.
Do not rely on memory for exact tables, deadlines, or score history.

## File-update protocol
In pure ChatGPT Project mode, the model cannot be trusted to silently mutate project files. Use this workflow:
1. Ask ChatGPT to produce the full updated replacement file.
2. Review it.
3. Replace the project file with the reviewed version.
4. Continue in the same project so context stays together.

## Included state
This spinoff ships with the same normalized seed state as the strengthened repo:
- existing candidate buildings migrated into `state/buildings.csv`
- existing decisions migrated into `state/decisions.csv`
- empty but ready templates for units, tours, contacts, and evidence

## Minimal runbook
1. Create a ChatGPT Project.
2. Upload everything from `state/` and the key docs from `docs/`.
3. Paste `chatgpt_project/project_instructions.md` into the Project instructions.
4. Start with `chatgpt_project/start_here.md`.
5. Use the stage prompts in `chatgpt_project/`.
6. After each meaningful change, replace the relevant file in the project with the reviewed full-file output.
7. Set milestone reminders using `chatgpt_project/tasks_setup.md`.
