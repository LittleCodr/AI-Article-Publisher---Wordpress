# AI Article Generation

## How It Works

### 1. User Input
The user enters a topic or keyword in the input box and clicks **Generate Article**.  
The app captures the input and triggers the `generateArticle()` function.

### 2. Crafting the AI Prompt
The JavaScript builds a detailed prompt containing content rules and writing instructions, telling the AI model:

- What style to use (tone, word count, clickbait title, etc.)  
- What JSON format to return (title, focus keyword, meta description, content as valid HTML).

### 3. Sending to AI Model
The code calls the **Puter.ai** platform via:

```js
puter.ai.chat(prompt, { model: "gpt-4.1" }, { stream: true })
```

- This runs the prompt through an OpenAI-compatible model (likely GPT-4 or similar via Puter.ai’s API).  
- The `{ stream: true }` option gets the result as a stream for quicker, more interactive feedback.

### 4. Parsing the Response
Once the AI returns a response, the JavaScript:

- Checks if the response is JSON (and tries to parse it).  
- If parsing fails, it tries to extract the JSON object from the AI text.  
- Validates that fields like `title`, `meta_description`, and `content` exist.

### 5. Displaying the Article
If parsing is successful, the generated article is shown in the preview window with formatting and styled content.  

- The word count is calculated and displayed.

### 6. Error Handling
If anything fails (bad format, AI error, empty result), visible notifications inform the user.

---

## Tech Stack Used

| Layer            | Tool / Library         | Purpose |
|------------------|------------------------|---------|
| **Frontend UI**  | Tailwind CSS           | Utility-first CSS for responsive, modern UI |
| **JS Logic**     | Vanilla JavaScript     | State, events, user flows, data parsing |
| **AI Service**   | Puter.ai JavaScript SDK| Sends prompt to GPT-4 (via Puter.ai API) |
| **AI Model**     | GPT-4, GPT-4o          | Large Language Models from OpenAI (via Puter.ai) |
| **Storage**      | Local File System      | Saves project data locally as `.json` |
| **WordPress API**| REST API v2            | Publishes posts via `fetch`/XHR |
| **Other**        | CSV Handling, FileReader| Bulk article import |

- No backend/server used: It’s a **pure browser application**, talking directly to Puter.ai and WordPress.  
- No frameworks: **No React, Vue, Angular**. Just plain JS and Tailwind.

---

## Summary
AI Article Generation works by:

1. Collecting the keyword  
2. Sending a prompt to GPT-4 through Puter.ai’s SDK  
3. Strictly requiring valid JSON/HTML output from the model  
4. Parsing and displaying the output with custom formatting  

**Tech stack:** Tailwind CSS, Vanilla JavaScript, Puter.ai (GPT-4/GPT-4o), direct browser APIs (FileReader, fetch), WordPress REST API.
