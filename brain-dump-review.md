# Revisão Crítica — `brain-dump.md` v1.0

> **Artefato:** `brain-dump-review.md` (revisão meta do system prompt)
> **Fonte sob auditoria:** `brain-dump.md` v1.0 (529 linhas, emitido 26 abr 2026)
> **Data da revisão:** 27 abr 2026 | **Idioma:** pt-BR | **Fuso:** America/Sao_Paulo
> **Revisor:** passe crítico-confrontacional automatizado, sob direção de Caio Villani França
> **Status:** Pendente de aceitação humana — nenhuma alteração aplicada a `brain-dump.md`

---

## 1. Sumário Executivo

**O system prompt é estruturalmente sólido, mas operacionalmente inflado para o porte do CMSMRI e cita um padrão de acessibilidade desatualizado em 2026.** A arquitetura de 12 seções é coerente, os guardrails de §10 cobrem o essencial da Reforma Psiquiátrica e o aterramento institucional em §2 está bem amarrado. Porém, o produto cartesiano `13 papéis × 18 camadas × 3 ciclos × 11 fases` produz um custo cognitivo desproporcional ao tamanho da Coordenadoria (RAPS regional ~85k hab) e à capacidade real de revisão humana solo do stakeholder.

**Antes de ativar o agente, três bloqueadores devem ser resolvidos:** (i) o gating humano só aparece na Fase 9, deixando 8 fases sem checkpoint externo; (ii) WCAG 2.1 AA é piso obsoleto em 2026, sem menção a WCAG 2.2 nem ao eMAG 3.1, que é mandatório para órgãos públicos brasileiros; (iii) a "equipe internacional simulada" não tem mecanismo para distinguir opinião do modelo de evidência verificável, o que viola o §4.1 do CLAUDE.md global ("anti-alucinação"). Os achados abaixo organizam 14 pontos por severidade, mais um patch concreto para v1.1.

### 1.1 Distribuição de severidade

| Severidade | Quantidade | Significado operacional |
|---|---|---|
| Bloqueador | 3 | Resolver antes da Fase 0 |
| Alto | 5 | Resolver antes da Fase 4 (escrita) |
| Médio | 4 | Incorporar até v1.1 (próxima revisão trimestral) |
| Baixo | 2 | Polimento opcional |
| **Total** | **14** | — |

### 1.2 Achado mais crítico (one-liner)

`brain-dump.md` v1.0 entrega disciplina sem entrega — é alto em processo (11 fases, 3 ciclos, 13 papéis) e baixo em mecanismo de saída (só uma checagem humana, na Fase 9). Para um stakeholder solo neurodivergente conduzindo um DS de saúde mental pública municipal, isso aumenta o risco de **planning paralysis** acima do risco de baixa qualidade do output.

---

## 2. Metodologia da Revisão

### 2.1 Lentes aplicadas

12 lentes de auditoria, cruzadas contra as §§1–12 do brain-dump:

| ID | Lente | Pergunta-guia |
|---|---|---|
| L1 | Auto-consistência interna | Há contradições entre §§? |
| L2 | Lacunas de escopo | O que falta em §5 para um DS de saúde mental pública? |
| L3 | Viabilidade operacional | É executável solo + 1 agente? |
| L4 | Simulação de papéis | A "equipe internacional" produz autoridade falsa? |
| L5 | LGPD / SUS / Reforma Psiquiátrica | Os guardrails cobrem dados sensíveis em saúde mental? |
| L6 | Acessibilidade | WCAG 2.1 é piso adequado em 2026? eMAG 3.1 está? |
| L7 | Critérios de "pronto" verificáveis | Os checklists são auditáveis ou retóricos? |
| L8 | Governança e ciclo de vida | Como o próprio prompt evolui? |
| L9 | Tooling realista | As skills/MCPs estão disponíveis? |
| L10 | Limites absolutos | §10.2 cobre derivação visual / direitos autorais? |
| L11 | Adequação ao contexto local | Há sobre-engenharia para Extrema-MG? |
| L12 | Clareza humano × IA | A fronteira "IA prepara / humano executa" é consistente? |

### 2.2 Fora do escopo desta revisão

- **Conteúdo do design system em si:** este documento audita o *processo de planejamento*, não a identidade visual ou os tokens.
- **Implementação técnica:** não foram testadas skills, MCPs, nem fluxos de export.
- **Tradução para outros idiomas:** o brain-dump é pt-BR-only por design (§1, §11.1).
- **Edição direta de `brain-dump.md`:** todas as correções são propostas; a aceitação é decisão do stakeholder.

### 2.3 Convenções

- Cada achado tem ID `[A##]`, severidade explícita, lente aplicada, seção(ões) afetada(s) e correção proposta.
- Severidades: **Bloqueador** (Fase 0), **Alto** (Fase 4), **Médio** (v1.1), **Baixo** (opcional).
- Citações literais entre aspas "..." com nº de linha. Paráfrases sem aspas.

---

## 3. Achados por Severidade

### 3.1 Bloqueadores

#### [A01] Custo cognitivo inviável para stakeholder solo neurodivergente

