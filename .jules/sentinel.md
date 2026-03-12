## 2025-02-27 - [Information Disclosure] Prevent Leaking Stack Traces to Clients

**Vulnerability:** The API endpoint `api/groq-summarize.js` was returning the `error.stack` and specific internal error messages/types when an error occurred, leaking potentially sensitive backend implementation details.
**Learning:** Returning unhandled exception messages directly to clients provides attackers with context (like file paths, library versions, or logic details) that can be used for exploitation. It also exposes internal variable names.
**Prevention:** Always catch exceptions at API boundaries and map them to a generic error message (e.g., "An internal error occurred"). Log the full stack trace securely on the server side using `console.error` for debugging, but do not send it in the HTTP response body.
