# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Developer portal ("Portal do Desenvolvedor") for **VerificaIdade** — age verification (18+) using **INJI Verify**. Static documentation site built with **Quarto**, written entirely in Portuguese (pt-BR).

The integration architecture is:

- **INJI Verify SDK** (`@mosip/react-inji-verify-sdk`) — React NPM package with embeddable verification components
- **INJI Verify Service** — Java/Spring Boot backend deployed via Docker on the verifier's VM, with PostgreSQL
- No custom backend is needed to orchestrate verification; the SDK talks directly to the Service

## Build Commands

```bash
quarto render          # Generate HTML in docs/
quarto preview         # Preview with live reload
```

Output goes to `docs/` for GitHub Pages deployment.

## Architecture

- **Quarto static site** — no backend, no JS framework
- **`_quarto.yml`** — main project config (site structure, theme, sidebar nav with sections)
- **`.qmd` files** (root) — documentation pages in Quarto Markdown with Mermaid diagrams
- **`docs/`** — generated output (committed for GitHub Pages)
- **Theme**: Cosmo + `styles.css` for custom overrides

## Content Structure

Pages organized in sections: Início Rápido (arquitetura, quickstart), Infraestrutura (setup-vm, inji-verify), Integração (fluxo-verificacao, integra-web, integra-mobile), Referência (policy18, seguranca-lgpd, producao, api-reference, troubleshooting, onboarding).

## Conventions

- All content in **Portuguese (pt-BR)**
- Site structure defined in `_quarto.yml` under `website.sidebar.contents`
- Adding a page: create `.qmd` file + add to sidebar in `_quarto.yml`
- After changes: `quarto render` and commit both source and `docs/`
- Code examples use **React/TypeScript** (frontend with SDK), **Node/Express** (optional backend for production security)
- INJI Verify Service deployed via **Docker Compose** (Spring Boot + PostgreSQL)
- Use Quarto callouts (`.callout-note`, `.callout-warning`, `.callout-important`)
- Use Mermaid diagrams for architecture and flow visualizations
- Placeholders: `<VERIFY_BASE_URL>`, `<SEU_DOMINIO>`
