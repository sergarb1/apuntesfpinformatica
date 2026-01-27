<!-- headroom:rtk-instructions -->
# RTK (Rust Token Killer) - Token-Optimized Commands

When running shell commands, **always prefix with `rtk`**. This reduces context
usage by 60-90% with zero behavior change. If rtk has no filter for a command,
it passes through unchanged — so it is always safe to use.

## Key Commands
```bash
# Git (59-80% savings)
rtk git status          rtk git diff            rtk git log

# Files & Search (60-75% savings)
rtk ls <path>           rtk read <file>         rtk grep <pattern>
rtk find <pattern>      rtk diff <file>

# Test (90-99% savings) — shows failures only
rtk pytest tests/       rtk cargo test          rtk test <cmd>

# Build & Lint (80-90% savings) — shows errors only
rtk tsc                 rtk lint                rtk cargo build
rtk prettier --check    rtk mypy                rtk ruff check

# Analysis (70-90% savings)
rtk err <cmd>           rtk log <file>          rtk json <file>
rtk summary <cmd>       rtk deps                rtk env

# GitHub (26-87% savings)
rtk gh pr view <n>      rtk gh run list         rtk gh issue list

# Infrastructure (85% savings)
rtk docker ps           rtk kubectl get         rtk docker logs <c>

# Package managers (70-90% savings)
rtk pip list            rtk pnpm install        rtk npm run <script>
```

## Rules
- In command chains, prefix each segment: `rtk git add . && rtk git commit -m "msg"`
- For debugging, use raw command without rtk prefix
- `rtk proxy <cmd>` runs command without filtering but tracks usage
<!-- /headroom:rtk-instructions -->

<!-- headroom:project-instructions -->
# Apuntes FP Informática - Project Guide

## URLs
- **Official**: https://apuntesfpinformatica.es
- **GitHub Pages**: https://sergarb1.github.io/apuntesfpinformatica/

## Structure
- `index.html` — Vue 3 SPA (CDN) + Tailwind CSS + Lucide Icons
- `recursos.json` — Resource database (array of JSON objects)
- `logo.png` — Site logo
- `README.md` — Documentation
- `AGENTS.md` — AI agent instructions

## Common Tasks

### Add a new resource
Edit `recursos.json` and append a new object before the closing `]`. Each resource has: Título, URL, Descripción, Autor, Github, Twitter, Licencia, Etiquetas, FechaPublicacion, Modulos.

### Edit UI
Edit `index.html`. Vue 3 app is in a `<script>` block at the bottom (lines 237-489).

### Deploy
Push to `main` — GitHub Actions deploys to both URLs automatically.

## Tagging conventions
- Etiquetas format: `{MODULO}-{TIPO}` (e.g. `PRG-APUNTES`)
- Tipos: APUNTES, APUNTES-OTROS, RECURSOS, CHEATSHEETS, JUEGOS, RETOS, CURSOS, LIBROS, JUECES
- Special types: MAQUINAS-Y-CONTENEDORES, APIS-PUBLICAS, ESPECIALIZACION-SEGURIDAD-RECURSOS

## Gitignore notes
- `*.js` is ignored (everything comes from CDN)
- Exception: `!recursos.json`
- `.codegraph/` and `.serena/` are ignored (local tool configs)
<!-- /headroom:project-instructions -->