- **Severidade:** Bloqueador
- **Lente:** L3 (viabilidade operacional)
- **Seção(ões) afetada(s):** §3 (linhas 70–90), §4.5 (linhas 125–130), §5 (linhas 134–263), §7 (linhas 308–361)
- **Evidência:** §3 prevê 13 papéis "convocados em decisões críticas" (linha 90); §4.5 prevê "mínimo de 3 ciclos completos" (linha 127); §5 lista 18 camadas; §7 lista 11 fases (Fases 0–10).
- **Problema:** O produto cartesiano teórico é 13 × 18 × 3 × 11 = **7 722 deliberações nominais**. Mesmo descontando 90% por sobreposição, restam centenas de passes. O stakeholder é um único humano (TDAH desatento, perfil Caio §1 do CLAUDE.md global), revisando solo, sem equipe de design contratada. A janela de contexto de qualquer modelo, e a banda atencional de qualquer humano, são finitas.
- **Impacto:** Risco alto de **planning paralysis**: o relatório nasce, mas nunca é implementado porque revisar 100+ páginas em 3 ciclos consome o orçamento cognitivo que deveria ir para execução. Isto contradiz frontalmente o §5 do CLAUDE.md global ("o risco a evitar não é entregar cedo demais — é refinar indefinidamente sem entregar").
- **Correção proposta para v1.1:**
  1. Reduzir §4.5 de "mínimo 3 ciclos" para "1 ciclo de auto-iteração + 1 revisão humana"; sinalizar que ciclos adicionais são opcionais e disparados por gatilho explícito (ex.: stakeholder solicita rigor extra conforme §11.3).
  2. Em §3, mudar "convocar 13 papéis em decisões críticas" para "convocar até 4 papéis relevantes por decisão substantiva, justificando exclusões".
  3. Em §6, adicionar **"MVP do relatório (v0.1)"** como entrega anterior ao Draft 0 completo: cobre só §§1–4 do entregável (Sumário Executivo + Análise Situacional + Premissas + Inventário Mínimo das 5 camadas críticas).
  4. Em §6.4, adotar a regra de suficiência do CLAUDE.md global §5: **"score ≥ 94/100 em rubrica auto-avaliada → entregar imediatamente"**.

---

#### [A02] Gating humano só aparece na Fase 9 — 8 fases operam sem checkpoint externo

- **Severidade:** Bloqueador
- **Lente:** L12 (humano × IA)
- **Seção(ões) afetada(s):** §1.1 (linhas 13–17), §7 Fases 0–8 (linhas 310–352), §10.3 (linhas 449–454)
- **Evidência:** §1.1: "Você é uma camada cognitiva de planejamento [...] que prepara o terreno para que designers humanos [...] executem". §7 Fase 9 (linha 354): "Validação Final pelo Stakeholder" é a primeira validação humana explícita. As Fases 0–8 (incluindo escrita do relatório completo na Fase 4 e três ciclos de auto-iteração nas Fases 6–8) não exigem validação humana entre etapas.
- **Problema:** Há um único gate humano — só após o Relatório v0.3 estar pronto. Isto cria três riscos: (i) erros de premissa em Fase 0–1 propagam-se irreversivelmente até Fase 8; (ii) o stakeholder solo recebe um documento volumoso pré-iterado, dificultando intervenção pontual; (iii) viola o princípio §4.6 do CLAUDE.md global ("decisão final é sempre humana") em sua dimensão *gradual*, não só *terminal*.
- **Impacto:** Auto-confirmação iterativa: o agente refina contra si mesmo nas Fases 5–8, podendo amplificar inferências frágeis ("o Brand Strategist convocou novamente o argumento X" não é evidência, é reverberação).
- **Correção proposta para v1.1:**
  1. Adicionar **gates humanos explícitos** após Fase 1 (validação do plano), Fase 2 (validação da auditoria crítica), Fase 5 (validação da primeira auto-auditoria do relatório).
  2. Cada gate humano deve ser binário: `aprova` | `solicita ajuste` | `interrompe`.
  3. Documentar prazo máximo razoável para resposta humana (ex.: 5 dias úteis); se ultrapassado, agente *para*, não continua por inércia.
  4. Em §1.1, substituir "diretor executivo" por "**preparador técnico**" para reduzir conotação de autonomia decisória.

---

#### [A03] WCAG 2.1 como piso é obsoleto em 2026; eMAG 3.1 ausente

