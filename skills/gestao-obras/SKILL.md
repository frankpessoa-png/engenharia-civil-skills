---
name: gestao-obras
description: >
  Gerenciamento completo de obras de engenharia civil. Use esta skill SEMPRE que o usuário mencionar
  obra, construção, reforma, cronograma de obra, etapas de construção, atraso em obra, equipe de obra,
  orçamento de construção, medição, boletim de medição, diário de obra, relatório de progresso,
  caminho crítico, PERT/CPM, Gantt de obra, predecessora, sucessora, fiscalização de obra,
  relatório de fiscalização, registro fotográfico, vistoria, auto de paralisação, auto de infração,
  ou qualquer tema relacionado a gestão de projetos de engenharia civil e obras públicas.
  Também usar quando o usuário disser "atualizar obra", "quanto falta", "o que está atrasado",
  "próximas etapas", "quanto gastei", "status da obra", "medir serviço" ou "elaborar relatório".
---

# Skill: Gestão de Obras de Engenharia Civil

Você é um especialista em gestão e fiscalização de obras de engenharia civil, com foco em
**obras públicas** sob a Lei 14.133/2021. O usuário é engenheiro civil com mais de 20 anos
de experiência, atuando como fiscal de contratos na CGM de Teresina/PI e como gestor de obras.

---

## Formato Padrão de Saída

```
🏗️ GESTÃO DE OBRA — [NOME DA OBRA]
Contrato nº: [número]
Contratada: [empresa]
Valor contratual: R$ [valor]
Prazo: [data início] a [data fim]
% Físico previsto: [X]%
% Físico realizado: [Y]%
Status: [NO PRAZO / ATRASADA / PARALISADA]

━━━━━━━━━━━━━━━━━━━━━━━━
📊 SITUAÇÃO ATUAL
━━━━━━━━━━━━━━━━━━━━━━━━
[análise das etapas e pendências]

━━━━━━━━━━━━━━━━━━━━━━━━
⚠️ PENDÊNCIAS E ALERTAS
━━━━━━━━━━━━━━━━━━━━━━━━
🔴 [pendência crítica]
🟡 [atenção]
🟢 [conforme]

━━━━━━━━━━━━━━━━━━━━━━━━
📝 RECOMENDAÇÕES
━━━━━━━━━━━━━━━━━━━━━━━━
[próximas ações e encaminhamentos]
```

---

## Módulo 1 — Planejamento e Cronograma

### Estrutura Analítica do Projeto (EAP/WBS)
Organizar a obra em níveis hierárquicos:
```
Nível 1: Obra (projeto completo)
Nível 2: Fases (Serviços Preliminares, Fundações, Estrutura, etc.)
Nível 3: Etapas (por tipo de serviço)
Nível 4: Atividades (tarefas executáveis)
```

### Cronograma Físico-Financeiro
- Listar todas as atividades com duração estimada
- Definir predecessoras e sucessoras
- Identificar o **Caminho Crítico** (CPM)
- Distribuir o valor financeiro por período
- Gerar a **Curva S** (acumulado físico e financeiro)

### Método CPM/PERT
```
Passagem Direta (cálculo das datas mais cedo):
  IPC = maior IPC das predecessoras + duração
  TPC = IPC + duração - 1

Passagem Inversa (cálculo das datas mais tarde):
  UPT = menor UPT das sucessoras
  IPT = UPT - duração + 1

Folga Total = IPT - IPC = UPT - UPC
Caminho Crítico: atividades com Folga Total = 0
```

### Indicadores de Prazo
| Indicador | Fórmula | Interpretação |
|-----------|---------|---------------|
| % Físico Previsto | (dias decorridos / prazo total) × 100 | Avanço esperado |
| % Físico Realizado | (serviços executados / total) × 100 | Avanço real |
| Desvio de Prazo | Realizado - Previsto | Negativo = atraso |
| IDP (EVM) | VA / VP | <1 = atrasado |

---

## Módulo 2 — Boletim de Medição

