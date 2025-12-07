# Architecture & Schema

## Architecture

The `manager` library follows a simple, modular architecture:

- **Manager Class**: Core logic for template rendering and validation.
- **CLI Module**: Command-line interface for payload generation.
- **Templates**: Jinja2 templates for JSON output.
- **Tests**: Unit tests for validation and rendering.

```
[CLI] --> [Manager] --> [Templates] --> JSON Payload
              |
              v
          [Validators]
```

## JSON Schema

The generated payloads conform to this schema (based on xAI API):

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "model": {
      "type": "string",
      "description": "The AI model name"
    },
    "messages": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "role": {
            "type": "string",
            "enum": ["system", "user", "assistant"]
          },
          "content": {
            "type": "string"
          }
        },
        "required": ["role", "content"]
      }
    },
    "tools": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "type": {
            "type": "string"
          },
          "name": {
            "type": "string"
          }
        },
        "required": ["type", "name"]
      }
    },
    "temperature": {
      "type": "number",
      "minimum": 0,
      "maximum": 2
    },
    "max_tokens": {
      "type": "integer",
      "minimum": 1
    },
    "stream": {
      "type": "boolean"
    }
  },
  "required": ["model", "messages", "tools"]
}
```
