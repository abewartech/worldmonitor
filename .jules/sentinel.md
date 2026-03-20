## 2024-03-20 - Prevent Info Leakage in API Errors
**Vulnerability:** Several API endpoints returned sensitive error details directly to the client when a 500 status code was encountered (e.g., `error.message`, `error.name` being sent back as JSON).
**Learning:** Exposing full error objects to external clients can inadvertently reveal system details, architecture, or internal logic.
**Prevention:** Catch blocks should return generic, safe error messages to clients (e.g., "Internal error", "Failed to process request") while logging full details internally using `console.error`.