- **Severidade:** Bloqueador
- **Lente:** L6 (acessibilidade)
- **Seção(ões) afetada(s):** §1.3 (linha 29), §5.4 (linha 164), §5.14 (linhas 226–231), §8 (linha 375), §10.1 (linha 435), §11.1 (linha 476)
- **Evidência:** Todas as referências a acessibilidade citam exclusivamente "WCAG 2.1 AA". O Modelo de Acessibilidade em Governo Eletrônico (eMAG 3.1) — referência **mandatória** para sítios de órgãos públicos brasileiros segundo Portaria 03/2007 do MP/SLTI — não é mencionado. Lei Brasileira de Inclusão (Lei 13.146/2015) também não.
- **Problema:** WCAG 2.2 foi publicada como W3C Recommendation em 5 out 2023 (a verificar a data exata). Para projetos novos iniciados em 2026, o piso defensável é WCAG 2.2 AA, não 2.1. Adicionalmente, o CMSMRI é equipamento da Prefeitura Municipal (§2.2), portanto sujeito ao eMAG quando publicar materiais digitais.
- **Impacto:** O design system pode nascer formalmente desatualizado. Risco político concreto: nota técnica do MPF ou questionamento do CMS sobre conformidade de acessibilidade, especialmente em materiais voltados a usuários do Centro Integrar (TEA / DI), onde acessibilidade cognitiva é central.
- **Correção proposta para v1.1:**
  1. Substituir todas as ocorrências de "WCAG 2.1 AA" por "**WCAG 2.2 AA + eMAG 3.1**".
  2. Em §5.14, adicionar como elementos constituintes:
     - LIBRAS (Lei 10.436/2002) para conteúdo audiovisual institucional;
     - Audiodescrição para vídeos > 30s;
     - Conformidade com Decreto 5.296/2004 em sinalização física;
     - Padrão de fácil leitura conforme Lei 13.146/2015 art. 63 para materiais voltados ao Centro Integrar.
  3. Em §8 ("Acessibilidade"), trocar a métrica "WCAG 2.1 AA referenciado" por "**WCAG 2.2 AA + eMAG 3.1 verificados em cada decisão de cor, tipografia e componente UI**".

---

### 3.2 Altos

#### [A04] Conformidade LGPD subspecificada para dados sensíveis em saúde mental

- **Severidade:** Alto
- **Lente:** L5 (LGPD/SUS)
- **Seção(ões) afetada(s):** §5.7 (linhas 184–188), §10.1 (linha 433), §10.2 (linhas 439–447)
- **Evidência:** §5.7 menciona "consentimento, LGPD" como diretriz para fotografia. §10.1 lista "Conformidade LGPD em coleta e uso de imagens/depoimentos" como verificação obrigatória. §10.2 proíbe "Acessar/divulgar dados pessoais sem consentimento e justificativa legal".
- **Problema:** Saúde mental é categoria de **dado pessoal sensível** sob Lei 13.709/2018 (LGPD) art. 5º II e art. 11. Isso impõe obrigações qualitativamente distintas das aplicáveis a dados gerais: (i) consentimento livre, informado e *específico para a finalidade* (art. 11 §1º); (ii) dispensa de consentimento apenas em hipóteses estritas (tutela da saúde por profissional, política pública prevista em lei, pesquisa por órgão público com anonimização). O brain-dump trata "LGPD" genericamente, sem distinguir essas hipóteses.
- **Impacto:** Risco real em três artefatos do DS: (a) banco de imagens com pacientes/familiares; (b) depoimentos em campanhas e materiais de psicoeducação; (c) materiais de imprensa que mencionem casos. Sem protocolo, qualquer um destes pode produzir incidente sob LGPD com responsabilidade da Coordenadoria.
- **Correção proposta para v1.1:**
  1. Adicionar §10.5 — **"Protocolo de Dados Pessoais Sensíveis"** com:
     - Distinção explícita entre Lei 13.709/2018 art. 7 (dados gerais) vs art. 11 (dados sensíveis);
     - Exigência de Termo de Consentimento Livre e Esclarecido **específico** para uso de imagem/depoimento;
     - Política de retenção e descarte;
     - Vedação de uso de imagens reais de usuários em materiais não-essenciais.
  2. Em §5.7, substituir "consentimento, LGPD" por "**Termo de Autorização de Uso de Imagem específico (LGPD art. 11) + alinhamento com Resolução CFM 2.314/2022 quando aplicável a contexto clínico**".
  3. Em §10.1, desdobrar "Conformidade LGPD" em três checks distintos: (a) finalidade declarada; (b) consentimento específico arquivado; (c) política de descarte aplicada.

---

#### [A05] Skills citadas sem verificação de disponibilidade no ambiente operacional

- **Severidade:** Alto
- **Lente:** L9 (tooling realista)
- **Seção(ões) afetada(s):** §9.1 (linhas 384–402)
- **Evidência:** §9.1 lista 15 skills da Anthropic, incluindo: `interface-design`, `brand-guidelines`, `canvas-design`, `algorithmic-art`, `theme-factory`, `web-artifacts-builder`, `internal-comms`, `accessibility-review`, `design-critique`, `design-system-management`, `ux-writing`.
- **Problema:** Confronto com a lista de skills carregadas no ambiente atual de Caio (system reminder do Claude Code, abr 2026): `interface-design` está disponível; `frontend-design` está disponível; `figma-*` (`figma-use`, `figma-implement-design`, `figma-generate-design`, etc.) estão disponíveis. **Não foram localizadas no ambiente:** `brand-guidelines`, `canvas-design`, `algorithmic-art`, `theme-factory`, `web-artifacts-builder`, `internal-comms`, `accessibility-review`, `design-critique`, `design-system-management`, `ux-writing`. Essas skills podem (i) existir em outros produtos Anthropic (claude.ai, Projects, Artifacts) mas não em Claude Code; (ii) estar planejadas mas não emitidas; (iii) ter sido inventadas pelo modelo durante a redação do brain-dump.
- **Impacto:** O agente, ao executar Fases 4–8, tentará invocar skills inexistentes, falhará e poderá fabricar racionalizações ("simulei o output da skill X"). Isto contamina a auditabilidade.
- **Correção proposta para v1.1:**
  1. Em §9.1, marcar cada skill com status: `[disponível em CC]`, `[disponível em claude.ai]`, `[a verificar]`.
  2. Substituir skills não-localizadas por equivalentes verificados ou por *prompts internos* descritivos (ex.: em vez de `accessibility-review` skill, instrução explícita: "auditar contra checklist WCAG 2.2 + eMAG 3.1").
  3. Adicionar §9.4 — **"Pré-voo de tooling"**: antes da Fase 0, agente confirma disponibilidade de cada skill listada e reporta lacunas.

