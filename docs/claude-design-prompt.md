# Prompt mestre — Landing page Gestalt ERP (Claude Design)

Use este prompt inteiro como entrada única no Claude Design (skill
`design`). Não resuma nem simplifique antes de colar — cada seção existe
pra impedir que o resultado saia como "LP de SaaS genérica".

---

## 1. Contexto do produto

Gestalt é um ERP desktop (Electron) de gestão de estoque industrial para
indústrias de **materiais planos**: marcenarias, marmorarias,
serralherias, comunicação visual e indústria em geral. Ele controla
chapas, retalhos, certificados de rastreabilidade, entradas/saídas de
estoque, produção e relatórios.

**Não trate isso como "mais um ERP".** O produto resolve um problema
muito específico: essas operações trabalham com material físico que se
perde, se esquece em forma de retalho, ou vira retrabalho porque ninguém
sabe a origem/quantidade certa. Gestalt existe para dar controle
operacional sobre material + produção + rastreabilidade — não é um
módulo financeiro/administrativo genérico com um nome bonito.

## 2. Posicionamento e narrativa

A página inteira segue a narrativa: **dor → solução → produto →
resultado → demonstração.**

Headline de referência (pode refinar, mas mantenha o espírito — vender o
resultado, não a categoria de produto):

> Do estoque à produção. Tudo sob controle.

Nunca abra vendendo "ERP" como conceito. Explique que é um ERP para o
setor **depois** de mostrar o resultado que ele entrega.

## 3. Público

Amplo, sem segmentar por porte: donos e gestores de marcenaria,
marmoraria, serralheria, comunicação visual, indústria — de operações
pequenas a médias/grandes. A copy não deve soar nem "startup enxuta" nem
"software corporativo pesado" — precisão e controle, sem jargão de
vendas.

## 4. Arquitetura da página (single-page, PT-BR)

Nesta ordem exata:

1. **Navbar** — logo Gestalt · links (Produto, Recursos, Como funciona,
   FAQ) · botão "Agendar demonstração"
2. **Hero** — headline vendendo resultado + subheadline explicando que é
   um ERP pro setor de materiais planos · CTA primário "Agendar
   demonstração" + CTA secundário "Falar pelo WhatsApp" · **mockup
   grande do sistema real como elemento visual central** (não decore com
   ilustração genérica — o mockup do produto É o hero visual)
3. **Problema** — "Sua operação ainda depende de planilhas, papel e
   memória?" — 6 cards de dor: material perdido no estoque, retalhos
   esquecidos, dificuldade de rastrear material, retrabalho por falta de
   informação, relatórios manuais, tempo perdido procurando informação
4. **Solução** — "Um único sistema para controlar toda a operação." —
   fluxo visual horizontal: Estoque → Produção → Rastreabilidade →
   Resultado
5. **Módulos** — cada um é um benefício, não uma feature crua:
   - Estoque inteligente — saiba o que entrou, onde está, quanto ainda
     pode ser usado
   - Gestão de retalhos — transforme sobras em estoque aproveitável
   - Rastreabilidade — origem e histórico do material durante toda a
     operação
   - Produção — o que está sendo produzido, por quem, em qual etapa
   - Relatórios
6. **Product showcase** — "Veja o Gestalt em ação" — screenshots grandes
   do sistema (telas de estoque, produção, rastreabilidade)
7. **Segmentos** — "Feito para diferentes tipos de operação": Marmoraria
   · Marcenaria · Serralheria · Comunicação Visual · Indústria. **Sem
   prova social inventada** — não gerar logos placeholder de empresas
   fictícias. Essa seção é sobre segmentos de uso, não sobre clientes.
8. **Por que Gestalt?** — "Mais que um ERP. Um sistema pensado para a
   operação." — 4 diferenciais: construído para materiais reais (chapas,
   pedras, perfis, retalhos, peças, insumos), rastreabilidade de ponta a
   ponta, visão operacional em tempo real, menos desperdício
9. **Como funciona** — "Da entrada à entrega" — 4 passos: 1. Conheça sua
   operação 2. Configure o Gestalt 3. Comece a controlar 4. Evolua sua
   operação
10. **Planos** — "Uma solução que acompanha o tamanho da sua operação" —
    3 cards **sem preço fechado**: Essencial (operações começando a se
    organizar), Profissional (controle completo da operação), Empresarial
    (operações maiores, necessidades personalizadas). CTA "Falar com um
    especialista" em cada card
11. **FAQ**
12. **CTA final** — "Pronto para ter sua operação sob controle?" +
    botões Agendar demonstração / WhatsApp
13. **Footer** — Gestalt ERP · © 2026 · Termos · Privacidade

## 5. Direção visual

Referência: **Linear + Vercel + "SaaS industrial"** — precisão,
controle, tecnologia. Não é "software corporativo genérico".

Tokens (herdados do brand book do produto — não inventar cores novas):

- `accent`: `#256CEB` — único acento de cor da página
- `background`: `#FAFAFA`
- `surface`: `#FFFFFF`
- `text-primary`: `#0A0A0A`
- `text-secondary`: `#687080`
- `border`: `#E5E7EB` — sempre 1px onde precisar de contorno, nunca 2px+
- Tema claro
- Tipografia: **Geist Sans** apenas — uma família só, headings peso
  600/700, corpo 400
- Ícones: **Lucide** exclusivamente
- `border-radius` na escala 4/8/12/16/24/32px

Diferença em relação ao produto: o app principal é denso (ferramenta
operacional de chão de fábrica). A LP é o oposto — **muito espaço em
branco, tipografia grande no hero, screenshots do produto como elemento
visual principal**, sombras quase imperceptíveis.

### Proibido (não fazer sob nenhuma circunstância)

- Gradientes grandes, blobs decorativos, glassmorphism
- Excesso de cards decorativos sem conteúdo real
- Stock photos de operários sorrindo ou qualquer fotografia genérica de
  banco de imagens
- Ícones gigantes coloridos fora do sistema Lucide
- Copy genérica tipo "revolucione sua empresa com nossa solução
  inovadora" — toda copy deve ser específica ao domínio (material,
  produção, rastreabilidade)
- Logos placeholder de empresas fictícias na seção de segmentos/prova
  social

## 6. Comportamento responsivo

Página pública (não é o app desktop) — precisa de layout mobile real:
navbar colapsa em menu simples, hero empilha (texto acima, mockup
abaixo), grids de cards (problema, módulos, planos) colapsam para 1
coluna em telas estreitas, fluxo visual da seção Solução vira vertical
no mobile.

## 7. O que fazer

1. Primeiro, absorva o contexto de produto, posicionamento e a
   arquitetura de página acima.
2. Defina a direção de UX/UI (grid, escala tipográfica, composição de
   cada seção) seguindo a referência visual e os tokens do brand book —
   não pule direto pra artboards sem decidir isso.
3. Gere os artboards da landing page completa, seção por seção, na
   ordem da Seção 4 deste prompt.
4. Ao final, o resultado será convertido para código em
   React + TypeScript + Tailwind (repositório `gestalt-lp`, já
   inicializado com os tokens deste brand book configurados em
   `src/index.css`).