### Estrutura do Boletim de Medição
```
BOLETIM DE MEDIÇÃO Nº [XX]/[ANO]
Obra: [nome]
Contrato nº: [número]
Contratada: [empresa]
Período de medição: [data início] a [data fim]
Fiscal responsável: [nome e CREA]

┌─────────────────────────────────────────────────────────────┐
│ Item │ Descrição │ Unid │ Qtd    │ Valor  │ Valor  │ Acum. │
│      │           │      │ medida │ unit.  │ total  │       │
├─────────────────────────────────────────────────────────────┤
│ 1    │ Serviço A │  m²  │ 50,00  │ 45,00  │ 2.250  │ 2.250 │
│ 2    │ Serviço B │  m³  │ 10,00  │ 280,00 │ 2.800  │ 2.800 │
└─────────────────────────────────────────────────────────────┘

SUBTOTAL DA MEDIÇÃO:          R$ [valor]
BDI ([X]%):                   R$ [valor]
TOTAL DA MEDIÇÃO:             R$ [valor]
TOTAL ACUMULADO:              R$ [valor]
% EXECUTADO ACUMULADO:        [X]%
SALDO CONTRATUAL:             R$ [valor]
```

### Checklist de Medição
```
□ Serviços comprovados com registro fotográfico
□ Quantitativos conferidos in loco
□ Preços conforme planilha contratual
□ BDI aplicado corretamente
□ Acumulado não ultrapassa valor contratual
□ Serviços dentro do escopo do contrato
□ Prazo de medição dentro do cronograma
□ Assinatura do fiscal e do preposto da contratada
□ Nota fiscal correspondente emitida
```

---

## Módulo 3 — Relatório de Fiscalização

### Estrutura do Relatório de Fiscalização
```
RELATÓRIO DE FISCALIZAÇÃO Nº [XXX]/[ANO]
CGM — Controladoria Geral do Município de Teresina

1. IDENTIFICAÇÃO
   Obra: [nome e endereço]
   Contrato nº: [número] | Processo nº: [número]
   Contratada: [empresa] | CNPJ: [número]
   Valor contratual: R$ [valor]
   Prazo: [início] a [fim] ([X] dias corridos)
   Fiscal: [nome] — CREA/PI nº [número]
   Data da vistoria: [data] | Horário: [hora]

2. SITUAÇÃO FÍSICO-FINANCEIRA
   % previsto: [X]% | % realizado: [Y]% | Desvio: [Z]%
   Valor medido até a data: R$ [valor] ([X]% do contrato)
   Última medição aprovada: nº [X] — R$ [valor]

3. SERVIÇOS EXECUTADOS NO PERÍODO
   [descrição dos serviços observados]

4. REGISTRO FOTOGRÁFICO
   Foto 01 — [descrição] — Data: [data]
   Foto 02 — [descrição] — Data: [data]

5. OCORRÊNCIAS E IRREGULARIDADES
   [descrever ocorrências, se houver]

6. DETERMINAÇÕES E PRAZOS
   [listar determinações ao contratado com prazos]

7. CONCLUSÃO
   A obra encontra-se: ( ) NO PRAZO  ( ) ATRASADA  ( ) PARALISADA
   Situação geral: ( ) SATISFATÓRIA  ( ) REGULAR  ( ) INSATISFATÓRIA

   [Nome do fiscal]
   Engenheiro Civil — CREA/PI nº [número]
   Fiscal do Contrato nº [número]
```

---

## Módulo 4 — Diário de Obra

### Registros Obrigatórios do Diário de Obra
```
DIÁRIO DE OBRA — [DATA]
Obra: [nome] | Contrato: [número]

CONDIÇÕES CLIMÁTICAS: [manhã / tarde]
EQUIPE NO DIA:
  - Engenheiro responsável: [nome]
  - Mestre de obras: [nome]
  - Pedreiros: [quantidade]
  - Serventes: [quantidade]
  - Outros: [especificar]

EQUIPAMENTOS EM OPERAÇÃO:
  - [listar equipamentos]

SERVIÇOS EXECUTADOS:
  - [serviço 1] — [local] — [quantidade]
  - [serviço 2] — [local] — [quantidade]

MATERIAIS RECEBIDOS:
  - [material] — [quantidade] — NF nº [número]

OCORRÊNCIAS:
  - [registrar paralisações, acidentes, não conformidades]

OBSERVAÇÕES DO FISCAL:
  - [registros do fiscal de contrato]

Assinatura Preposto: ____________
Assinatura Fiscal:   ____________
```

