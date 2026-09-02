# Gestalt LP — Design

## Objetivo

Landing page institucional do Gestalt ERP. Público amplo (marcenaria,
serralheria, marmoraria, comunicação visual, indústria de materiais
planos em geral, qualquer porte). CTA principal: agendar demonstração.
CTAs secundários: WhatsApp e formulário de contato (via Resend).

## Posicionamento

O Gestalt não deve parecer "mais um ERP genérico". A LP vende **controle
operacional** para indústrias que trabalham com material, produção e
rastreabilidade — não um cadastro financeiro/administrativo qualquer.

Narrativa: **dor → solução → produto → resultado → demonstração.**

## Estrutura da página (single-page, PT-BR)

1. **Navbar** — Logo Gestalt · Produto | Recursos | Como funciona | FAQ
   · botão "Agendar demonstração"
2. **Hero** — headline vendendo resultado, não a categoria de produto
   (ex. "Do estoque à produção. Tudo sob controle."). Subheadline
   explicando que é um ERP para marcenarias, marmorarias, serralherias,
   comunicação visual etc. CTA primário "Agendar demonstração" + CTA
   secundário "Falar pelo WhatsApp". **Mockup grande do sistema real**
   como elemento visual central — LP sem mostrar o produto perde força.
3. **Problema** — "Sua operação ainda depende de planilhas, papel e
   memória?" — 6 cards de dor: material perdido no estoque, retalhos
   esquecidos, dificuldade de rastrear material, retrabalho por falta
   de informação, relatórios manuais, tempo perdido procurando
   informação.
4. **Solução** — "Um único sistema para controlar toda a operação."
   Fluxo visual: Estoque → Produção → Rastreabilidade → Resultado.
5. **Módulos** — cada um como benefício, não como feature-list crua:
   - Estoque inteligente — saiba o que entrou, onde está, quanto pode
     ser usado
   - Gestão de retalhos — transforma sobras em estoque aproveitável
   - Rastreabilidade — origem e histórico do material na operação
   - Produção — o que está sendo produzido, por quem, em qual etapa
   - Relatórios
6. **Product showcase** — screenshots grandes do sistema, "Veja o
   Gestalt em ação"
7. **Segmentos** — "Feito para diferentes tipos de operação": Marmoraria
   · Marcenaria · Serralheria · Comunicação Visual · Indústria. Sem
   prova social falsa: nenhum logo placeholder. A única logo real
   disponível hoje entra à parte, em destaque próprio (não como fileira
   de marquee com placeholders) — a seção de prova social plena
   (marquee de clientes) fica para quando houver base suficiente.
8. **Por que Gestalt?** — "Mais que um ERP. Um sistema pensado para a
   operação." 4 diferenciais: construído para materiais reais (chapas,
   pedras, perfis, retalhos, peças, insumos), rastreabilidade de ponta
   a ponta, visão operacional em tempo real, menos desperdício.
9. **Como funciona** — "Da entrada à entrega": 1. Conheça sua operação
   2. Configure o Gestalt 3. Comece a controlar 4. Evolua sua operação.
10. **Planos** — "Uma solução que acompanha o tamanho da sua operação".
    3 cards sem preço fechado: Essencial, Profissional, Empresarial.
    CTA "Falar com um especialista" (evita reescrever a LP quando o
    modelo comercial mudar).
11. **FAQ**
12. **CTA final** — "Pronto para ter sua operação sob controle?" +
    botões Agendar demonstração / WhatsApp
13. **Footer** — Gestalt ERP, © 2026, Termos, Privacidade

## Direção visual

Herda os tokens do brand book do produto principal
(`../Gestalt/design-system/gestalt/MASTER.md`):

- `accent` `#256CEB` (light) — único acento de cor, sem inventar
  hexadecimais novos
- Tema claro
- Tipografia: Geist Sans (self-hosted, `@fontsource/geist-sans`), uma
  família só
- Ícones: Lucide exclusivamente
- Bordas finas 1px, `border-radius` na escala do brand book (4/8/12/16
  /24/32px)
- Sombras quase imperceptíveis, nunca pesadas

Diferença em relação ao produto: o app principal é "denso, ferramenta
operacional" (ver MASTER.md §7); a LP é o oposto disso — **muito espaço
em branco, tipografia grande, screenshots do produto como elemento
visual principal**. Referência: Linear + Vercel + "SaaS industrial".

### Proibido

- Gradientes grandes, blobs, glassmorphism
- Excesso de cards decorativos
- Stock photos de operários sorrindo
- Ícones gigantes coloridos fora do sistema Lucide
- Copy genérica tipo "revolucione sua empresa com nossa solução
  inovadora"
- Qualquer prova social inventada (logos placeholder de empresas que
  não existem)

## Stack de destino

React + Vite + TypeScript + Tailwind (mesma base do app principal
Gestalt), repositório `gestalt-lp`.

## Fluxo de trabalho

1. Prompt mestre para o Claude Design (skill `design`) — contexto de
   produto, posicionamento, arquitetura de página, direção visual,
   regras do que não fazer, comportamento responsivo — para gerar os
   artboards da LP.
2. Conversão do resultado do Claude Design para código via skill
   `design-to-code`, no scaffold React/Vite/TS/Tailwind deste
   repositório.

## Fora de escopo (por agora)

- Preço fechado nos planos
- Prova social em formato marquee/múltiplos logos (falta base de
  clientes)
- Integração de fato com Resend/WhatsApp (link/mailto/wa.me bastam
  nesta fase de LP estática)