---

#### [A06] Risco de falsa autoridade da "equipe internacional simulada"

- **Severidade:** Alto
- **Lente:** L4 (simulação de papéis)
- **Seção(ões) afetada(s):** §1.1 (linha 15), §3 (linhas 70–90), §10.1 (linha 437)
- **Evidência:** §1.1: "diretor executivo de uma equipe interdisciplinar internacional simulada de especialistas". §3 lista 13 papéis com perspectivas, sem mecanismo para distinguir "perspectiva como recurso heurístico" de "expert opinion verificável".
- **Problema:** Quando o agente diz "o Accessibility Expert (WCAG/IAAP) recomenda X", há ambiguidade ontológica: (i) é uma recomendação verificável da literatura WCAG/IAAP? (ii) é uma inferência do modelo a partir do papel? (iii) é uma alucinação plausível? O brain-dump não exige rastreabilidade do tipo "papel X afirma Y porque [fonte verificável]". Isto colide com o §4.1 do CLAUDE.md global ("anti-alucinação", "distinguir explicitamente entre fato verificado, inferência razoável, e opinião/recomendação").
- **Impacto:** Risco de o relatório final transmitir falsa confiança em decisões fundamentadas apenas no roleplay do modelo. Em contexto institucional público, isto pode evoluir para **defesa frágil** sob auditoria do TCM-MG, MPF ou CMS.
- **Correção proposta para v1.1:**
  1. Em §3, adicionar parágrafo final:
     > **Atenção ontológica:** os 13 papéis são *lentes deliberativas heurísticas*, não fontes de autoridade. Quando uma decisão for atribuída a um papel, o agente deve marcá-la como `[lente: papel N]` se for inferência interna, ou como `[fonte: ref. Y]` se houver evidência verificável citável. Nunca apresentar opinião do modelo como consulta a especialista real.
  2. Em §10.1, adicionar verificação obrigatória: "**Distinção fato verificado / inferência / opinião aplicada em todas as recomendações substantivas**".

---

#### [A07] Direitos autorais e licenciamento de ativos não cobertos

- **Severidade:** Alto
- **Lente:** L10 (limites absolutos)
- **Seção(ões) afetada(s):** §5.5 (linha 171), §5.7 (linhas 184–188), §10.2 (linha 446)
- **Evidência:** §5.5 menciona "Licenciamento (open-source preferencial: Inter, IBM Plex, Source, etc.)". §10.2 proíbe "Cópia de identidade visual de outras instituições".
- **Problema:** Três zonas de risco não cobertas:
  - **Tipografia comercial sem licença:** se o agente recomendar uma fonte comercial (ex.: Helvetica Neue, Avenir) para uso institucional, a Prefeitura precisa de licença OEM/web compatível com escala de uso. O brain-dump não orienta sobre isso.
  - **Bancos de imagem com TOS incompatível:** alguns bancos (incluindo gratuitos como Unsplash) têm cláusulas que vedam uso por entidades públicas em materiais oficiais sem licença ampliada. Outros bancos vetam uso com sobreposição de logos institucionais.
  - **Ativos gerados por IA + direitos autorais:** logos ou ilustrações geradas via Midjourney/DALL-E/Sora podem (i) estar fora do escopo de proteção pela Lei 9.610/1998 (jurisprudência nacional ainda é escassa em 2026, a verificar); (ii) treinadas em corpora com obras protegidas, criando risco derivativo.
- **Impacto:** Identidade visual institucional construída sobre base juridicamente frágil. Risco político e patrimonial concreto.
- **Correção proposta para v1.1:**
  1. Adicionar §5.19 — **"Licenciamento e Propriedade Intelectual"** como nova camada (nº 19, ou incorporar à §5.16 expandida) cobrindo:
     - Política de tipografia: preferência por OFL ou domínio público; vedação de uso de fontes comerciais sem licença documentada;
     - Política de imagens: banco oficial CMSMRI com obras com licença explícita (CC0, CC-BY com atribuição, ou produção própria);
     - Política de geração por IA: vedação de uso de logos gerados por IA como marca registrável; uso permitido apenas para mockups internos com revisão humana;
     - Conformidade com Lei 9.610/1998 e LGPD.
  2. Em §10.2, expandir "Cópia de identidade visual" para "**Cópia, derivação não-autorizada ou uso de ativos com licenciamento incompatível com uso institucional público**".

---

#### [A08] Critérios de "pronto" são parcialmente tautológicos e não definem validador

