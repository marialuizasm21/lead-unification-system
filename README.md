# Sistema Unificado de Qualificação de Leads

Sistema centralizado de qualificação desenvolvido com **engenharia de prompts e automação assistida por IA**, implementando 6 workflows integrados para eliminar descentralização, duplicidade e criar segmentação automática de leads.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/marialuizasm21)

---

## Skills

<div align="center">

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)
![Google Drive](https://img.shields.io/badge/Google_Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)
![Google Cloud](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=googlecloud&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Regex](https://img.shields.io/badge/Regex-000000?style=for-the-badge)
![GitHub Repo](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![VS Code](https://img.shields.io/badge/VS_Code-0078D4?style=for-the-badge&logo=visualstudiocode&logoColor=white)

</div>

---

## O Problema

O processo de qualificação operava através de **múltiplas planilhas descentralizadas** criadas individualmente para cada lista ou campanha.

| Problema | Impacto |
|---|---|
| 📂 Múltiplas planilhas sem padronização | Impossibilidade de acompanhamento consolidado |
| 🔒 Acesso restrito por planilha | Barreiras operacionais entre áreas |
| ♻️ Sem validação cruzada entre planilhas | Alto risco de qualificar o mesmo lead duas vezes |
| 📝 Estrutura diferente em cada planilha | Dossiês inconsistentes, difícil de comparar |

**Impacto:** Operação ineficiente, retrabalho constante, falta de visão estratégica.

---

## A Solução

Desenvolvi um **sistema unificado** que evoluiu progressivamente através de **4 versões** ao longo de 3 dias (12 horas total), implementando **6 automações integradas** — utilizando **Claude AI (Anthropic)** extensivamente para engenharia de prompts, arquitetura de código e otimização de workflows.

---

## Evolução do Sistema

### Versão 1 — Protótipo: Estrutura Base
> 4 scripts fundamentais que estabeleceram a base do sistema

- **Timestamp Automático** — registra data/hora ao atribuir responsável
- **Verificação de Duplicados** — valida nome E email com lógica temporal
- **Geração de Dossiê** — compila 14 campos em texto estruturado
- **Verificação em Base Master** — cruza com base externa de leads mapeados

### Versão 2 — Produção: Dossiê Profissional
> Transformação do dossiê simples em documento estruturado em 4 seções

- Expandiu de **14 → 24 campos** mapeados
- Adicionou cálculo de valor estimado com margem de segurança de 60%
- Benchmark completo de concorrência
- Função `validar()` para tratar campos vazios elegantemente

### Versão 3 — Inteligência e Segurança
> Camadas de inteligência e validação de contexto

- Dossiê expandido para **7 seções** estruturadas
- Lógica condicional: constrói frases apenas com campos preenchidos
- Validação de ambiente: scripts executam apenas na aba correta
- UX melhorada: verificação silenciosa, sem pop-ups intrusivos

### Versão Final — Sistema Completo com Segmentação Automática
> Modelo de segmentação automática baseado em regras de negócio

| Flag | Significado | Ação |
|:---:|---|---|
| 🔴 Red | Bad-fit definitivo | Descartar |
| 🟡 Yellow | Contrato ativo / timing específico | Aguardar |
| 🟢 Green | Sem impeditivos | Contato imediato |

- Trigger unificado consolida timestamp + flags em 1 função
- `calcularFlag()`: lógica hierárquica de prioridades
- `atualizarEmLote()`: processa base histórica completa com relatório

---

## Aplicação de IA no Projeto

**Claude AI (Anthropic)** foi utilizado em todas as 4 versões:

> **Prompt usado:** "Preciso criar uma função que valide duplicados por nome OU email, aplicando normalização de texto que remova acentos, sufixos corporativos e mantenha o registro mais antigo. Como estruturar essa lógica em Apps Script?"
>
> **→ Resultado:** função `verificarDuplicados()` com normalização NFD e lógica temporal

- Arquitetura de código e validação multicamadas via prompts estruturados
- Design de triggers inteligentes e lógicos hierárquicos de segmentação
- Identificação de casos extremos e depuração assistida
- Code review e sugestões de melhoria

---

## Resultados

### Quantitativos

| Métrica | Resultado |
|---|---|
| Automações integradas | **6** |
| Campos mapeados | **27** |
| Seções no dossiê | **7** |
| Qualificação centralizada | **100%** |
| Duplicidades em produção | **0** |
| Versões desenvolvidas | **4 em 3 dias** |
| Categorias de segmentação | **3 (Red/Yellow/Green)** |

### Qualitativos

- ✅ **Centralização total** — uma única fonte de verdade para toda a equipe
- ✅ **Zero retrabalho** — validação automática elimina qualificação duplicada
- ✅ **Democratização de acesso** — todos os membros na mesma base
- ✅ **Padronização absoluta** — qualidade consistente independente do operador
- ✅ **Segmentação automática** — flags eliminam interpretação subjetiva
- ✅ **Onboarding simplificado** — novos membros produzem desde o primeiro dia

> Sistema entregue e utilizado diariamente por toda a equipe de qualificação.

---

## Fluxo de Trabalho

> **1. Atribuição** → Timestamp automático registra data/hora
>
> **2. Preenchimento** → Sistema monitora edições em campos-chave
>
> **3. Duplicados** → Cruza nome + email com normalização de texto
>
> **4. Base Master** → Verificação silenciosa, sem interromper operação
>
> **5. Flags** → Red / Yellow / Green calculado automaticamente
>
> **6. Dossiê** → 27 campos compilados em 7 seções estruturadas
>
> **7. Lote (opcional)** → Processa base histórica completa com relatório

---

## Arquitetura dos Scripts

| Script | Responsabilidade |
|---|---|
| `onEdit()` | Trigger unificado — orquestra todas as automações |
| `verificarDuplicados()` | Validação por nome OU email com normalização NFD |
| `gerarDossie()` | Compila 27 campos em dossiê estruturado de 7 seções |
| `verificarBaseMaster()` | Integração cross-sheet com base externa |
| `calcularFlag()` | Lógica hierárquica Red/Yellow/Green |
| `atualizarEmLote()` | Processamento em massa com relatório de execução |

---

## Limitações & Próximos Passos

**Limitações atuais:**
- Estrutura de colunas fixa (mudanças exigem atualização de índices)
- Duplicados por similaridade fuzzy ainda não capturados
- Regras de flags hardcoded no código
- Performance em lote pode cair em bases acima de 1.000 registros

**Próximos passos:**
- [ ] Mapeamento dinâmico de colunas
- [ ] Fuzzy matching na validação de duplicados
- [ ] Regras de flags externalizadas para configuração
- [ ] Integração com APIs de LLMs para enriquecimento automático
- [ ] Scoring preditivo de leads com ML
- [ ] Dashboard de métricas em tempo real

---

## Aprendizados

> **Prompt Engineering** — prompts bem formulados aceleram significativamente o desenvolvimento de lógica complexa
>
> **Triggers Unificados** — centralizar automações melhora manutenibilidade e performance
>
> **Normalização de Texto** — remoção agressiva de acentos e sufixos aumenta taxa de match
>
> **Desenvolvimento Incremental** — versões progressivas permitem validação contínua com feedback real

---

## Autor

**Maria Luiza Moraes** Estagiária • Estratégia, Gestão e M&A @ Sympla

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/marialuizasm21)

---

> **Nota:** O código completo não está disponível publicamente por conter lógica de negócio proprietária. Este repositório serve como documentação do projeto para fins de portfólio.
