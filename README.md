# 🏗️ engenharia-civil-skills

> **Agent Skills para Engenharia Civil Pública Brasileira** — Skills profissionais para Claude Code, Claude Desktop e demais agentes compatíveis com o formato SKILL.md.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Skills: 3](https://img.shields.io/badge/Skills-3-blue.svg)](#skills-disponíveis)
[![Compatível com](https://img.shields.io/badge/Compatível%20com-Claude%20Code%20%7C%20Claude%20Desktop-blueviolet.svg)](#compatibilidade)

---

## O que é este repositório?

Este repositório reúne **Agent Skills especializadas em engenharia civil pública brasileira**, desenvolvidas por um Engenheiro Civil com mais de 20 anos de experiência em obras públicas, fiscalização de contratos e controladoria municipal.

As skills seguem o **formato aberto SKILL.md** — padrão adotado pelo ecossistema de agentes de IA — e funcionam no Claude Code, Claude Desktop, Cursor, Copilot e demais ferramentas compatíveis.

Pense nelas como **especialistas digitais** treinados para atuar como fiscal de contrato, orçamentista sênior e gestor de obras públicas — com domínio da legislação e normas brasileiras.

---

## Skills Disponíveis

| # | Skill | Descrição | Status |
|---|-------|-----------|--------|
| 01 | [`licitacoes-14133`](./skills/licitacoes-14133/SKILL.md) | Análise de processos licitatórios e contratos sob a Lei 14.133/2021 — ETP, TR, editais, aditivos, reequilíbrio, fiscalização, pareceres técnicos CGM | ✅ v1.0 |
| 02 | [`gestao-obras`](./skills/gestao-obras/SKILL.md) | Gerenciamento completo de obras públicas — Gantt, PERT/CPM, boletins de medição, diários de obra, relatórios de fiscalização, controle de etapas | ✅ v1.0 |
| 03 | [`orcamento-obras`](./skills/orcamento-obras/SKILL.md) | Elaboração de orçamentos de obras com SINAPI, BDI (fórmula TCU), composições de preços, EAP, planilha orçamentária e cronograma físico-financeiro | ✅ v1.0 |

---

## Base Técnica

As skills são desenvolvidas com base em:

| Referência | Aplicação |
|------------|-----------|
| **Lei 14.133/2021** | Nova Lei de Licitações e Contratos Administrativos |
| **SINAPI** — CEF/IBGE | Preços de insumos e composições para obras públicas |
| **Decreto 7.983/2013** | Uso obrigatório do SINAPI em obras federais |
| **Acórdão TCU 2622/2013** | Limites de BDI para obras públicas |
| **Decreto 9.983/2019** | Implantação do BIM no setor público brasileiro |
| **ABNT NBR 12721** | CUB — Custo Unitário Básico |
| **NR-18** | Segurança em obras de construção civil |

---

## Como Instalar

### Opção 1 — Manual (Windows PowerShell)

```powershell
# licitacoes-14133
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\licitacoes-14133"
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/frankpessoa-png/engenharia-civil-skills/main/skills/licitacoes-14133/SKILL.md" -OutFile "$env:USERPROFILE\.claude\skills\licitacoes-14133\SKILL.md" -UseBasicParsing

# gestao-obras
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\gestao-obras"
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/frankpessoa-png/engenharia-civil-skills/main/skills/gestao-obras/SKILL.md" -OutFile "$env:USERPROFILE\.claude\skills\gestao-obras\SKILL.md" -UseBasicParsing

# orcamento-obras
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.claude\skills\orcamento-obras"
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/frankpessoa-png/engenharia-civil-skills/main/skills/orcamento-obras/SKILL.md" -OutFile "$env:USERPROFILE\.claude\skills\orcamento-obras\SKILL.md" -UseBasicParsing
```

### Opção 2 — Linux/Mac

```bash
# licitacoes-14133
mkdir -p ~/.claude/skills/licitacoes-14133
curl -o ~/.claude/skills/licitacoes-14133/SKILL.md \
  https://raw.githubusercontent.com/frankpessoa-png/engenharia-civil-skills/main/skills/licitacoes-14133/SKILL.md

# gestao-obras
mkdir -p ~/.claude/skills/gestao-obras
curl -o ~/.claude/skills/gestao-obras/SKILL.md \
  https://raw.githubusercontent.com/frankpessoa-png/engenharia-civil-skills/main/skills/gestao-obras/SKILL.md

# orcamento-obras
mkdir -p ~/.claude/skills/orcamento-obras
curl -o ~/.claude/skills/orcamento-obras/SKILL.md \
  https://raw.githubusercontent.com/frankpessoa-png/engenharia-civil-skills/main/skills/orcamento-obras/SKILL.md
```

---

## Como Usar

### Invocação explícita (Claude Code)

```
/licitacoes-14133
/gestao-obras
/orcamento-obras
```

### Invocação por linguagem natural

```
"Analise este processo licitatório e identifique riscos sob a Lei 14.133/2021"
"Gere um boletim de medição para a obra com os seguintes serviços executados"
"Monte uma planilha orçamentária com SINAPI para reforma de UBS em Teresina/PI"
"Elabore um parecer técnico sobre este aditivo contratual"
"Crie o cronograma físico-financeiro para esta obra de 6 meses"
```

---

## Compatibilidade

| Ferramenta | Suporte | Invocação |
|------------|---------|-----------|
| **Claude Code** | ✅ Nativo | `/skill-name` ou linguagem natural |
| **Claude Desktop** | ✅ Via configurações | Linguagem natural |
| **Cursor** | ✅ Via `.cursor/skills/` | Linguagem natural |
| **GitHub Copilot** | ✅ Via `.github/skills/` | `/skill-name` no chat |

---

## Estrutura do Repositório

```
engenharia-civil-skills/
├── README.md
├── LICENSE
└── skills/
    ├── licitacoes-14133/
    │   └── SKILL.md
    ├── gestao-obras/
    │   └── SKILL.md
    └── orcamento-obras/
        └── SKILL.md
```

---

## Sobre o Autor

**Frank Pessoa Avelino** — Engenheiro Civil | Fiscal de Contratos | CGM Teresina/PI

- 🏛️ Engenheiro Civil concursado na Controladoria Geral do Município de Teresina/PI
- 📋 Especialista em fiscalização de contratos e obras públicas sob a Lei 14.133/2021
- 🎓 Especializações em Gestão de Projetos e Gestão de Negócios (FGV) e Gestão da Construção (UNIP)
- 🔧 +20 anos de experiência em obras públicas, orçamentação e licitações
- 📦 GitHub: [@frankpessoa-png](https://github.com/frankpessoa-png)

---

## Contribuição

Contribuições são bem-vindas! Se você é profissional da engenharia civil ou da área jurídica de licitações e quer melhorar ou adicionar skills:

1. Faça um fork do repositório
2. Crie uma branch: `git checkout -b feat/nome-da-skill`
3. Adicione ou edite o `SKILL.md` na pasta correta
4. Abra um Pull Request descrevendo a melhoria

---

## Licença

MIT License — veja o arquivo [LICENSE](./LICENSE) para detalhes.
