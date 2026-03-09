## 2025-01-20 - Leaked Stack Traces and Error Details in Groq Summarize API
**Vulnerability:** The API endpoints (`api/groq-summarize.js` and `api/openrouter-summarize.js`) leaked stack traces (`error.stack?.split('\n')[1]`) to console logs and internal error details (`error.message`, `error.name`) in public-facing JSON responses.
**Learning:** Returning exception object properties blindly in catch blocks is a common anti-pattern that exposes internal infrastructure, paths, execution state, and potential downstream dependency vulnerabilities to external users.
**Prevention:** Always log specific error details internally (via console.error or a logging service) but return generic error messages like "Internal server error" for 500 status codes in API responses.
