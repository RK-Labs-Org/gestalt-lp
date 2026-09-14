# Gestalt LP — Seção "Integrações" (arranjo de serviço)

## Objetivo

Adicionar uma nova seção à LP divulgando a integração do Gestalt com
softwares de arranjo/agendamento de serviço já existentes no mercado —
pedido direto do sócio. Reforça que adotar o Gestalt não exige trocar a
ferramenta de arranjo que a operação já usa.

## Posicionamento

Mensagem central: **"Já usa um sistema de arranjo? O Gestalt entra no
seu fluxo."** — o Gestalt se encaixa na operação existente em vez de
substituir uma ferramenta que já funciona.

Integração real e nomeada hoje: **Cypnest**. Demais softwares de
arranjo do mercado são tratados de forma genérica — sem inventar nomes
de parceiros ou logos de marcas com quem não há integração de fato.

## Posição na página

Entra logo após a seção **5. Módulos** e antes da **6. Product
showcase ("Veja o Gestalt em ação")** — na sequência de "o que o
sistema faz", como mais uma capacidade do produto.

## Estrutura da seção

1. **Título** — variação de "Já usa um sistema de arranjo? O Gestalt
   entra no seu fluxo." Subheadline curta reforçando que não é preciso
   trocar de ferramenta.
2. **Card grande — Cypnest** — destaque principal da seção:
   - Wordmark/placeholder do Cypnest (sem logo oficial disponível
     ainda — usar tratamento tipográfico neutro, não inventar um
     logotipo)
   - 1–2 frases curtas sobre o que a integração resolve (ex.:
     sincronização de arranjos/agendamentos direto no Gestalt, sem
     retrabalho manual de reentrada de dados)
3. **Grid pequeno — "outros softwares do mercado"** — 3–5 chips/ícones
   genéricos (não nomeados), com legenda do tipo "e outros sistemas de
   arranjo de serviço do mercado". Visualmente subordinado ao card do
   Cypnest (menor, mais discreto).

## Direção visual

Herda os tokens já estabelecidos na spec da LP
(`2026-09-02-landing-page-design.md`): accent `#256CEB`, tema claro,
Geist Sans, ícones Lucide, bordas finas, sombras quase imperceptíveis.

- Card do Cypnest com peso visual comparável a um card de módulo
  "hero" — não um card pequeno igual aos genéricos
- Grid de "outros" claramente menor/mais discreto que o card Cypnest —
  a hierarquia visual precisa deixar óbvio quem é a integração real
  vs. os genéricos
- Nenhum logo de marca real além de Cypnest (mesma regra de "sem prova
  social inventada" já aplicada ao resto da LP)

### Proibido

- Inventar nomes ou logos de softwares de arranjo com quem não há
  integração real
- Prometer parceria/integração que não existe
- Estourar a hierarquia visual (grid genérico não pode competir com o
  card do Cypnest)

## Fluxo de trabalho

Mesmo fluxo da LP original: a fonte de verdade do design é o **Claude
Design** (`dist/index.html` é o export estático servido pela Vercel;
`src/App.tsx` é apenas scaffold placeholder, não reflete a LP real).

1. Gerar/editar o artboard da nova seção no Claude Design, seguindo
   este spec e herdando a direção visual do artboard existente da LP.
2. Reexportar o standalone (`dist/index.html`) a partir do resultado
   aprovado no Claude Design.

## Fora de escopo (por agora)

- Logo oficial do Cypnest (usar tratamento tipográfico até termos o
  asset real)
- Nomear qualquer outro software de arranjo específico além do Cypnest
- Deep-link ou integração técnica de fato (a seção é institucional/
  divulgação, não configuração funcional da integração)
