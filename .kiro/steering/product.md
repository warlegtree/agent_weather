# Product Documentation

## Project Overview

**Weather Assistant Agent** - An AI-powered weather query agent that uses LLM (DeepSeek) to understand user intent and call tools to fetch weather information.

## Core Features

1. **Natural Language Interface**: Users can ask about weather in plain language
2. **Tool-Based Agent Loop**: Uses perception → decision → action → observation pattern
3. **Multi-City Support**: Currently supports Beijing, Shanghai, Guangzhou
4. **Date Flexibility**: Query "today" or "tomorrow" weather

## User Interactions

- Users send weather queries (e.g., "武汉明天天气怎么样？")
- Agent decides whether to call a tool or respond directly
- If tool needed, executes and returns results to LLM for final response

## Supported Queries

| Query Type | Example |
|------------|---------|
| Today's weather | "北京今天天气怎么样？" |
| Tomorrow's weather | "上海明天天气怎么样？" |
| Activity suggestion | "能出去玩吗？" (requires weather context) |

## Current Limitations

- Only supports 3 cities: 北京, 上海, 广州
- Only supports today and tomorrow dates
- Weather data is mock (not real API)

## Future Enhancements (indicated by README)

- Login feature (placeholder exists in app.py)
- Real weather API integration
- More cities and date ranges