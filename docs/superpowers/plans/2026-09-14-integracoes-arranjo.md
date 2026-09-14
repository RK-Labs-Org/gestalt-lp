# Seção "Integrações" (arranjo de serviço) — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking. This plan is browser/design-tool driven, not a pytest-style codebase change — subagent-driven-development does not apply because the work depends on one continuous authenticated browser session in the Claude Design project.

**Goal:** Add a new "Integrações" section to the Gestalt LP (destaque Cypnest + grid genérico de outros softwares de arranjo), positioned after "Os módulos" and before "Veja o Gestalt em ação", without losing the hand-made loading-screen customization already living in `landing-standalone.html`.

**Architecture:** The LP's real source of truth is the Claude Design project ("Landing Gestalt ERP", `https://claude.ai/design/p/47837e2d-2e86-48a8-ab9d-14b06b3e2326`), a chat-driven canvas. Its "Download Landing Gestalt ERP (standalone)" export produces a single self-contained HTML file that gets checked in as `landing-standalone.html` (tracked in git; `dist/index.html` is a gitignored build copy Vercel creates via `cp landing-standalone.html dist/index.html`). Because `landing-standalone.html` was hand-edited afterward (loading-screen animation) outside the Design canvas, a fresh export must be reconciled with that hand-edit before it replaces the tracked file.

**Tech Stack:** Claude Design (canvas/export), static HTML/CSS/JS (no build step for the LP itself — `src/App.tsx`/Vite scaffold is unused placeholder).

## Global Constraints

- Accent color: `#256CEB` only, no new hex values (spec `2026-09-02-landing-page-design.md`)
- Icons: Lucide exclusively
- No invented software names/logos beyond **Cypnest** (spec `2026-09-14-integracoes-arranjo-design.md`)
- Cypnest card visually dominant; generic grid clearly subordinate
- New section sits after "Os módulos, pelo que eles resolvem." and before "Veja o Gestalt em ação"
- The loading-screen customization currently in `landing-standalone.html` (Gestalt logo + progress bar animation + 1.3s minimum display) must survive the re-export

---

### Task 1: Upload Cypnest asset and brief the Claude Design project

**Files:**
- Reference: `src/assets/brand/cypnest-logo.png` (already transparent-background, 1376×422px)
- Reference: `docs/superpowers/specs/2026-09-14-integracoes-arranjo-design.md` (full section spec)

**Interfaces:**
- Consumes: nothing from prior tasks (first task)
- Produces: a new/updated artboard page inside the Claude Design project reflecting the "Integrações" section, ready for visual review in Task 2

- [ ] **Step 1: Open the Claude Design project in the browser tab already navigated to it**

Tab is already at `https://claude.ai/design/p/47837e2d-2e86-48a8-ab9d-14b06b3e2326?file=Landing+Gestalt+ERP.dc.html&via=share`. Confirm the chat panel and "Describe what you want to create..." input are visible (see prior screenshot).

- [ ] **Step 2: Upload `src/assets/brand/cypnest-logo.png` as an attachment on the chat input**

Use the `+` button next to the chat input to attach the local file `src/assets/brand/cypnest-logo.png` so the Design project can reference the real Cypnest logo asset instead of inventing one.

- [ ] **Step 3: Send the section brief as a chat message**

Type and send this prompt (adapt only if the input has a hard length limit — keep all constraints):

```
Adicione uma nova seção "Integrações" na Landing Gestalt ERP, logo
após a seção "Os módulos, pelo que eles resolvem." e antes de "Veja
o Gestalt em ação".

Mensagem central: "Já usa um sistema de arranjo? O Gestalt entra no
seu fluxo." + subheadline curta reforçando que não é preciso trocar
de ferramenta.

Estrutura:
1. Card grande de destaque para o Cypnest (uso o logo anexado nesta
   mensagem, fundo transparente) — 1-2 frases curtas sobre a
   integração (sincronização de arranjos/agendamentos direto no
   Gestalt, sem retrabalho manual de reentrada de dados). Peso visual
   comparável a um card "hero" de módulo.
2. Abaixo, um grid pequeno e visualmente mais discreto com 3-5
   chips/ícones GENÉRICOS (não nomeados, ícones Lucide) representando
   "outros sistemas de arranjo de serviço do mercado" — sem inventar
   nomes ou logos de marcas específicas além do Cypnest.

Regras de marca: accent #256CEB único acento de cor, ícones Lucide
exclusivamente, tema claro, mesma tipografia (Geist Sans) e bordas/
sombras do resto da LP. Não usar gradientes grandes, blobs ou
glassmorphism. Não inventar prova social.
```

