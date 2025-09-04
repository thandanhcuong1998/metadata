# Oncosoft Frontend Code Rules (Svelte 5 + TypeScript)
# Project: onco-rpt-frontend

---
## 1) Project Structure

* [cite_start]**SG-001 (MUST):** Follow this layout: `src/{lib/{components,utils,apis,stores},routes}/`. 
* **SG-002 (SHOULD):** One component per file. [cite_start]Place tests (`*.test.ts`) alongside the component. 
* **SG-003 (MUST):** Public APIs in `src/lib/**` must be stable and typed. [cite_start]Avoid deep imports. 

---
## 2) Naming & Files

* **SG-010 (MUST):** Naming conventions: PascalCase for Components & Types; camelCase for utilities & stores; [cite_start]UPPER_SNAKE_CASE for constants. 
* [cite_start]**SG-011 (MUST):** Use correct file suffixes: `.svelte`, `.store.ts`, `.service.ts`, `.utils.ts`. 

---
## 3) Svelte Component Conventions

* **SG-020 (MUST):** Use `<script lang="ts">`. [cite_start]Ordering: imports → props → state → derived → effects → functions. 
* [cite_start]**SG-021 (MUST):** Define props with an `interface`. 
* **SG-030 (MUST):** Props are immutable. [cite_start]Communicate upwards via typed events only. 
* **SG-040 (MUST):** Prefer `$derived` over `$effect`. [cite_start]Keep effects pure. [cite: 1, 1]
* **SG-050 (MUST):** All interactive elements MUST be accessible (a11y), including keyboard operability. [cite_start]Use `aria-*` attributes where needed. [cite: 1, 1, 1]

---
## 4) State Management

* [cite_start]**SG-060 (MUST):** Use Svelte stores for shared state. 
* [cite_start]**SG-062 (MUST):** Avoid global singletons for ephemeral (temporary) state. 

---
## 5) Data & API Layer

* **SG-070 (MUST):** All HTTP calls MUST be placed in `lib/apis/*.ts`. [cite_start]No `fetch` inside `.svelte` files. 
* [cite_start]**SG-071 (MUST):** Define explicit request/response types for all API calls. 

---
## 6) Styling

* [cite_start]**SG-080 (MUST):** Use scoped `<style>` or global styles in `static/css/`. 
* [cite_start]**SG-085 (MUST):** Icon colors must be changed via `currentColor` and CSS variables only. 

---
## 7) Performance

* [cite_start]**SG-090 (MUST):** No blocking work in top-level script scope. 
* [cite_start]**SG-091 (MUST):** Always provide keys in `{#each}` blocks. 
* [cite_start]**SG-092 (SHOULD):** Lazy-load large, rarely used components. 

---
## 8) Security & Privacy

* [cite_start]**SG-100 (MUST):** DO NOT log Protected Health Information (PHI) or Personally Identifiable Information (PII). 
* [cite_start]**SG-101 (MUST):** All user-generated input MUST be escaped/encoded before rendering. 
* [cite_start]**SG-102 (MUST):** Use secure cookies (`HttpOnly`, `Secure`) and CSRF protection. 

---
## 9) Testing

* [cite_start]**SG-110 (MUST):** Write unit tests with Vitest + Testing Library. 
* [cite_start]**SG-112 (MUST):** Tests must follow the Arrange-Act-Assert pattern. 

---
## 10) SvelteKit Usage

* [cite_start]**SG-200 (SHOULD):** Use SvelteKit’s standard routing, endpoints, and form actions. 
* [cite_start]**SG-202 (SHOULD):** Separate server code into `+page.server.ts` and client code into `+page.svelte`.

## 20) Metadata Files

* **SG-300 (MUST):** The root of a `.json` file MUST contain a `version` key.
* **SG-301 (MUST):** The value of the `version` key MUST follow Semantic Versioning format (e.g., "1.0.0", "2.1.5", "1.0.0-beta.1"). Non-compliant values like "latest" or "v1" are forbidden.
* **SG-302 (MUST):** Files MUST NOT contain hardcoded secrets, API keys, or passwords. Use environment variables or a secrets management service instead.