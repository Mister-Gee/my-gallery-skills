---
name: file-generator
description: Generate and preview file content as CSV tables, JSON, plain text, HTML, SVG, Markdown, XML, or YAML. The LLM produces the content and the skill renders it in a syntax-highlighted viewer with a copy-to-clipboard button.
metadata:
  homepage: https://mister-gee.github.io/my-gallery-skills/file-generator/
---

# File Generator

Generates structured file content and renders it in an interactive viewer with syntax highlighting, CSV table rendering, SVG preview, and one-tap copy support. Works fully offline — no internet required.

## Prompts / Triggers
- "Generate a CSV with [data]"
- "Create a JSON config for [purpose]"
- "Write an HTML page about [topic]"
- "Make an SVG icon of [shape]"
- "Generate a text file with [content]"
- "Create a YAML config for [app]"
- "Export this data as a table"
- "Generate a [filetype] file"

## Instructions

Call the `run_js` tool with the following exact parameters:
- data: A JSON string with the following fields:
  - type: String. The file type. One of: "csv", "json", "txt", "html", "svg", "md", "xml", "yaml". Required.
  - content: String. The complete file content to generate. Required.
  - filename: String (optional). Suggested filename including extension (e.g. "data.csv"). Defaults to "file.<type>".
