## 2024-02-15 - SSRF / Path Traversal in Proxy APIs
**Vulnerability:** User-controlled URL parameters were directly interpolated into fetch URLs without encoding.
**Learning:** Path parameters can be manipulated to change the API endpoint being accessed or inject arbitrary query parameters if not properly URI-encoded.
**Prevention:** Always use `encodeURIComponent` when interpolating variables into URL paths or `URLSearchParams` for query parameters in server-side proxies.
