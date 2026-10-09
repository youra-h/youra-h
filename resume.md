# Yuri Soldatov — Senior Frontend / Fullstack Developer

TypeScript · React · Vue 3 · headless UI components · accessibility · 18 years in software development, 7+ in modern web.

- GitHub: [github.com/youra-h](https://github.com/youra-h)
- Featured project: [github.com/youra-h/soldy](https://github.com/youra-h/soldy)
- Email: manandship@gmail.com
- Location / time zone: Orenburg, Russia — UTC+5 (Yekaterinburg Time, YEKT), no daylight saving; open to remote work
- Languages: Russian (native); English — confident reading of technical docs and code, written and spoken communication mostly with the help of a translator.

## Featured project: soldy

[soldy](https://github.com/youra-h/soldy) is an open-source headless UI component framework: component behavior and WAI-ARIA semantics are written once in a framework-agnostic TypeScript core, and each UI framework gets a thin adapter. Author and architect; ~1,400 commits, ~590 test files.

**Stack:** TypeScript, React, Vue 3, Angular, Svelte, Solid, Web Components, Vite, Vitest, Playwright, Tailwind (theme package), ESLint, changesets, GitHub Actions.

**What I designed and built**

- **Layered architecture.** `core` (headless models) → `plugins` (DOM and lifecycle behavior) → `setup` (shared component descriptors and wiring) → `ui/*` adapters. Framework imports are allowed only in adapters, enforced by ESLint rules and tests.
- **Components:** Button, Input, Checkbox, Switch, RadioGroup, Tabs, Accordion, ListBox, Select, Tags, Slider, Popover, Tooltip, Dialog, Drawer, Calendar, DatePicker, Table and more, with compound parts (`Tabs.Item`, `Tabs.Content`).
- **Collection engine:** one engine for every list-like component, with pluggable extensions for selection, activation, ordering and drag-and-drop, plus facades that expose them to components.
- **Accessibility:** WAI-ARIA patterns, keyboard navigation, focus management, accessible names; ids built from the mount, so markup is SSR-safe.
- **Overlays:** layering, anchoring, dismiss on outside click, focus trap and scroll lock, shared by Select, Popover, Dialog and Drawer.
- **Theming:** components emit BEM classes and `data-*` attributes only; the theme is a separate package. Localization through a subtree locale provider; motion follows `prefers-reduced-motion`.
- **Quality gates in CI:** type checks per package (including Angular `ngc` with strict templates), lint rules that forbid type casts, real-browser layout tests in Chromium, and a check that published packages declare everything they import.
- **AI-agent development workflow:** analyst, tech lead, developer and designer agents work through a task board with strict project instructions ([AGENTS.md](https://github.com/youra-h/soldy/blob/main/AGENTS.md)).

**Code to look at**

| What | Link |
| --- | --- |
| Architecture overview | [docs/architecture.md](https://github.com/youra-h/soldy/blob/main/docs/architecture.md) |
| Headless core | [packages/core](https://github.com/youra-h/soldy/tree/main/packages/core) |
| Behavior plugins (dismiss, overlay, table, select…) | [packages/plugins/src/custom](https://github.com/youra-h/soldy/tree/main/packages/plugins/src/custom) |
| React adapter | [packages/ui/react](https://github.com/youra-h/soldy/tree/main/packages/ui/react) |
| Vue adapter | [packages/ui/vue](https://github.com/youra-h/soldy/tree/main/packages/ui/vue) |
| Table benchmark | [BENCHMARKS.md](https://github.com/youra-h/soldy/blob/main/BENCHMARKS.md), [tools/bench-table](https://github.com/youra-h/soldy/tree/main/tools/bench-table) |

## Table benchmark: 5,000 rows × 20 columns

soldy's Table now leads every Vue component library on render, memory, selection, sorting and data replacement; headless baselines without keyboard, ARIA or column resize stay lighter. In one day of profiling, first render went from 2.9 s to 1.58 s, memory from 729 MB to 288 MB and select-all from 1.7 s to 0.62 s. I built the [benchmark harness](https://github.com/youra-h/soldy/tree/main/tools/bench-table) myself (Vite + Playwright) to find bottlenecks, and every optimization is logged in [BENCHMARKS.md](https://github.com/youra-h/soldy/blob/main/BENCHMARKS.md).

Method: Vue 3.5, production build, Chromium, median of 3 runs, real DOM clicks, time measured until frames settle. Memory is the JS heap after render. Virtualization off; every run is verified (5,000 → 0 selected rows, correct sort order).

**soldy vs Vue component libraries**

| Metric | soldy | Naive UI 2.45 | Element Plus 2.14 | PrimeVue 5.0 |
| --- | --- | --- | --- | --- |
| First render | **1.58 s** | 2.45 s | 9.1 s | 24.9 s |
| Memory (JS) | **288 MB** | 409 MB | 580 MB | 2.8 GB |
| Select all | **0.62 s** | 2.84 s | 41 s | 11.8 s |
| Clear selection | **0.54 s** | 2.92 s | 43 s | 11.7 s |
| Sort | **0.96 s** | 2.28 s | 91 s | 10.7 s |
| Replace data | **2.35 s** | 5.65 s | 60 s | 11.8 s |
| Unmount | 0.31 s | **0.27 s** | 0.56 s | 12.2 s |
| DOM nodes | **125k** | 145k | 235k | 130k |

**soldy vs plain Vue and headless baselines**

Baselines, not finished components: no keyboard, ARIA, column resize or reordering — only what the bench measures.

| Metric | Plain Vue | TanStack Table 9 | TanStack + Reka UI | soldy |
| --- | --- | --- | --- | --- |
| First render | 0.77 s | 0.76 s | 1.09 s | 1.58 s |
| Memory (JS) | 27 MB | 39 MB | 145 MB | 288 MB |
| Select all | 0.09 s | 0.08 s | 1.43 s | 0.62 s |
| Clear selection | 0.08 s | 0.08 s | 1.54 s | 0.54 s |
| Sort | 0.73 s | 0.74 s | 0.58 s | 0.96 s |
| Replace data | 0.84 s | 1.01 s | 0.81 s | 2.35 s |

With the optional virtualized mode, first render drops to 0.10 s and memory to 19 MB; scrolling through all rows takes 4.2 s vs 7.4 s for Naive UI and 27.3 s for PrimeVue.

## Experience

**Senior Frontend Developer — Muvi LLC** · May 2025 – present

Nuxt, Vue 3, Pinia, Tailwind, Python / FastAPI, PostgreSQL, video streaming.

- Took over a Nuxt video client with home-made state and caching that caused unpredictable bugs and blocked framework upgrades; initiated and led a rewrite on a new stack.
- Introduced Pinia and a single API layer through the Nuxt server, with centralized request and error handling on client and server.
- Built the user account, camera pages and a live-stream video player.
- Ad detection platform for TV streams: SCTE-35 parsing from UDP multicast, scene detection with OpenCV, an ML pipeline (CLIP embeddings + FAISS similarity search + XGBoost scoring), real-time delivery via PostgreSQL NOTIFY/LISTEN and SSE.

**Senior Fullstack Developer — Bortsov.Group LLC** · Apr 2023 – May 2025

Cloud accounting product. TypeScript, Vue 3, AngularJS, PHP 7–8 (Yii), PostgreSQL, Redis, Docker.

- Initiated the new client app: compared stacks, the team chose Vue 3 + Vite + Tailwind; designed the app architecture (routing, Pinia, API layer, modules).
- Designed and built the in-house UI component library: forms, tables, modals, notifications, navigation.
- Automated form generation during a core refactor: fewer bugs, faster delivery of new forms; removed 30–90% of code in several modules.
- Optimized the heaviest SQL query from 6 s to 0.6 s; added client-side caching that cut database requests.
- Built a Vue tool that consolidated 200+ hard-coded CSS colors into a manageable palette; moved the team to Docker for local development; introduced Microsoft Copilot into internal processes; code reviews.

**Fullstack Developer — freelance and contract work** · Feb 2019 – May 2023

- Contributed to UI components built on Google Material Design Components (TypeScript, SCSS, webpack).
- Admin panels and features in Vue + TypeScript, browser extensions, Telegram bots, a large-scale web scraper.

**Earlier experience** · 2008 – 2019

| Years | Company | Role | Highlights |
| --- | --- | --- | --- |
| 2013 – 2019 | ActivBusinessCollection LLC | Lead Developer | Designed the in-house framework and UI components for a modular debt-collection system (Delphi XE5, MS SQL), later extended at Sberbank; full-stack web platform for a betting company (PHP, Yii2, MySQL, Memcached) |
| 2011 – 2013 | Genes1s Intellectual Solutions LLC | Lead Developer | Led a team of 4 building a utilities CRM (Delphi, MS SQL); built its component framework on the Windows API and VCL and set the design and data-access standards; CRM for betting (PHP, ExtJS, MySQL); led 2–3 devs on e-commerce sites |
| 2010 – 2011 | EtAp LLC | Developer | Web client for remote staff access (PHP, jQuery, MS SQL); auto-dialer server for Asterisk |
| 2008 – 2010 | Hospital and 1C integrators | Software Engineer | Hospital admission and registry systems (Delphi, MS SQL); 1C:Enterprise configurations |

## Education

- **Orenburg State University** — Software Engineer, 2009. Diploma with honors (red diploma, highest grades).
- **College of Electronics and Business, Orenburg State University** — Technician Programmer, 2005.

## Skills

| Area | Tools |
| --- | --- |
| Languages | TypeScript, JavaScript, Python, PHP, SQL |
| UI frameworks | React, Vue 3, Nuxt, Angular, Svelte, Solid, Web Components |
| Component design | headless primitives, compound components, WAI-ARIA, keyboard and focus management, theming, i18n |
| Tooling | Vite, Vitest, Playwright, ESLint, changesets, Docker, GitHub Actions, Bitbucket |
| Backend and data | FastAPI, Yii, PostgreSQL, Redis, REST integrations, SSE |
| AI | multi-agent dev workflows with Claude, Copilot; CLIP, FAISS, XGBoost |