- **Severidade:** Alto
- **Lente:** L7 (critérios verificáveis)
- **Seção(ões) afetada(s):** §6.4 (linhas 296–304), §8 (linhas 365–378), §11 (linhas 467–495)
- **Evidência:** §6.4 lista 6 condições para "pronto", incluindo: "Todos os critérios de qualidade do §8 foram atendidos" e "Sinais vitais do §11 foram verificados". §8 é uma tabela de critério × métrica sem definição de quem aplica a métrica. §11.1 inclui "Recência e datas validadas" sem fonte de verdade.
- **Problema:** Tautologia operacional — "pronto" = "atende §8" = "auto-consistência verificada" = "zero contradições detectadas em busca dirigida". Quem dirige a busca? Com que profundidade? Quanto custa atingir o critério? Não há rubrica numérica nem validador externo.
- **Impacto:** O agente pode declarar "pronto" iterativamente sem que ninguém o desafie. Caio recebe um documento marcado como "pronto" e não tem instrumento para questionar. Em contraste, o §5 do CLAUDE.md global oferece **rubrica explícita de 10 eixos com cutoff em 94/100**, mas o brain-dump não a importou.
- **Correção proposta para v1.1:**
  1. Em §8, substituir a tabela por rubrica auto-avaliada de 10 eixos, importando do CLAUDE.md global §5: fidelidade factual, completude, conformidade regulatória, viabilidade operacional, clareza, adequação às normas pt-BR, legibilidade, arquitetura textual, fluidez, fidedignidade.
  2. Definir cutoff: **score ≥ 94/100 → entregar; < 94 → identificar eixo mais frágil e iterar até 1× nele**.
  3. Em §6.4, substituir as 6 condições atuais por: (a) rubrica ≥ 94/100; (b) gates humanos atendidos (cf. A02); (c) §11.1 e §11.2 marcados.
  4. Designar validador para cada métrica do §11 (ex.: "datas validadas → pelo agente, com flag explícito quando inferidas").

---

### 3.3 Médios

#### [A09] Lacunas de escopo em §5: comunicação em crise, multilinguismo, wayfinding territorial

- **Severidade:** Médio
- **Lente:** L2 (lacunas de escopo)
- **Seção(ões) afetada(s):** §5 (linhas 134–263), especialmente §5.8, §5.9, §5.13, §5.18
- **Evidência:** §5.8 (Voz e Tom) prevê "tom modulado por contexto (usuário em crise, gestão, mídia, equipe)" como item da camada, sem desdobrar em padrões. §5.13 (Som) é minimalista. §5.18 (Implementação por meio) lista web/impressão/sinalização/redes/equipes — sem **território**.
- **Problema:** Para um equipamento de saúde mental que coordena CAPS I + Centro de Saúde Mental + Centro Integrar, faltam:
  - **Comunicação em crise / talkdown:** padrões para mensagens em situações de risco autopercebido (ideação suicida, surto psicótico). A literatura é específica (Means Restriction Counseling, Safe Messaging Guidelines da WHO 2017 atualizada — a verificar) e divergente do tom institucional padrão.
  - **Multilinguismo regional:** Extrema-MG tem trabalhadores transfronteiriços (Atibaia, fronteira com SP) e potencialmente comunidades migrantes (a verificar via censo Extrema 2022). Falta diretriz mínima sobre quando produzir versão em espanhol ou português simplificado.
  - **Wayfinding territorial:** sinalização externa entre os três equipamentos (CI, CSM, CAPS) e sua relação com a UBS de referência. §5.18 fala em "sinalização (materiais, durabilidade)" mas não em arquitetura informacional territorial.
  - **Material de educação permanente:** capacitações de equipe RAPS, oficinas para ACS — formato distinto de comunicação institucional.
  - **Atendimento à imprensa:** kit de imprensa, protocolo de fala com mídia (especialmente em casos sensíveis: suicídio, internação involuntária, MS divulgar dados).
- **Impacto:** O DS nasce com pontos cegos exatamente nas situações de maior fricção pública.
- **Correção proposta para v1.1:**
  1. Adicionar §5.20 — **"Comunicação em Saúde Mental de Alta Sensibilidade"** com sub-itens: talkdown / Safe Messaging Guidelines / protocolo imprensa / linguagem em postvenção.
  2. Adicionar §5.21 — **"Educação Permanente e Capacitação"** com templates de slide-deck, handout, vídeo curto.
  3. Em §5.18, expandir "sinalização" para "sinalização interna + wayfinding territorial RAPS".
  4. Em §5.9, adicionar item: "Política de tradução / multilinguismo (espanhol regional, português simplificado, LIBRAS)".

---

#### [A10] Sobre-engenharia para o porte do CMSMRI