- [ ] **Step 4: Wait for generation to finish**

Poll with `mcp__claude-in-chrome__computer` (`action: "wait"`, 5-10s) then `action: "screenshot"` until the chat shows a completed response (no in-progress spinner) and the canvas on the right renders the updated page.

---

### Task 2: Visual review against spec

**Files:**
- Reference: `docs/superpowers/specs/2026-09-14-integracoes-arranjo-design.md`

**Interfaces:**
- Consumes: the artboard produced in Task 1
- Produces: an approved (or iterated-on) "Integrações" section ready to export in Task 3

- [ ] **Step 1: Screenshot the new section in the canvas**

`mcp__claude-in-chrome__computer` with `action: "screenshot"` on the design tab, scrolled to the new section (use `scroll` first if it's below the fold).

- [ ] **Step 2: Check against the spec's checklist**

Verify all of:
- Section sits between "Os módulos" and "Veja o Gestalt em ação"
- Cypnest card is visually dominant (larger/heavier) vs. the generic grid
- Generic grid has no specific brand names/logos other than Cypnest
- Only `#256CEB` used as accent color; icons are Lucide-style line icons
- No gradients/blobs/glassmorphism; copy isn't generic marketing fluff

- [ ] **Step 3: If any check fails, send a follow-up chat message describing the specific fix, then repeat Step 1**

Example follow-up pattern: `"O grid de outros softwares está competindo visualmente com o card do Cypnest — reduza o tamanho/peso dele para ficar claramente subordinado."` Only send fixes for checks that actually failed — don't re-request things already correct.

- [ ] **Step 4: Get explicit user sign-off on the screenshot before exporting**

Show the user the screenshot and wait for approval before moving to Task 3 — exporting locks in whatever is on the canvas.

---

### Task 3: Export standalone HTML and reconcile the loading-screen customization

**Files:**
- Modify: `landing-standalone.html` (repo root)
- Create (temporary): none tracked — downloaded file goes through the browser's download flow

**Interfaces:**
- Consumes: the approved artboard from Task 2
- Produces: an updated `landing-standalone.html` containing both the new "Integrações" section and the pre-existing loading-screen customization

- [ ] **Step 1: Click "Download Landing Gestalt ERP (standalone)" in the Design project chat**

Use `mcp__claude-in-chrome__computer` `left_click` on that button (visible in the left chat panel, as seen in the initial screenshot). Note the downloaded file's path reported by Chrome (typically `~/Downloads/Landing Gestalt ERP.html` or similar).

- [ ] **Step 2: Back up the current tracked file before touching it**

```bash
cp landing-standalone.html /tmp/landing-standalone.pre-integracoes.html
```

- [ ] **Step 3: Confirm the new export lost the loading-screen customization**

```bash
grep -c '__bundler_bar' "<path to downloaded file>"
```

Expected: `0` (the fresh export ships the Design bundler's default thumbnail, not the hand-made progress-bar version) — this confirms reconciliation is needed, not optional.

- [ ] **Step 4: Reapply the loading-screen customization onto the freshly downloaded file**

Two edits, using the exact same changes already proven to work in `landing-standalone.html` (from commits `d69d79e`, `9eab33d`, `ba6b2a0`, `56bccaf`):

In the `<style>` block, replace the default `#__bundler_thumbnail` rules with:

```css
#__bundler_thumbnail { position: fixed; inset: 0; width: 100%; height: 100%; display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 20px; background: #FAFAFA; z-index: 9999; }
#__bundler_thumbnail img { width: 180px; height: auto; animation: __bundler_pulse 1.1s ease-in-out infinite; }
#__bundler_bar { width: 120px; height: 4px; border-radius: 4px; background: #ede6ff; overflow: hidden; }
#__bundler_bar::after { content: ''; display: block; width: 40%; height: 100%; border-radius: 4px; background: #7e14ff; animation: __bundler_bar_slide 1.1s ease-in-out infinite; }
#__bundler_placeholder { color: #999; font-size: 14px; }
@keyframes __bundler_pulse {
  0%, 100% { opacity: 0.5; transform: scale(0.94); }
  50% { opacity: 1; transform: scale(1); }
}
@keyframes __bundler_bar_slide {
  0% { transform: translateX(-120%); }
  100% { transform: translateX(300%); }
}
```

Replace the default `<div id="__bundler_thumbnail">...<svg>...</svg></div>` markup with the logo-based version — reuse the exact `<img src="data:image/png;base64,...">` element already present in the backed-up `/tmp/landing-standalone.pre-integracoes.html` (extract it with `grep -o '<div id="__bundler_thumbnail">.*</div>' /tmp/landing-standalone.pre-integracoes.html`, since the base64 payload is long and must be copied verbatim, not retyped) plus the `<div id="__bundler_bar"></div>` sibling element.

In the loading `<script>` block, right before `document.documentElement.replaceWith(doc.documentElement);`, ensure this minimum-display-time gate is present (copy verbatim from the backup if the export's script structure otherwise matches):

```js
  const __elapsed = Date.now() - __loadStart;
  if (__elapsed < __MIN_LOADING_MS) {
    await new Promise(function(r) { setTimeout(r, __MIN_LOADING_MS - __elapsed); });
  }
```

...and near the top of the `DOMContentLoaded` handler:

```js
  const __loadStart = Date.now();
  const __MIN_LOADING_MS = 1300;
```

- [ ] **Step 5: Move the reconciled file into place**

```bash
cp "<path to downloaded+reconciled file>" landing-standalone.html
```

- [ ] **Step 6: Verify the reconciliation landed**

```bash
grep -c '__bundler_bar' landing-standalone.html
grep -c '__MIN_LOADING_MS' landing-standalone.html
```

Expected: both `> 0`.

---

### Task 4: Build, visually verify in the real app, and commit

**Files:**
- Modify: `landing-standalone.html` (already updated in Task 3)
- No other files change

**Interfaces:**
- Consumes: the reconciled `landing-standalone.html` from Task 3
- Produces: a committed, working LP with the new section live

- [ ] **Step 1: Serve the file locally**

```bash
cd /Users/rianrapkievicz/dev/gestalt-lp && python3 -m http.server 8123 &
```

- [ ] **Step 2: Open it in the browser and confirm it loads past the loading screen**

`mcp__claude-in-chrome__navigate` to `http://localhost:8123/landing-standalone.html`, then screenshot after a few seconds — confirm the loading screen (logo + progress bar) appears briefly and the full page renders after.

- [ ] **Step 3: Scroll to and screenshot the new "Integrações" section**

Confirm visually it matches what was approved in Task 2 (position, Cypnest card dominance, generic grid subordination).

- [ ] **Step 4: Stop the local server**

```bash
kill %1
```

- [ ] **Step 5: Stage and commit**

```bash
git add landing-standalone.html src/assets/brand/cypnest-logo.png
git commit -m "$(cat <<'EOF'
feat: adiciona seção de integrações com softwares de arranjo

Nova seção "Já usa um sistema de arranjo? O Gestalt entra no seu
fluxo." entre Módulos e o showcase do produto, com destaque para a
integração real com Cypnest e um grid genérico para os demais
softwares de arranjo do mercado (docs/superpowers/specs/2026-09-14-integracoes-arranjo-design.md).

Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_013FAoyd6jzFDhH2ckZ1wABr
EOF
)"
```

- [ ] **Step 6: Confirm clean status**

```bash
git status
```

Expected: working tree clean, new commit present in `git log -1`.
