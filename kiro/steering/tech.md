# Technical Documentation

## Tech Stack

| Component | Technology |
|-----------|------------|
| LLM | DeepSeek V4 Flash (`deepseek-v4-flash`) |
| SDK | OpenAI Python SDK |
| Config | python-dotenv (`.env` file) |
| Templating | Jinja2 |
| Testing | pytest |

## Dependencies

```
openai
python-dotenv
jinja2
```

## Environment Variables

Create `.env` file with:
```
OPENAI_API_KEY=your_api_key
OPENAI_BASE_URL=your_base_url
```

## Key Files

### app.py
- Entry point
- Contains `login()` function (placeholder)
- Basic hello world test

### weather_agent.py
- **Core agent logic** - `run_agent()` function
- Defines system prompt
- Implements tool-calling loop (max 10 rounds)
- Uses `tools_schema.json` for tool definitions

### weather_tool.py
- `get_weather(city, date)` function
- Returns dict with: city, date, weather, temperature
- Mock data for Beijing, Shanghai, Guangzhou
- Date parsing: "today", "tomorrow", "YYYY-MM-DD"

### f_sys_prompt.py
- Generates system prompt using Jinja2
- Template: `templates/agent_system.j2`
- Defines agent name, role, tools, constraints, examples

### tools_schema.json
- JSON schema for tool definitions
- Used by OpenAI SDK for tool calling

## Agent Loop Pattern

```
1. User message → LLM
2. LLM decides: call tool or respond
3. If tool call:
   a. Parse tool name + args
   b. Execute via TOOL_DISPATCH
   c. Return result to LLM
   d. Loop (back to step 2)
4. Return LLM response
```

## Tool Dispatch

Tools are registered in `TOOL_DISPATCH` dict in `weather_agent.py`:
```python
TOOL_DISPATCH = {
    "get_weather": get_weather,
}
```

Add new tools by:
1. Define function in appropriate module
2. Add entry to `TOOL_DISPATCH`
3. Update `tools_schema.json`