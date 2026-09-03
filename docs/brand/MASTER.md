# Gestalt ERP — Master Visual System

Use este arquivo no Claude Design **uma vez** para estabelecer o sistema
visual completo. Após gerar o sistema visual, use cada prompt de tela
individualmente em sessões separadas.

> **LOGIC:** ao construir uma tela específica, primeiro checar
> `design-system/pages/[nome-da-tela].md`. Se existir, suas regras
> **sobrescrevem** este Master. Se não, seguir estritamente o que está aqui.

---

## 1. Identidade do produto

- **Marca:** Gestalt ERP
- **Produto:** ERP desktop (Electron) para gestão de estoque industrial —
  chapas, retalhos, certificados de rastreabilidade, produção e relatórios,
  pra indústrias de materiais planos (marcenaria, serralheria, marmoraria,
  comunicação visual).
- **Público:** operadores de chão de fábrica e administrativos/gestores,
  frequentemente na mesma estação de desktop compartilhada entre turnos.
- **Tom visual:** ferramenta profissional, densa em informação, séria e
  estável — não é landing page, não é app consumer. Referência: Linear,
  Vercel Dashboard — fino, bordas de 1px, hierarquia por tipografia/peso
  em vez de cor, sombra quase imperceptível.
- **Plataforma:** desktop Electron, janela mínima 1024×600. Não é PWA, não
  precisa de layout mobile — precisa continuar legível numa janela
  redimensionada até o mínimo.

---

## 2. Design tokens — Light theme

Valores travados pelo brand book do produto (`Gestalt ERP Brand Book v1.0`)
— não substituir, não inventar acento novo.

| Token | Hex | Uso |
|---|---|---|
| `accent` | `#256CEB` | CTA primário, item ativo de navegação, foco de input |
| `background` | `#FAFAFA` | Fundo principal da área de conteúdo |
| `surface` | `#FFFFFF` | Sidebar, cards, áreas agrupadas |
| `text-primary` | `#0A0A0A` | Texto principal, títulos |
| `text-secondary` | `#687080` | Labels, metadados, texto secundário |
| `border` | `#E5E7EB` | Divisores, bordas de input, separadores — sempre 1px |
| `success` | `#16A34A` | Badge ativo, métricas positivas (não é cor de marca, semântica padrão) |
| `error` | `#DC2626` | Badge erro, alertas críticos |
| `warning` | `#D97706` | Badge pendente, avisos |

## 3. Design tokens — Dark theme

Mesmos valores do brand book (§05 "Dark Mode Usage") — não é uma inversão
calculada, são valores fixos.

| Token | Hex Dark | Uso |
|---|---|---|
| `accent` | `#3B82F6` | CTA primário, item ativo, foco de input |
| `background` | `#0A0A0A` | Fundo principal |
| `surface` | `#171717` | Sidebar, cards |
| `text-primary` | `#F5F5F5` | Texto principal |
| `text-secondary` | `#A3A3A3` | Labels, metadados |
| `border` | `#1F1F1F` | Divisores, bordas |
| `success` | `#4ADE80` | Badge ativo |
| `error` | `#F87171` | Badge erro |
| `warning` | `#FBBF24` | Badge pendente |

---

## 4. Anatomia do layout — desktop Electron (sem variante mobile)

### Janela padrão (1280×720, mínimo 1024×600)
```
┌─────────────────────────────────────────────────────┐
│  TOPBAR: título da tela + ações + usuário/notif.    │
├──────────┬──────────────────────────────────────────┤
│ logo +   │                                          │
│ gestalt  │           CONTENT AREA                  │
│ erp      │           padding: 32px                 │
│ SIDEBAR  │                                          │
│  240px   │                                          │
│ nav itens│                                          │
│(agrupados)│                                         │
└──────────┴──────────────────────────────────────────┘
```