- **Severidade:** Médio
- **Lente:** L11 (contexto local)
- **Seção(ões) afetada(s):** §1.2 (linhas 19–21), §5 (18 camadas), §6.2 (11 seções de relatório)
- **Evidência:** §1.2: "processo iterativo, auditável e de **alta granularidade** que culmine em um relatório técnico completo". §5 cobre 18 camadas, várias com 6+ sub-itens. §6.2 prevê 11 seções no relatório final.
- **Problema:** A escala do entregável é compatível com um DS corporativo (banco grande, app B2C nacional). O CMSMRI é Coordenadoria de município de ~85 mil habitantes (RAPS regional), com equipe ~45 profissionais (CLAUDE.md global §1). Há descompasso entre ambição documental e capacidade de operacionalização. O risco não é falhar em qualidade, é produzir um documento que não será mantido — e cuja manutenção a longo prazo (v2, v3) nunca chegará por falta de owner técnico.
- **Impacto:** ROI cognitivo decrescente. Possível percepção pela liderança política (prefeito, secretário) de desproporcionalidade entre esforço de planejamento e impacto na ponta.
- **Correção proposta para v1.1:**
  1. Adicionar §1.4 — **"Calibração de profundidade"**:
     > A profundidade de cada camada é proporcional ao volume de uso institucional. Camadas críticas (cor, tipografia, voz, governança, acessibilidade) recebem tratamento completo. Camadas opcionais (som, movimento, ilustração) são marcadas como `[diferida v2]` quando não há uso imediato planejado.
  2. Em §6, adicionar nível **"Relatório MVP"** (cobre 5–6 camadas críticas) como entrega-âncora, complementado pelo relatório completo apenas se houver demanda explícita.
  3. Em §6.4, adicionar critério: "Cada camada não-crítica tem decisão explícita: incluir agora / diferir / dispensar".

---

#### [A11] Governança do próprio prompt subspecificada

- **Severidade:** Médio
- **Lente:** L8 (ciclo de vida)
- **Seção(ões) afetada(s):** §12 (linhas 499–519)
- **Evidência:** §12 declara `proxima_revisao: 2026-07-26 (trimestral)` e lista gatilhos de revisão extraordinária. Não define: quem revisa, como, onde fica registrada a versão anterior, como o agente em sessão tem ciência da versão vigente.
- **Problema:** §5.17 define governança *do design system*, mas governança *do system prompt* fica órfã. Risco prático: Caio começa um ciclo de uso com v1.0, atualiza para v1.1 a partir desta revisão, e em 3 meses não lembra qual versão estava ativa em qual sessão. Sem changelog operacional vinculado, perde-se rastreabilidade.
- **Impacto:** Acúmulo de débito de governança meta. Em 6–12 meses, o prompt pode estar tão divergente do uso real quanto um documento abandonado.
- **Correção proposta para v1.1:**
  1. Em §12, adicionar campo `localizacao_repo: brain-dump.md (raiz)` e `politica_de_versao: alterações > 5 linhas geram bump de minor`.
  2. Adicionar §12.1 — **"Workflow de atualização do prompt"**: branch `claude/prompt-vN`, PR com diff e changelog, merge requer aprovação humana.
  3. Adicionar §12.2 — **"Bootstrapping de sessão"**: o agente, ao ser ativado, declara primeiro a versão do prompt que está usando e referencia o changelog mais recente.

---

#### [A12] §6.4 conflita parcialmente com §11

- **Severidade:** Médio
- **Lente:** L1 (auto-consistência)
- **Seção(ões) afetada(s):** §6.4 (linhas 296–304), §11.1 (linhas 469–476), §11.2 (linhas 478–484)
- **Evidência:** §6.4 lista "Sinais vitais do §11 foram verificados (pré e pós)". §11.1 é "antes de cada entrega substantiva", §11.2 é "após cada entrega substantiva".
- **Problema:** §11 é definido como ciclo *por entrega*, mas §6.4 trata como gate único de "pronto". Se o ciclo é por entrega e o relatório tem múltiplas entregas (Drafts 0, v0.1, v0.2, v0.3, v1.0), §11 deveria rodar 5 vezes. §6.4 não diz isso. Inconsistência operacional.
- **Impacto:** Ambiguidade em quantos ciclos de checagem de §11 são necessários. Provavelmente o agente fará 1, declarando que "verificou §11", quando o desenho original prevê N.
- **Correção proposta para v1.1:**
  1. Em §11, declarar explicitamente: "§11 roda em **cada Draft entregue ao stakeholder**, nunca apenas no final".
  2. Em §6.4, esclarecer: "§11 verificado em cada Draft, com registro do resultado no changelog interno".
  3. Adicionar campo de controle: cada Draft tem header com `§11.1: ✅/⚠️/❌` e `§11.2: ✅/⚠️/❌`.

---

### 3.4 Baixos

#### [A13] Inconsistências menores de nomenclatura

- **Severidade:** Baixo
- **Lente:** L1 (auto-consistência)
- **Seção(ões) afetada(s):** §9.2 (linhas 411–415)
- **Evidência:** Lista de MCPs em §9.2:
  - "DOCLING" em maiúsculas (linha 413). Nome canônico do projeto é "Docling" (IBM Research).
  - "Windows-MCP / system-files" — nome híbrido não-canônico; o servidor MCP padrão para Windows é diferente de "system-files".
  - "context7" em minúsculas — nome do produto é "Context7" capitalizado.
- **Problema:** Pequenas falhas de canonicidade dificultam confronto com instalação real e parecem alucinatórias se confrontadas com documentação oficial.
- **Impacto:** Marginal. Custo de correção ~5min.
- **Correção proposta para v1.1:** Padronizar grafia: `Docling`, `Context7`, e identificar nome canônico do MCP de Windows em uso (ex.: `mcp-windows-cli` se for o caso).

---

#### [A14] Termo "diretor executivo" colide com instrução de não-substituir humanos

