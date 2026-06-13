# CLAUDE.md — Site B-Core Labs

> Este arquivo instrui o agente de implementação. Para regras de negócio, conteúdo e design system, consulte `SPEC_SITE.md`. Este arquivo responde *como* trabalhar, não *o quê* construir.

---

## Stack

- HTML + CSS + JS vanilla — arquivo único `index.html`
- Google Fonts: Syne, DM Sans, JetBrains Mono
- Sem frameworks, sem build step, sem dependências npm
- Deploy: GitHub Pages ou CDN estático

## Estrutura do Projeto

```
10-Projects/B-CORE/
  SPEC_SITE.md   ← fonte de verdade (conteúdo, design system, fixture)
  CLAUDE.md      ← este arquivo
  TASKS.md       ← checklist de implementação
  index.html     ← entregável final
```

## Regras Invioláveis

1. **Leia a SPEC antes de qualquer coisa.** Não assuma nada sobre cores, copy ou estrutura.
2. **Use EXATAMENTE o copy da fixture JSON.** Não reescreva headlines, não invente variações.
3. **Não altere o design system.** As CSS variables estão definidas na SPEC — não substitua por valores diferentes.
4. **Arquivo único.** Todo CSS e JS dentro do `index.html`. Sem arquivos externos além de Google Fonts.
5. **Não adicione seções fora do escopo.** A SPEC define exatamente as seções da v1.

## Design System (resumo — detalhes na SPEC)

```css
--color-bg:            #0D1117
--color-surface:       #161C26
--color-border:        #2A3040
--color-border-strong: #3A4A5C
--color-accent:        #2E8B84
--color-accent-light:  #4DB8B0
--color-accent-dark:   #1A5C5A
--color-text:          #E8EDF2
--color-muted:         #8A92A3
--color-development:   #D97B20
--color-roadmap:       #6B7280
```

Fontes: `Syne` (headlines), `DM Sans` (body), `JetBrains Mono` (terminal/dados).

## Padrões de Implementação

### Badges de status
```html
<!-- Disponível -->
<span class="badge badge-available">● Disponível</span>

<!-- Em desenvolvimento -->
<span class="badge badge-development">● Em desenvolvimento</span>

<!-- Roadmap -->
<span class="badge badge-roadmap">● Roadmap</span>
```

### Terminal do hero
- Fundo `#0D1117`, fonte `JetBrains Mono`
- Status OK → `--color-accent` (#2E8B84)
- Status WARN → `--color-development` (#D97B20)
- Cursor piscante no final

### Cards de produto
- Background: `--color-surface` (#161C26)
- Borda padrão: `1px solid var(--color-border)`
- Hover: `border-color → --color-accent`, `translateY(-2px)`
- Seções internas: label "DOR" e "SOLUÇÃO" em `--color-muted`, uppercase, font-size 11px

### Formulário de contato
- Campos: nome, empresa, cargo, email, produto de interesse (select)
- Submit → redireciona WhatsApp (link `https://wa.me/5519XXXXXXXXX`) ou Formspree
- Botão secundário separado para WhatsApp direto

## O que NÃO fazer

- Não usar `#00E5A0` — substituído por `#2E8B84`
- Não usar `#F5A623` — substituído por `#D97B20`
- Não usar `#111318` para cards — usar `#161C26`
- Não adicionar seções (blog, pricing, depoimentos) — fora do escopo v1
- Não usar Inter, Roboto ou Arial
- Não usar sombras pesadas (`box-shadow` apenas em focus rings)
- Não inventar copy — usar fixture da SPEC

## Checklist antes de entregar

- [ ] Passou pelo checklist de validação da SPEC
- [ ] Testou em 375px (mobile)
- [ ] Testou em 1280px (desktop)
- [ ] Todos os links/anchors funcionam
- [ ] Sem `console.error` no browser