**Sidebar:** topo fixo com logo (`gestalt-logo.png`) + wordmark. Abaixo,
grupos de navegação recolhíveis (ver Bloco 9) — cada grupo é uma seção com
label + ícone + itens filhos, não uma lista plana. A topbar não repete a
logo — só título da tela, ações contextuais e o menu de usuário.

**Janela redimensionada perto do mínimo (1024×600):** sidebar não colapsa
em bottom-nav (não existe em desktop) — permanece fixa em 240px com o
conteúdo ganhando scroll horizontal controlado só dentro de tabelas largas,
ou colapsa pra modo ícone-only (~64px) preservando a hierarquia. Nunca
esconder a navegação inteira atrás de um hambúrguer nessa largura.

---

## 5. Componentes base (ícones: Lucide exclusivamente)

Projeto já usa `lucide-react` — não introduzir outro set de ícones.

| Componente | Especificação |
|---|---|
| `Table` | Cabeçalho fixo com sort arrows, linhas zebradas (`bg-surface` alternando com `background` sutil), paginação no rodapé (Anterior / 1 2 3 / Próxima) |
| `Badge` | `ativo` → verde + fundo verde-claro \| `inativo` → cinza \| `pendente` → âmbar \| `erro` → vermelho. `border-radius: 4px`, `padding: 2px 8px` |
| `MetricCard` | Número grande (32px, Geist Sans Bold) + label (`text-secondary`) + variação (ícone Lucide `TrendingUp`/`TrendingDown` + %) |
| `Button primary` | `bg-accent`, texto branco, `border-radius: 8px` |
| `Button secondary` | borda `accent`, texto `accent`, fundo transparente |
| `Button danger` | `bg-error`, texto branco |
| `Button ghost` | texto `accent`, sem borda, sem fundo |
| `FormInput` | Label acima (`text-secondary`, 12–14px), borda 1px `border`, borda `accent` no foco (ring 2px), mensagem de erro abaixo em `error` |
| `Skeleton` | Shimmer animado (gradiente esquerda→direita), `border-radius` igual ao componente que substitui |
| `EmptyState` | Ícone Lucide 48px centralizado (`text-secondary`) + título (16px, `text-primary`) + subtítulo (`text-secondary`) + Button primary opcional |
| `ErrorState` | Ícone `AlertCircle` (Lucide, `error`) + mensagem + Button ghost "Tentar novamente" |
| `Toggle` | Switch: off = cinza, on = `accent`. Label à direita. |

---

## 6. Instrução de uso

Ao processar este master:
1. Absorva o sistema de cores (light + dark), tipografia e componentes
2. Gere um style guide visual mostrando os tokens, componentes e layouts
3. Não gere telas individuais agora — elas virão em prompts separados
4. Mantenha este sistema em contexto para aplicar consistentemente

---

## 7. Regras de geração (não violar em nenhuma tela)

- Usar **somente** os tokens dos Blocos 2 e 3 — nunca hexadecimais avulsos
- **Proibido:** gradientes, glassmorphism, sombras `box-shadow` pesadas,
  blur decorativo, ícone/metáfora fora do sistema (ex.: nada de tag
  industrial, código de barras, textura — já testado e rejeitado)
- Ícones: **Lucide** apenas. Nunca Heroicons, Material Icons, FontAwesome
- Bordas: sempre 1px onde precisar de contorno — nunca 2px+
- Densidade **alta**: é ferramenta operacional, não landing page — tabelas
  com 5–8 linhas, cards com dados completos, sem espaço vazio decorativo
- Tipografia: **uma família só, Geist Sans** (self-hosted,
  `@fontsource/geist-sans`) — headings em peso 600/700, corpo em 400, labels
  em 500. Não introduzir segunda fonte (nem mono, nem serifada, nem display)
- `border-radius`: escala do brand book (4/8/12/16/24/32px) — inputs e
  botões em 8px, cards até 16px, badges em 4px