- **Severidade:** Baixo
- **Lente:** L12 (humano × IA), L1 (auto-consistência)
- **Seção(ões) afetada(s):** §1.1 (linha 15)
- **Evidência:** §1.1 abre com: "Você é um agente de IA [...] configurado para atuar como **diretor executivo** de uma equipe interdisciplinar internacional simulada".
- **Problema:** "Diretor executivo" carrega conotação de autoridade decisória — a frase imediatamente seguinte (linha 17) reverte: "você não é um designer humano nem substitui equipes". A oscilação enfraquece o framing.
- **Impacto:** Pequeno deslize retórico, mas em contexto público brasileiro (responsabilização administrativa) palavras carregam peso. Coerência com §1.1 §2 ("Você não é um designer humano") aumenta com termo mais sóbrio.
- **Correção proposta para v1.1:** Substituir "diretor executivo" por "**preparador técnico**", "**maestro de planejamento**" ou "**curador analítico**", mantendo o restante.

---

## 4. Achados por Seção do `brain-dump.md`

Mapeamento rápido de quais achados tocam cada seção, para auxiliar edição cirúrgica:

| Seção | Achados aplicáveis | Carga total |
|---|---|---|
| §1. Identidade e Missão | A02, A14 | Média |
| §2. Contexto Institucional | — | Nenhuma |
| §3. Equipe Simulada | A01, A06 | Média-alta |
| §4. Frameworks | A01 | Média |
| §5. Escopo (18 camadas) | A03, A04, A07, A09, A10 | **Alta — concentra a maioria das correções** |
| §6. Entregável | A01, A08, A10, A12 | Alta |
| §7. Processo em Fases | A01, A02 | Alta |
| §8. Critérios de Qualidade | A03, A08 | Média |
| §9. Arsenal | A05, A13 | Média |
| §10. Guardrails | A04, A07 | Média |
| §11. Sinais Vitais | A03, A12 | Baixa |
| §12. Metadados | A11 | Baixa |

**Concentração:** §5 e §6 são os hotspots — fazem sentido como alvo prioritário do patch v1.1.

---

## 5. Riscos Sistêmicos (não atribuíveis a uma seção única)

### 5.1 Planning paralysis

A combinação de 11 fases + 3 ciclos + 13 papéis + 18 camadas é típica de framework de consultoria enterprise. Para um stakeholder solo neurodivergente (TDAH desatento, conforme CLAUDE.md global §1) sem equipe de design contratada, o risco maior **não é entregar com baixa qualidade — é nunca entregar**. O brain-dump não tem mecanismo anti-procrastinação embutido (ex.: time-boxing, MVP first, regra dos 80/20 explícita).

**Mitigação proposta:** importar do CLAUDE.md global §5 a regra de suficiência (`≥ 94/100 → entregar`) e adicionar **time-box explícito por fase** em §7.

### 5.2 Duplicação com CLAUDE.md global

Vários elementos do brain-dump (Smart Brevity, BLUF, hierarquia de evidências, anti-alucinação, safety net BR, limites absolutos) são também regras do CLAUDE.md global de Caio. Risco de divergência entre ambos quando atualizados em momentos diferentes.

**Mitigação proposta:** em §1 do brain-dump, declarar explicitamente: "este prompt **estende** as regras do CLAUDE.md global, não as substitui; em caso de conflito, prevalece o CLAUDE.md global". Marcar regras herdadas com `[herdado de CLAUDE.md §X]` em vez de duplicá-las.

### 5.3 Ausência de integração com RAPS 4.0

O CLAUDE.md global §6 cita RAPS 4.0 (jan/2026–abr/2028) como projeto estratégico-âncora. O brain-dump menciona RAPS apenas como contexto regional (§2.2), sem integrar o cronograma do DS ao cronograma do RAPS 4.0. Possível desalinhamento: o DS pode estar pronto antes ou depois do marco onde seria mais útil (ex.: lançamento de novos equipamentos).

**Mitigação proposta:** adicionar §2.4 — "Alinhamento com Cronograma RAPS 4.0", ancorando marcos de entrega do DS aos marcos do programa estratégico.

### 5.4 Inflação de processo > maturidade institucional

O CMSMRI, como Coordenadoria recente, pode não ter ainda missão/visão/valores formalmente aprovados (§2.3 marca todos como "a coletar"). Construir 18 camadas de DS sobre fundações institucionais incompletas é construir andaime sobre fundação. Há ordem de operações implícita: primeiro consolidar o institucional formal, depois o DS.

**Mitigação proposta:** em §7, adicionar Fase **-1** — "Pré-condições institucionais": confirmar que missão/visão/valores estão formalizados (ato administrativo, decreto municipal, instrução normativa) antes de iniciar Fase 0.

---

## 6. Patch sugerido para `brain-dump.md` v1.1

Lista priorizada de edits concretos, prontos para serem aplicados quando o stakeholder aprovar:

### 6.1 Bloqueadores (resolver antes de Fase 0)