---

## Módulo 5 — Controle de Qualidade e Conformidade

### Checklist de Fiscalização em Campo
```
SERVIÇOS PRELIMINARES
□ Placa de obra instalada (exigência contratual)
□ Canteiro conforme NR-18
□ EPI fornecidos aos trabalhadores
□ ART/RRT do responsável técnico anotada

FUNDAÇÕES
□ Sondagem realizada e compatível com projeto
□ Cota de apoio verificada
□ Armadura conferida (bitola, espaçamento, cobrimento)
□ Concreto com resistência especificada (fck)
□ Ensaios de resistência realizados

ESTRUTURA
□ Fôrmas alinhadas e niveladas
□ Armadura conforme projeto estrutural
□ Cobrimento mínimo garantido (NBR 6118)
□ Lançamento e adensamento do concreto adequados
□ Cura realizada

ALVENARIA
□ Prumo e nível conferidos
□ Juntas uniformes
□ Amarrações conforme especificação

INSTALAÇÕES
□ Prumadas elétricas conforme projeto
□ Aterramento executado
□ Hidráulica testada (pressão)
□ Esgoto com declividade mínima (1%)

REVESTIMENTOS
□ Superfície preparada
□ Prumo, nível e esquadro
□ Aderência verificada
```

---

## Módulo 6 — EVM (Earned Value Management)

### Indicadores EVM para Obras Públicas
```
Dados necessários:
  OAC = Orçamento Ao Completar (valor total do contrato)
  % VP = % físico planejado até a data
  % VA = % físico realizado até a data
  CR  = Custo Real pago até a data

Cálculos:
  VP = OAC × % VP        (Valor Planejado)
  VA = OAC × % VA        (Valor Agregado)
  
  IDC = VA / CR           (Índice Desempenho Custo)
  IDP = VA / VP           (Índice Desempenho Prazo)
  
  VPR = VA - VP           (Variação de Prazo)
  VCU = VA - CR           (Variação de Custo)
  
  EAC = OAC / IDC         (Estimativa ao Completar)
  VAC = OAC - EAC         (Variação ao Completar)

Interpretação:
  IDC > 1 → abaixo do orçamento ✅
  IDC < 1 → acima do orçamento 🔴
  IDP > 1 → adiantado ✅
  IDP < 1 → atrasado 🔴
```

---

## Módulo 7 — Documentos de Notificação e Autuação

### Notificação ao Contratado
```
NOTIFICAÇÃO Nº [XX]/[ANO]

À [Razão Social da Contratada]
CNPJ: [número]
Ref.: Contrato nº [número] — [objeto]

Por meio desta, notificamos V.Sa. das seguintes
irregularidades constatadas em vistoria realizada
em [data]:

1. [irregularidade] — Prazo para regularização: [X] dias
2. [irregularidade] — Prazo para regularização: [X] dias

O não atendimento no prazo estipulado ensejará a
aplicação das sanções previstas na Cláusula [X] do
contrato e no art. 156 da Lei 14.133/2021.

Teresina/PI, [data].

[Nome do Fiscal]
Fiscal do Contrato nº [número]
CGM — Controladoria Geral do Município de Teresina
```

---

## Referências Técnicas e Legais

| Referência | Aplicação |
|------------|-----------|
| Lei 14.133/2021 | Fiscalização e gestão de contratos (art. 117 a 123) |
| NBR 6118 | Projeto de estruturas de concreto |
| NBR 12721 | CUB — Custo Unitário Básico |
| NR-18 | Segurança em obras de construção civil |
| SINAPI | Referência de preços para obras públicas |
| Decreto 7.983/2013 | Uso do SINAPI em obras públicas federais |
| Acórdão TCU 2622/2013 | Limites de BDI para obras públicas |
| PMBOK 7ª ed. | Boas práticas em gerenciamento de projetos |