- Dados **sempre realistas** no domínio do produto: nomes de chapas/materiais
  reais (MDF, MDP, granito, vidro), certificados com número de lote,
  quantidades em m²/unidades, datas no formato DD/MM/AAAA

---

## 8. Data states obrigatórios

Toda tela existe em 3 estados. Quando o prompt de tela não especificar,
gerar **Populated**.

| Estado | O que renderizar |
|---|---|
| **Loading** | Skeletons shimmer no lugar de tabelas, cards e métricas. Sidebar e topbar visíveis e normais. |
| **Empty** | `EmptyState`: ícone contextual + título + subtítulo explicativo + CTA (ex.: "Nenhum retalho registrado ainda — registre uma sobra de corte") |
| **Populated** | Dados realistas do domínio industrial, tabelas com 5–8 linhas, métricas plausíveis (ex.: "1.284 m² em estoque", "97,2% de aproveitamento de chapa") |

---

## 9. Mapa de navegação (real — extraído de `src/components/layout/header.tsx`)

Grupos condicionados por permissão (`canChapas`, `canRetalhos`,
`canProducao`, `canReports`, `isAdmin`) — nem todo usuário vê todos os
grupos.

| Grupo | Ícone Lucide | Itens |
|---|---|---|
| Principal | `LayoutGrid` | Painel Principal (`/home`), Dashboard (`/dashboard-saidas`) |
| Chapas | `Box` | Estoque (`/estoque`), Entradas (`/entradas`), Saídas (`/saidas`) |
| Retalhos | `Layers` | Retalhos (`/retalhos`), Saídas (`/saidasretalhos`) |
| Produção | `Factory` | Quadro de Produção (`/producao`), Painel TV (`/producao-tv`), Painel de Máquinas (`/painel-maquinas`), Setores (`/producao-setores`), Máquinas (`/producao-maquinas`), Pausas Automáticas (`/producao-pausas`) |
| Relatórios | `BarChart2` | Central de Relatórios (`/relatorios`), Eficiência de Produção (`/relatorio-eficiencia`) |
| Administrativo | `ShieldCheck` | Usuários (`/usuarios`), Certificados de Rastreio (`/certificados`), Categorias de Materiais (`/categorias`), Acabamentos de Materiais (`/acabamentos`), Catálogo de Materiais (`/adicionar-material`), Configurações do Sistema (`/configuracoes`), Perfis de Acesso (`/perfis`), Etapas de Produção (`/etapas-producao`), Motivos de Alteração (`/motivos-alteracao`), Motivos de Pausa (`/motivos-pausa`) |

Sem variante mobile/bottom-nav — é sidebar de desktop sempre.

---

## 10. Regras UX (ui-ux-pro-max, adaptadas pra desktop mouse/teclado)

| Categoria | Regra |
|---|---|
| Alvo de clique | Mínimo 32–40px de altura em botões/inputs (já o padrão do projeto, `h-10`) — não é alvo de toque de celular, é mouse |
| Espaçamento | Gap mínimo de 8px entre elementos clicáveis adjacentes |
| Contraste | Texto principal vs fundo: mínimo 4.5:1. `text-secondary`: mínimo 3:1 |
| Animação | Micro-interações: 150–300ms. Usar `transform`/`opacity`, nunca animar `width`/`height` |
| Formulários | Label visível acima do input, nunca só placeholder. Erro abaixo do campo |
| Empty states | Sempre ícone + título + subtítulo + CTA opcional — nunca tela em branco |
| Listas longas | Tabelas com 50+ linhas: paginação real (já é o padrão do backend) |
| Charts (Recharts) | Sempre legenda + tooltip visível no hover. Grid lines sutis (`border` do tema) |
| Disabled states | Opacidade 0.38–0.5 + `cursor: not-allowed` |
| Foco de teclado | Ring visível (`accent`, 2px) em todo elemento interativo — app é usado com teclado em formulários de produção |
