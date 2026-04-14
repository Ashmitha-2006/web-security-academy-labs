# PortSwigger Web Security Academy — Lab Writeups

A collection of professional writeups for completed PortSwigger Web Security Academy labs, covering vulnerability analysis, step-by-step exploitation, root cause analysis, and remediation guidance.

---

## Labs Completed

| # | Lab | Category | Difficulty | Status |
|---|-----|----------|------------|--------|
| 1 | [URL-Based Access Control Bypass](./url_access_control/README.md) | Access Control | Practitioner | ✅ Solved |
| 2 | [IDOR — User ID with Password Disclosure](./idor/README.md) | Access Control / IDOR | Apprentice | ✅ Solved |
| 3 | [DOM XSS via `document.write` + `location.search`](./dom_xss/README.md) | XSS — DOM-Based | Practitioner | ✅ Solved |
| 4 | [Reflected XSS — WAF Bypass](./reflected_xss/README.md) | XSS — Reflected | Practitioner | ✅ Solved |
| 5 | [Stored XSS — Nothing Encoded](./stored_xss/README.md) | XSS — Stored | Apprentice | ✅ Solved |

---

## Vulnerability Summary

### 🔐 Access Control
- **URL-Based Access Control Bypass** — Front-end proxy blocked `/admin` by URL path, but the back-end honoured the `X-Original-URL` header, allowing full bypass via header injection.
- **IDOR + Password Disclosure** — User account data controlled by an unvalidated `id` parameter, with plaintext passwords exposed directly in the HTML response.

### ⚡ Cross-Site Scripting (XSS)
- **DOM XSS** — `document.write` sink fed by `location.search` with no sanitization; payload breaks out of `<select>` context to execute `alert(1)`.
- **Reflected XSS (WAF Bypass)** — WAF blocks common tags/attributes; bypass achieved by enumerating allowed tags (`<body>`) and event handlers (`onresize`) via Burp Intruder, then using a zero-interaction iframe-resize delivery chain.
- **Stored XSS** — Comment input stored and rendered with no output encoding; persistent `<script>` payload fires for every visitor.

---

## Tools Used

- **Burp Suite** — Proxy, Repeater, Intruder, Exploit Server
- **Browser DevTools** — DOM inspection and source analysis
- **PortSwigger Web Security Academy** — Lab environment

---

## OWASP Top 10 Mapping

| Lab | OWASP Top 10 (2021) |
|-----|---------------------|
| URL-Based Access Control Bypass | A01 — Broken Access Control |
| IDOR + Password Disclosure | A01 — Broken Access Control / A02 — Cryptographic Failures |
| DOM XSS | A03 — Injection |
| Reflected XSS (WAF Bypass) | A03 — Injection |
| Stored XSS | A03 — Injection |

---

*All labs completed on PortSwigger Web Security Academy for educational purposes.*
