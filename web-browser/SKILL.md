---
name: web-browser
description: Open an in-app web browser to navigate, surf the internet, and browse any website by URL or search query.
metadata:
  homepage: https://mister-gee.github.io/edge-gallery-skills/web-browser/
---

# Web Browser

An in-app web browser with an address bar, back/forward/reload/home navigation, and the ability to browse any URL or perform a Google search directly in the chat.

## Prompts / Triggers
- "Browse to [url]"
- "Open [website] in the browser"
- "Search the web for [query]"
- "Go to [url]"
- "Navigate to [website]"
- "Open a web browser"
- "Surf the internet"
- "Open browser and search for [topic]"
- "Show me [website]"

## Instructions

Call the `run_js` tool with the following exact parameters:
- data: A JSON string with the following fields:
  - url: String (optional). The full URL to open. If the user provides a bare domain (e.g. "github.com"), prepend "https://". Defaults to "https://www.google.com".
  - query: String (optional). A search query. If provided and no URL given, use: https://www.google.com/search?q=<encoded_query>