| Edit | Local | Ação |
|---|---|---|
| E01 | §3 | Adicionar parágrafo de atenção ontológica (cf. A06) |
| E02 | §4.5 | Substituir "mínimo 3 ciclos" por "1 ciclo + 1 revisão humana" |
| E03 | §7 | Inserir gates humanos após Fases 1, 2, 5 |
| E04 | §1.3, §5.4, §5.14, §8, §10.1, §11.1 | Trocar "WCAG 2.1 AA" por "WCAG 2.2 AA + eMAG 3.1" |
| E05 | §5.14 | Adicionar LIBRAS, audiodescrição, Decreto 5.296/2004, Lei 13.146/2015 art. 63 |

### 6.2 Altos (resolver antes de Fase 4)

| Edit | Local | Ação |
|---|---|---|
| E06 | §10 | Adicionar §10.5 — Protocolo de Dados Pessoais Sensíveis |
| E07 | §9.1 | Marcar status de cada skill (`[disponível]` / `[a verificar]`) |
| E08 | §9 | Adicionar §9.4 — Pré-voo de tooling |
| E09 | §5 | Adicionar §5.19 — Licenciamento e Propriedade Intelectual |
| E10 | §10.2 | Expandir cláusula de "cópia de identidade" para cobrir derivação não-autorizada |
| E11 | §8 | Substituir tabela atual por rubrica 10 eixos × cutoff 94/100 |

### 6.3 Médios (até v1.1)

| Edit | Local | Ação |
|---|---|---|
| E12 | §5 | Adicionar §5.20 — Comunicação em Saúde Mental de Alta Sensibilidade |
| E13 | §5 | Adicionar §5.21 — Educação Permanente e Capacitação |
| E14 | §1 | Adicionar §1.4 — Calibração de profundidade |
| E15 | §6 | Adicionar nível "Relatório MVP" |
| E16 | §12 | Adicionar §12.1 e §12.2 — workflow de atualização e bootstrapping |
| E17 | §11 | Declarar que §11 roda por Draft, não apenas no final |

### 6.4 Baixos (opcional)

| Edit | Local | Ação |
|---|---|---|
| E18 | §9.2 | Padronizar grafia (Docling, Context7, MCP Windows canônico) |
| E19 | §1.1 | Trocar "diretor executivo" por "preparador técnico" |

---

## 7. Itens para Validação Humana de Caio

Pontos onde a revisão **não pode decidir solo** e exige posicionamento do stakeholder:

1. **Profundidade vs porte (A10):** o relatório completo de 18 camadas é desejado, ou um MVP de 5–6 camadas é mais útil para a Coordenadoria neste momento? Esta é decisão estratégica, não técnica.
2. **Cronograma vs RAPS 4.0 (5.3):** existe um marco do RAPS 4.0 ao qual o DS precisa estar alinhado? Lançamento de novo equipamento? Auditoria? Apresentação ao CMS?
3. **Risco político de over-documentation (A10):** há leitura política do prefeito/secretário a antecipar? O esforço pode ser percebido como desproporcional ao porte da Coordenadoria?
4. **Gating humano (A02):** Caio tem banda atencional para 3 gates humanos (Fases 1, 2, 5) além do gate final (Fase 9)? Caso negativo, qual subset prioritário?
5. **Skills indisponíveis (A05):** vale rodar inventário formal de skills antes da Fase 0, ou aceitar fallback para prompts internos?
6. **Tom da equipe simulada (A06):** o ganho heurístico dos 13 papéis compensa o risco de falsa autoridade? Considerar reduzir para 5–7 papéis essenciais.
7. **WCAG 2.2 vs 2.1 (A03):** alinhar com possível política digital municipal já existente; se Extrema-MG já adota outro padrão, refletir.
8. **Multilinguismo (A09):** confirmar via dados Censo 2022 a presença de comunidades migrantes em Extrema antes de codificar política de tradução.
9. **Aprovação do patch v1.1:** dos 19 edits listados em §6, quais aceitar? A revisão recomenda **todos os bloqueadores e altos**; médios e baixos podem ser deferidos para revisão trimestral.

---

## 8. Encerramento e Próximos Passos

Esta revisão é meta — examinou o instrumento, não executou o processo. Antes de qualquer Fase 0, recomenda-se:

1. **Caio lê este documento** (estimativa: 25–35 min de leitura cuidadosa).
2. **Caio decide** sobre os 9 itens de §7 acima.
3. **Aplicar patch v1.1** ao `brain-dump.md` conforme decisões aceitas.
4. **Bump de versão:** `v1.0 → v1.1` em §12 com changelog explícito referenciando esta revisão.
5. Só então: ativar agente em Fase 0.

**Custo estimado de aplicar todos os bloqueadores + altos:** 60–90 min de edição em `brain-dump.md` (cirúrgica, com `Edit`/`str_replace`).

---

## 9. Metadados desta Revisão

```yaml
artefato: brain-dump-review.md
fonte: brain-dump.md v1.0 (linhas 1-529)
data_revisao: 2026-04-27
revisor: Claude (Anthropic) sob direção de Caio Villani França
escopo: meta-revisão do system prompt; sem execução
lentes_aplicadas: 12 (L1-L12)
achados_total: 14
distribuicao:
  bloqueador: 3
  alto: 5
  medio: 4
  baixo: 2
patch_proposto: 19 edits (E01-E19) em 6.1-6.4
proxima_acao: aprovação humana dos itens em §7 antes de Fase 0
```

— Fim da revisão crítica.
