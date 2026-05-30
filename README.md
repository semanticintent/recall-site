# recall-site

Documentation site for [RECALL](https://github.com/semanticintent/recall-compiler) — a COBOL-inspired publishing language for the web.

**Live:** [recall.semanticintent.dev](https://recall.semanticintent.dev)

---

## What this is

The docs site is itself written in RECALL. Every page is a `.rcl` source file compiled to self-contained HTML by `@semanticintent/recall-compiler`. The site builds with one command and deploys to Cloudflare Pages on push to `main`.

```
src/
├── index.rcl        — home page
├── docs.rcl         — language reference
├── examples.rcl     — annotated examples
├── pipeline.rcl     — AI pipeline / Common Record Description
├── changelog.rcl    — release history
├── legal.rcl        — terms and privacy
├── components/      — shared .rcpy copybooks (nav, footer)
└── theme.rcpy       — site-wide palette and fonts

static/
├── playground.html  — live RECALL playground (with WITH INTENT expand)
└── _redirects       — CF Pages routing rules
```

---

## Local development

```sh
npm install
npm run build       # compiles all .rcl → public/
```

Open any file in `public/` directly in a browser, or use `recall serve` for hot reload:

```sh
npx recall serve src/index.rcl
```

---

## Deploy

Cloudflare Pages auto-deploys on push to `main`. The build command is:

```sh
recall build src/ --out public/ && cp static/_redirects public/_redirects && cp static/playground.html public/playground.html
```

---

## Dependencies

| Package | Role |
|---|---|
| `@semanticintent/recall-compiler` | Compiles `.rcl` source to HTML |

No other runtime dependencies. The compiler is a zero-dep CLI.

---

## Related

- [recall-compiler](https://github.com/semanticintent/recall-compiler) — the compiler and CLI
- [recall-ui](https://github.com/semanticintent/recall-ui) — standard component library
- [`@semanticintent/recall-compiler`](https://www.npmjs.com/package/@semanticintent/recall-compiler) — npm package
- [RECALL Language extension](https://marketplace.visualstudio.com/items?itemName=semanticintent.recall-language) — VS Code syntax highlighting
