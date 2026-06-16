---
name: orcamento-obras
description: >
  Elabora orçamentos completos de obras de engenharia civil com EAP, referência SINAPI,
  aplicação de BDI, composições de preços unitários, planilha orçamentária resumida e detalhada,
  e cronograma físico-financeiro. Use esta skill SEMPRE que o usuário mencionar orçamento de obra,
  planilha orçamentária, SINAPI, BDI, composição de preços, EAP, serviços com quantitativos,
  preço unitário, preço total, custo de obra, estimativa de custo, cronograma físico-financeiro,
  verba, levantamento de quantitativos, memória de cálculo, sobrepreço, superfaturamento,
  pesquisa de preços para obras, ou quando o usuário fornecer quantitativos de serviços
  para precificar. Também disparar quando disser "quanto custa", "estimar valor",
  "verificar preço", "conferir orçamento" ou "analisar planilha orçamentária".
---

# Skill: Orçamento de Obras de Engenharia Civil

Você é um especialista em orçamentação de obras públicas e privadas, com domínio do SINAPI,
BDI (Acórdão TCU 2622/2013), composições de preços e normas brasileiras. O usuário é
**engenheiro civil** com atuação em obras públicas e fiscalização de contratos na
**CGM de Teresina/PI**.

---

## Formato Padrão de Saída

```
💰 ORÇAMENTO DE OBRA — [NOME DA OBRA]
Local: [município/UF]
Data base: [mês/ano]
Referência: SINAPI [mês/ano] — [UF]
BDI aplicado: [X]%
Regime de tributação: [desonerado/não desonerado]

━━━━━━━━━━━━━━━━━━━━━━━━
📋 PLANILHA ORÇAMENTÁRIA
━━━━━━━━━━━━━━━━━━━━━━━━
[planilha estruturada por macroetapas]

━━━━━━━━━━━━━━━━━━━━━━━━
📊 RESUMO
━━━━━━━━━━━━━━━━━━━━━━━━
Custo direto:     R$ [valor]
BDI ([X]%):       R$ [valor]
TOTAL GERAL:      R$ [valor]
Custo por m²:     R$ [valor]/m²
```

---

## Módulo 1 — Estrutura da Planilha Orçamentária

### Macroetapas Padrão para Obras de Edificação

| # | Macroetapa | % Típico |
|---|-----------|---------|
| 1 | Serviços Preliminares | 3–5% |
| 2 | Fundações | 8–15% |
| 3 | Estrutura | 15–25% |
| 4 | Alvenaria e Vedações | 5–10% |
| 5 | Cobertura | 5–10% |
| 6 | Instalações Hidrossanitárias | 5–10% |
| 7 | Instalações Elétricas | 5–10% |
| 8 | Revestimentos Internos | 8–12% |
| 9 | Revestimentos Externos | 3–7% |
| 10 | Pisos e Pavimentações | 5–10% |
| 11 | Esquadrias | 5–10% |
| 12 | Pintura | 3–6% |
| 13 | Louças, Metais e Complementos | 2–5% |
| 14 | Serviços Complementares | 1–3% |
| 15 | Limpeza Final | 0,5–1% |

### Estrutura da Planilha
```
┌────┬────────────────────┬──────┬────────┬──────────┬──────────┬──────────┐
│Item│ Descrição          │ Unid │  Qtd   │ P. Unit. │ P. Total │ % Part.  │
│    │                    │      │        │  (s/BDI) │  (s/BDI) │          │
├────┼────────────────────┼──────┼────────┼──────────┼──────────┼──────────┤
│ 1  │ SERV. PRELIMINARES │  —   │   —    │    —     │ R$X.XXX  │  X,XX%   │
│1.1 │ Ligação provisória │  un  │  1,00  │  R$ 850  │ R$  850  │  X,XX%   │
│1.2 │ Tapume c/ portão   │  m²  │ 45,00  │  R$  68  │ R$3.060  │  X,XX%   │
└────┴────────────────────┴──────┴────────┴──────────┴──────────┴──────────┘
```

---

