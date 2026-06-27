# Sistema de Classificação de Leads e Requalificação

Sistema automatizado construído em Google Apps Script que atua como o "cérebro" de triagem comercial. O projeto consolida leads desqualificados de múltiplas fontes, executa lógicas avançadas de anti-duplicidade e calcula matematicamente a elegibilidade para requalificação com base em regras temporais de negócio.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/marialuizasm21)

---

## Skills Técnicas Aplicadas

<div align="center">

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Apps Script](https://img.shields.io/badge/Apps_Script-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)
![Data Processing](https://img.shields.io/badge/Data_Processing-4285F4?style=for-the-badge)

</div>

---

## O Desafio vs. A Solução

**O Problema:** Historicamente, os leads desqualificados (marcados como *Bad Fit*, *Fit Sympla sem timing* ou por *Faturamento*) acabavam esquecidos e fragmentados em dezenas de planilhas. Sem uma base unificada, os qualificadores gastavam até 3 horas por semana procurando históricos para decidir se um lead poderia ser abordado novamente, resultando em retrabalho (requalificar o mesmo lead) e na perda de "timing" comercial (esquecer leads que já estavam maduros para reabordagem).

**A Solução:** Desenvolvi um motor de Inteligência e Requalificação que "pesca" dados de 10+ planilhas simultaneamente. O script centraliza a base, varre duplicatas com lógica de desempate temporal e, através de cálculos matemáticos sobre a data de desqualificação, classifica automaticamente quais leads estão prontos (Green), quase prontos (Yellow) ou bloqueados (Red) para o funil de vendas.

---

## 🛠️ Arquitetura e Engenharia do Sistema

### 1. Extração Multi-fonte (Crawler Interno)
O sistema opera a partir de um *Dashboard Central*. O script lê um array de URLs e itera sobre as abas "NUTRIÇÃO" de todas as planilhas da equipe. 
* Ele identifica proativamente leads marcados como `Bad Fit`, `Fit Sympla`, `Faixa F` ou `Gratuito`.
* Captura 15 colunas críticas e consolida em um único "data lake" na Base Unificada.

### 2. Motor Anti-duplicidade (Lógica de Desempate Temporal)
Para evitar que a base unificada vire um caos, o script processa cada novo lead contra um Dicionário de Dados (`mapaEmpresas`):
1. **Normalização:** Converte o nome da empresa para *lowercase* e remove espaços extras.
2. **Match:** Se a empresa já existe no banco, o código avalia as datas (Date Objects).
3. **Desempate:** O sistema **sobrescreve o registro antigo** apenas se a nova entrada for temporalmente mais recente. Se for mais antiga, o novo input é sumariamente ignorado. Isso garante que a base exiba sempre o estado atualizado da última negociação.

### 3. Matriz de Requalificação (Time-Based Rules)
O coração comercial do script é a função `calcularRequalificacao()`. Ela calcula a diferença exata de meses entre a data de nutrição e o timestamp atual, aplicando regras de negócio restritas:
* 🔴 **Bloqueios Permanentes:** Leads internacionais ("Gringo") ou bloqueios de "Não Atribuição".
* 🚫 **Bad Fit Permanente:** Leads fora de escopo total.
* ✅ **Fit Sympla Maturado (>= 6 meses):** Leads que eram "Fit" mas não fecharam, agora liberados para nova prospecção.
* ⏳ **Warm-up (5 meses):** Lead "prestes a ser requalificado", avisando o vendedor para preparar a estratégia.

---

## 🔄 A Integração em Tempo Real (Cross-Sheet)

O verdadeiro impacto ocorre na operação diária. O sistema de Base Unificada foi plugado a um gatilho (`onEdit`) na Planilha Master dos vendedores.

**O Fluxo Instantâneo:**
1. O SDR/Qualificador digita o Nome da Empresa ou E-mail.
2. Em background, o script consulta a Base Unificada.
3. Em milissegundos, retorna na própria linha o aviso: *"Bad Fit - Concorrência"* ou *"Fit Sympla - Timing de 6 meses"*.
4. O vendedor interrompe a pesquisa imediatamente, economizando 20 minutos de trabalho inútil em um lead que não deve ser abordado.

---

## 🚀 Resultados e Impacto do Projeto

* **Zero Retrabalho Operacional:** A integração de consulta instantânea eliminou o problema de requalificar leads bloqueados (Economia direta de 2 a 3 horas semanais por analista).
* **Governança Unificada:** Mais de 1.000 leads históricos retirados da "sombra" de 10 planilhas diferentes e consolidados em uma visão gerencial única.
* **Funil Proativo:** Vendedores pararam de contar com a memória ou lembretes manuais; o dashboard aponta automaticamente quais leads passaram da barreira de 6 meses de "geladeira" e voltaram para o jogo.
* **Escalabilidade Tecnológica:** O uso de Dicionários/Mapas em JavaScript (`{}`) ao invés de *arrays* aninhados reduziu o tempo de execução do script para a casa dos segundos, mesmo cruzando milhares de linhas.

---

## Autor

**Maria Luiza Moraes**
Estagiária • Estratégia, Gestão e M&A @ Sympla

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/marialuizasm21)

---
> **Nota de Confidencialidade:** Este repositório documenta a lógica de negócio, a engenharia temporal e a arquitetura de processamento em lote para fins de portfólio profissional. Códigos-fonte internos e bases de clientes foram intencionalmente omitidos.
