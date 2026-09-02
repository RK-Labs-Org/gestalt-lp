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
   ilustração genérica — o mockup do produto É o hero visual). Ver regra
   de assets reais vs. placeholder na Seção 5.
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
7. **Segmentos / credibilidade** — "Projetado para operações onde cada
   material importa." + segmentos de uso: Marmoraria · Marcenaria ·
   Serralheria · Comunicação Visual · Indústria. Isso é uma seção de
   **credibilidade por especificidade de domínio**, não prova social
   disfarçada — não simular clientes, não gerar logos placeholder de
   empresas fictícias.
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
branco, mas sem desperdício de espaço ou longos trechos visualmente
vazios**, tipografia grande no hero, screenshots do produto como
elemento visual principal, sombras quase imperceptíveis.

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

### Assets reais vs. placeholder

Se houver screenshots/assets reais do Gestalt disponíveis no projeto,
use-os como fonte visual pro mockup do hero e pro product showcase. Não
recrie telas fictícias do produto por conta própria. Caso ainda não haja
assets reais anexados a este prompt, crie **placeholders estruturais
claramente identificados** (ex. frame com texto "[screenshot real do
Gestalt aqui]") para substituição posterior — nunca um "ERP fake"
genérico que pareça bonito mas seja visualmente diferente do produto
real.

Se o arquivo `../Gestalt/design-system/gestalt/MASTER.md` estiver
acessível, leia-o antes de definir componentes ou recriar qualquer tela
do produto — ele descreve os componentes reais (Table, Badge, MetricCard
etc.) e qualquer tela recriada deve seguir essa especificação
exatamente, sem inventar funcionalidade que não existe no produto. Se
não estiver acessível, não invente regras adicionais de design; siga
exclusivamente os tokens e regras deste prompt.

## 6. Comportamento responsivo

Página pública (não é o app desktop) — precisa de layout mobile real:
navbar colapsa em menu simples, hero empilha (texto acima, mockup
abaixo), grids de cards (problema, módulos, planos) colapsam para 1
coluna em telas estreitas, fluxo visual da seção Solução vira vertical
no mobile.

## 7. Conversão e UX

Objetivo primário da página: converter visitantes em solicitações de
demonstração.

- CTA principal: "Agendar demonstração"
- CTA secundário: "Falar pelo WhatsApp"
- O CTA deve reaparecer de forma contextual ao longo da página (não só
  no topo e no rodapé), sem parecer repetitivo ou agressivo
- Nada de pop-ups, countdowns, urgência artificial ou dark patterns

A página deve permitir que o visitante entenda em poucos segundos, nesta
ordem: (1) o que é o Gestalt, (2) qual problema resolve, (3) para quem
é, (4) como funciona, (5) por que é diferente, (6) como solicitar uma
demonstração.

### Copy e conteúdo

Toda a copy deve ser escrita em PT-BR natural, direta e específica ao
contexto industrial.

Não inventar:

- Números de clientes
- Percentuais de redução de desperdício
- Resultados financeiros
- Depoimentos
- Nomes de clientes
- Certificações
- Integrações
- Funcionalidades que não foram mencionadas neste briefing

Não usar claims que exigiriam comprovação, como "reduza seu desperdício
em 40%" ou "aumente sua produtividade em 3x". Quando uma informação
comercial não estiver definida, prefira uma formulação neutra em vez de
inventar dados.

A linguagem deve falar com o dono/gestor da operação, não com um
profissional de marketing ou investidor.

### Hero — exploração de copy

Antes de fixar a headline final, explore internamente até 3 direções de
copy, todas orientadas a resultado e específicas ao domínio.

A headline final deve:

- Ser curta
- Ser compreendida em poucos segundos
- Falar de controle, material ou operação
- Evitar começar com "Gestalt é um ERP..."
- Evitar linguagem exageradamente publicitária

"Do estoque à produção. Tudo sob controle." é a referência principal,
não uma frase obrigatória.

## 8. Qualidade visual — evitar "AI slop"

Evite padrões visuais genéricos de páginas SaaS geradas por IA. Não
usar:

- Hero dividido 50/50 de forma automática
- Grids repetitivos de 3 cards como resposta padrão pra qualquer seção
- "Ícone + título + descrição" como template único repetido em todas as
  seções
- Círculos decorativos
- Números gigantes sem significado
- Gradientes usados só pra "dar vida"
- Excesso de badges
- Sombras pesadas
- Elementos flutuantes sem função

Cada seção deve ter uma composição visual própria, mas permanecer dentro
do mesmo sistema de design. Priorize hierarquia, ritmo vertical,
tipografia, whitespace, alinhamento e os screenshots reais do produto
como elementos de design — não decoração em cima da composição.

**Não deixe a LP "bonita" demais.** O Gestalt tem a oportunidade de
parecer um produto de software sério: branco, preciso, técnico, quase
editorial, com o azul (`accent`) aparecendo só onde realmente importa
(CTA, foco, destaque pontual). O produto real — os screenshots — é a
estrela da página, não a decoração ao redor dele.

## 9. Qualidade técnica

Projetar já pensando na implementação real em
React + Vite + TypeScript + Tailwind. Priorizar:

- HTML semântico
- Acessibilidade WCAG (contraste adequado, navegação por teclado,
  estados hover/focus/active visíveis)
- Imagens otimizadas, lazy loading para screenshots abaixo do fold
- Responsividade real (ver Seção 6)
- SEO básico e Open Graph
- Performance / Core Web Vitals

Não propor interações que dependam de bibliotecas adicionais sem
necessidade real.

## 10. O que fazer

1. Primeiro, absorva o contexto de produto, posicionamento e a
   arquitetura de página das Seções 1-4.
2. **Antes de gerar qualquer artboard**, apresente a Design Direction —
   decisões estruturais explícitas, não pule direto pro visual:
   - Grid e largura máxima do conteúdo
   - Escala tipográfica
   - Espaçamento vertical entre seções
   - Sistema de componentes (botões, cards, badges) derivado dos tokens
     da Seção 5
   - Comportamento dos CTAs (Seção 7)
   - Composição do hero (Seção 7, exploração de copy)
   - Tratamento visual dos screenshots/mockups (Seção 5, assets reais
     vs. placeholder)
   - Estratégia responsiva (Seção 6)
3. Aplique essas decisões de forma **consistente em toda a página** —
   não alterar arbitrariamente o sistema visual entre seções (evitar a
   primeira seção parecer Vercel, a segunda um template Webflow, a
   terceira um dashboard genérico).
4. Gere os artboards da landing page completa, seção por seção, na
   ordem da Seção 4 deste prompt, seguindo a Design Direction definida
   no passo 2 e as regras de qualidade das Seções 8 e 9.
5. Ao final, o resultado será convertido para código em
   React + TypeScript + Tailwind (repositório `gestalt-lp`, já
   inicializado com os tokens deste brand book configurados em
   `src/index.css`).
