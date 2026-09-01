# Project Structure

```
agent_weather/
├── .venv/                    # Python virtual environment
├── .env                      # Environment variables (OPENAI_API_KEY, OPENAI_BASE_URL)
├── .gitignore                # Git ignore rules
├── README.md                 # Project readme
│
├── app.py                    # Entry point, login placeholder
├── weather_agent.py          # Core agent logic (run_agent, TOOL_DISPATCH)
├── weather_tool.py           # get_weather function
├── trip_plan_tool.py         # Trip planning tool (not used)
├── multi_tool_agent.py       # Alternative agent implementation
├── tools_schema.json         # Tool definitions for OpenAI SDK
├── f_sys_prompt.py           # System prompt generator (Jinja2)
├── utils.py                  # Utilities
│
├── templates/
│   └── agent_system.j2       # Jinja2 template for system prompt
│
├── kiro/                     # Kiro CLI documentation
│   └── steering/
│       ├── product.md        # Product documentation
│       ├── tech.md           # Technical documentation
│       └── structure.md      # This file
│
└── __pycache__/              # Python cache
```

## File Responsibilities

| File | Responsibility |
|------|----------------|
| app.py | Entry point, runs agent |
| weather_agent.py | Agent loop, tool dispatch, LLM calls |
| weather_tool.py | Weather query implementation |
| tools_schema.json | Tool schema definitions |
| f_sys_prompt.py | System prompt generation |
| templates/*.j2 | Jinja2 templates |

## Naming Conventions

- Snake_case for Python files: `weather_agent.py`, `weather_tool.py`
- Snake_case for functions: `run_agent()`, `get_weather()`
- PascalCase for classes (if any)
- Lowercase for env vars: `OPENAI_API_KEY`

## Code Style

- Type hints for function signatures
- Docstrings for public functions
- JSON for tool arguments/responses
- UTF-8 encoding for file operations

## Testing

- Test file: `test_call_llm_with_retry.py`
- Run with: `pytest` or `python -m pytest`