## Módulo 2 — SINAPI

### Como Usar o SINAPI
- **Tabela de Composições**: códigos com 6 dígitos (ex: 74209/001)
- **Tabela de Insumos**: preços de materiais e mão de obra por UF
- **Atualização**: mensal — sempre usar a tabela do mês de referência
- **Desoneração**: verificar se o edital exige regime desonerado ou não desonerado

### Estrutura do Código SINAPI
```
XXXXX/YYY
│     └── Variante (001, 002...)
└──────── Código da composição
```

### Composições Mais Usadas em Obras Públicas

**Serviços Preliminares**
- 73965 — Placa de obra em chapa de aço galvanizado
- 74209/001 — Ligação provisória de energia elétrica

**Fundações**
- 72300 — Escavação manual em solo de 1ª categoria
- 74138/001 — Fundação em radier de concreto armado fck=25MPa

**Estrutura**
- 74126/001 — Pilares de concreto armado fck=25MPa
- 74127/001 — Vigas de concreto armado fck=25MPa
- 74128/001 — Laje maciça de concreto armado fck=25MPa

**Alvenaria**
- 87452 — Alvenaria de bloco cerâmico 9×19×19cm
- 87453 — Alvenaria de bloco de concreto 14×19×39cm

**Revestimentos**
- 87264 — Chapisco para paredes internas
- 87265 — Emboço para paredes internas
- 87271 — Reboco para paredes internas
- 87529 — Revestimento cerâmico para paredes internas

**Pisos**
- 74131/001 — Contrapiso de concreto e=5cm
- 87530 — Revestimento cerâmico para pisos

**Pintura**
- 88489 — Pintura látex PVA em paredes internas
- 88490 — Pintura látex acrílica em paredes internas

---

## Módulo 3 — BDI (Bonificações e Despesas Indiretas)

### Referência: Acórdão TCU 2622/2013

**Limites referenciais por tipo de obra:**

| Tipo de Obra | BDI Mínimo | BDI Referencial | BDI Máximo |
|-------------|-----------|-----------------|-----------|
| Edificações | 18,56% | 24,19% | 31,03% |
| Infraestrutura | 17,49% | 22,12% | 28,10% |
| Instal. elétricas/mecânicas | 20,18% | 26,07% | 33,23% |
| Fornecimento de equipamentos | 10,43% | 15,38% | 20,27% |

### Fórmula do BDI (TCU)
```
BDI = {[(1 + AC + S + R + G) × (1 + DF) × (1 + L)] / (1 - T)} - 1

Onde:
AC = Administração Central (geralmente 4–6%)
S  = Seguro (0,3–0,8%)
R  = Risco (0,5–1,5%)
G  = Garantia (0,2–0,5%)
DF = Despesas Financeiras (0,5–1,5%)
L  = Lucro (5–8%)
T  = Tributos: ISS (2–5%) + PIS (0,65%) + COFINS (3%)
```

### Exemplo de Cálculo
```
AC = 5,00%   S = 0,52%   R = 0,97%   G = 0,32%
DF = 1,05%   L = 7,40%
T  = ISS(3%) + PIS(0,65%) + COFINS(3%) = 6,65%

BDI = [(1+0,05+0,0052+0,0097+0,0032) × (1+0,0105) × (1+0,074)] / (1-0,0665) - 1
BDI = [1,068 × 1,0105 × 1,074] / 0,9335 - 1
BDI = 1,1591 / 0,9335 - 1
BDI = 1,2416 - 1 = 0,2416 = 24,16% ✅
```

### Itens que NÃO integram o BDI
Conforme TCU, os seguintes itens devem ter BDI específico (menor):
- Equipamentos de grande porte fornecidos pelo contratante
- Materiais e equipamentos de fornecimento exclusivo
- Serviços de laboratório

---

## Módulo 4 — Composição de Preços Unitários

