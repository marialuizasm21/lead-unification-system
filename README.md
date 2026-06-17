# Sistema de Unificação Automática de Leads e Requalificação

<img width="4170" height="2970" alt="sistema-integracao-leads" src="https://github.com/user-attachments/assets/e5d0e022-3cb5-4bf7-ac5b-4f8df7352e31" />

Sistema automático que consolida leads desqualificados de múltiplas fontes, elimina duplicidades e calcula elegibilidade para requalificação baseado em regras de negócio.

---

## O Problema

Leads desqualificados (Bad Fit, Fit Sympla, Faixa F) estavam espalhados em mais de 10 planilhas diferentes de nutrição. Isso gerava:

- Impossibilidade de mapear rapidamente produtores já qualificados
- Retrabalho ao processar o mesmo lead múltiplas vezes
- Perda de oportunidades de requalificação
- Falta de visão centralizada do histórico de desqualificações
- Tempo perdido buscando informação em múltiplas fontes

**Impacto:** Time gastava 2-3 horas por semana buscando informações de leads já processados e perdia oportunidades de reabordagem.

---

## A Solução

Desenvolvi um sistema automatizado em **Google Apps Script** que:

### Extração Multi-fonte
- Percorre automaticamente todas as planilhas cadastradas na Central de Extração
- Identifica leads desqualificados por diferentes critérios (GMV Faixa F, Gratuito, Bad Fit, Fit Sympla)
- Consolida dados em uma base única centralizada

### Anti-duplicidade Inteligente
- Compara registros pelo nome da empresa
- Identifica duplicatas e mantém apenas o registro mais recente
- Utiliza data de nutrição como critério de desempate

### Classificação Automática de Status
- **Bad Fit:** Permanente (não requalificar)
- **Fit Sympla:** Elegível após 6 meses
- **Faixa F:** Critério específico de faturamento

### Cálculo Temporal
- Calcula automaticamente tempo decorrido desde a desqualificação
- Define status de requalificação baseado em regras de negócio
- Atualiza indicadores em tempo real

### Dashboard Centralizado
- Puxa automaticamente indicadores de resumo de cada planilha
- Atualiza painel central com métricas consolidadas
- Permite visão macro de performance por lista

---

## Tecnologias

- **Google Apps Script** - Automação e integração
- **Google Sheets** - Base de dados e interface
- **JavaScript** - Lógica de processamento
- **Algoritmos anti-duplicidade** - Comparação e desempate
- **Lógica temporal** - Cálculo de elegibilidade

---

## Resultados

### Quantitativos
- **1000+ leads** unificados automaticamente
- **10+ planilhas** consolidadas em uma base única
- **2-3 horas/semana** economizadas
- **100%** eliminação de retrabalho na busca

### Qualitativos
- Base única de consulta para toda equipe
- Identificação instantânea de leads elegíveis para requalificação
- Histórico completo preservado com data e motivo
- Visão estratégica de leads desqualificados
- Decisões mais rápidas sobre reabordagem

---

---

## Como Funciona

O sistema opera em 4 etapas automatizadas:

### 1. Extração de Dados
O script percorre todas as planilhas de nutrição cadastradas na Central de Extração, identificando automaticamente leads com status de desqualificação (Bad Fit, Fit Sympla, Faixa F ou Gratuito). Para cada lead encontrado, extrai informações relevantes: nome da empresa, data de nutrição, motivo da desqualificação e lista de origem.

### 2. Anti-duplicidade
Com todos os dados extraídos, o sistema compara os registros pelo nome da empresa. Quando encontra duplicatas (mesmo lead em múltiplas planilhas), mantém apenas o registro mais recente utilizando a data de nutrição como critério de desempate. Isso garante que o histórico reflete sempre a última interação com o lead.

### 3. Classificação e Cálculo
Para cada lead único, o sistema:
- Classifica o tipo de desqualificação (Bad Fit permanente, Fit Sympla elegível após 6 meses, ou Faixa F)
- Calcula automaticamente o tempo decorrido desde a desqualificação
- Define o status atual de requalificação baseado nas regras de negócio

### 4. Consolidação Final
Todos os dados processados são consolidados na Base Unificada, que serve como fonte única de consulta. O dashboard central é atualizado automaticamente com métricas agregadas de cada lista, permitindo visão estratégica do volume e distribuição de leads desqualificados.

---

## Integração com Verificador Automático

Este sistema funciona em conjunto com um **script de verificação** que roda diretamente na **Planilha Master de Nutrição** durante o processo de qualificação.

### Como Funciona a Integração

**Durante a Qualificação:**
1. Qualificador preenche Nome da Empresa (coluna T) ou E-mail (coluna AD) na planilha master
2. Script verificador **consulta automaticamente** esta Base Unificada
3. Retorna instantaneamente na coluna J se o lead já foi mapeado:
   - Motivo específico de Bad Fit
   - Fit Sympla com motivo de não atribuição  
   - Identificação de Faixa F

### Normalização Inteligente

O verificador usa normalização avançada para garantir correspondência:
- Remove acentos e caracteres especiais
- Elimina espaços extras
- Desconsidera sufixos corporativos (LTDA, S.A., ME, Eireli)
- Busca cruzada por nome E email

### Execução Silenciosa

- Roda automaticamente em background
- Sem pop-ups ou interrupções
- Atualização instantânea na planilha
- Zero impacto na operação

### Impacto Combinado

**Base Unificada** fornece a fonte de verdade centralizada  
↓  
**Verificador Automático** consulta em tempo real  
↓  
**Resultado:** Identificação instantânea de leads já processados

**Benefício:** Economia de 20-30 minutos por lead que seria requalificado incorretamente, eliminando 100% do retrabalho.

---

## Estrutura de Dados

### Campos Extraídos
- Nome da Empresa
- Data de Nutrição
- Motivo de Desqualificação
- Tipo (Bad Fit / Fit Sympla / Faixa F)
- Status de Requalificação
- Tempo Decorrido
- Lista de Origem

### Regras de Negócio
- Bad Fit = Permanente (não requalificar)
- Fit Sympla = 6 meses para requalificação
- Faixa F = Critério específico

---

## Aprendizados

### Técnicos
- Otimização de loops em Apps Script para processar grandes volumes
- Normalização de texto para comparação (remoção de acentos, sufixos LTDA/ME)
- Estruturação de dados para facilitar consultas futuras

### Processo
- Importância de base única como fonte de verdade
- Automatização reduz erro humano drasticamente
- Visão consolidada permite decisões estratégicas mais rápidas

---

## Limitações & Próximos Passos

### Limitações Atuais
- Dependente de estrutura padronizada nas planilhas de origem
- Execução manual (não agendada automaticamente)

### Melhorias Futuras
- Trigger automático diário/semanal
- Alertas quando leads ficam elegíveis para requalificação
- Integração direta com HubSpot para enriquecimento

---

## Autor

**Maria Luiza Moraes**  
Estagiária • Estratégia, Gestão e M&A @ Sympla

[LinkedIn](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/) • [GitHub](https://github.com/marialuizasm21)

---

**Nota:** Este projeto faz parte do portfólio de automações e melhorias de processos desenvolvidas na área de Inteligência de Mercado. O código não está disponível publicamente por conter lógica de negócio proprietária.