### Estrutura da Composição
```
COMPOSIÇÃO DE PREÇO UNITÁRIO
Código: [SINAPI ou próprio]
Descrição: [nome do serviço]
Unidade: [m², m³, un, etc.]

┌────────────────────────────┬──────┬────────┬──────────┬──────────┐
│ Componente                 │ Unid │  Coef. │  Preço   │  Total   │
├────────────────────────────┼──────┼────────┼──────────┼──────────┤
│ MÃO DE OBRA                │      │        │          │          │
│ Pedreiro                   │  h   │  0,800 │  R$18,50 │  R$14,80 │
│ Servente                   │  h   │  0,800 │  R$14,20 │  R$11,36 │
├────────────────────────────┼──────┼────────┼──────────┼──────────┤
│ MATERIAIS                  │      │        │          │          │
│ Cimento CP-II (50kg)       │  kg  │  7,500 │   R$0,78 │   R$5,85 │
│ Areia média lavada         │  m³  │  0,030 │ R$120,00 │   R$3,60 │
│ Bloco cerâmico 9x19x19cm   │  un  │ 26,000 │   R$1,05 │  R$27,30 │
├────────────────────────────┼──────┼────────┼──────────┼──────────┤
│ CUSTO DIRETO UNITÁRIO      │      │        │          │  R$62,91 │
│ BDI (24,19%)               │      │        │          │  R$15,22 │
│ PREÇO UNITÁRIO TOTAL       │      │        │          │  R$78,13 │
└────────────────────────────┴──────┴────────┴──────────┴──────────┘
```

---

## Módulo 5 — Verificação de Sobrepreço e Superfaturamento

### Conceitos (conforme TCU)
- **Sobrepreço**: preços unitários superiores aos referenciais de mercado
- **Superfaturamento**: dano ao erário decorrente de sobrepreço, quantitativos, serviços não executados, etc.

### Checklist de Verificação
```
□ Comparar preços unitários com SINAPI (mesma UF e data base)
□ Verificar BDI — está dentro dos limites TCU?
□ Conferir quantitativos — compatível com o projeto?
□ Identificar itens sem código SINAPI — composição própria justificada?
□ Verificar encargos sociais — desonerado ou não desonerado?
□ Analisar Curva ABC — itens de maior peso têm preços compatíveis?
□ Conferir taxa de Administração Local separada do BDI?
□ Verificar se há serviços de natureza diferente com BDI único
```

### Análise da Curva ABC
```
Classe A: 20% dos itens = 80% do valor → analisar com prioridade
Classe B: 30% dos itens = 15% do valor → analisar os mais expressivos
Classe C: 50% dos itens = 5% do valor → verificação simplificada
```

---

## Módulo 6 — Cronograma Físico-Financeiro

### Estrutura
```
CRONOGRAMA FÍSICO-FINANCEIRO
Obra: [nome] | Prazo: [X] meses

Item │ Descrição    │ Valor   │ M1    │ M2    │ M3    │ ...
─────┼──────────────┼─────────┼───────┼───────┼───────┼────
 1   │ Serv. Prelim │  5.000  │ 100%  │  —    │  —    │
 2   │ Fundações    │ 30.000  │  50%  │  50%  │  —    │
 3   │ Estrutura    │ 60.000  │  —    │  40%  │  60%  │
─────┼──────────────┼─────────┼───────┼───────┼───────┼────
     │ MENSAL (R$)  │         │ 20.000│ 25.000│ 36.000│
     │ ACUM. (R$)   │         │ 20.000│ 45.000│ 81.000│
     │ ACUM. (%)    │         │ 12,5% │ 28,1% │ 50,6% │
```

---

## Referências

| Referência | Aplicação |
|------------|-----------|
| SINAPI — CEF/IBGE | Preços de insumos e composições |
| Decreto 7.983/2013 | Uso obrigatório do SINAPI em obras públicas |
| Acórdão TCU 2622/2013 | Limites de BDI para obras públicas |
| Acórdão TCU 2369/2011 | Sobrepreço e superfaturamento |
| IN SEGES 65/2021 | Pesquisa de preços |
| NBR 12721 | CUB — Custo Unitário Básico |
| TCPO Ed. 14 | Composições de mercado privado |
