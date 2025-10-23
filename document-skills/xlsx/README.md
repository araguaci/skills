# Análise do Skill XLSX

## Visão Geral
Este skill fornece criação, edição e análise abrangente de planilhas com suporte para fórmulas, formatação, análise de dados e visualização. Abrange tanto pandas para análise de dados quanto openpyxl para fórmulas e formatação.

## Estrutura do SKILL.md

### Metadados YAML
- **name**: xlsx
- **description**: Criação, edição e análise abrangente de planilhas
- **license**: Proprietary. LICENSE.txt tem termos completos

### Conteúdo Principal

#### 1. Requisitos para Saídas
- **Todos os arquivos Excel**: Zero erros de fórmula obrigatório
- **Modelos financeiros**: Padrões de codificação de cores e formatação
- **Preservação de templates**: Manter formato, estilo e convenções existentes

#### 2. Construção de Fórmulas
- **Colocação de suposições**: Células separadas para todas as suposições
- **Prevenção de erros**: Verificação de referências e casos extremos
- **Documentação**: Fonte e referência para valores codificados

#### 3. CRÍTICO: Usar Fórmulas, Não Valores Codificados
- **❌ ERRADO**: Calcular em Python e codificar resultado
- **✅ CORRETO**: Deixar Excel calcular com fórmulas
- **Benefício**: Planilha permanece dinâmica e atualizável

#### 4. Fluxo de Trabalho Comum
- **Escolher ferramenta**: pandas para dados, openpyxl para fórmulas
- **Criar/Carregar**: Novo workbook ou arquivo existente
- **Modificar**: Adicionar/editar dados, fórmulas e formatação
- **Salvar**: Escrever em arquivo
- **Recalcular fórmulas**: Script recalc.py obrigatório
- **Verificar e corrigir erros**: Verificar saída JSON

## Padrões Identificados

### Requisitos de Qualidade
- **Zero erros de fórmula**: Obrigatório para todos os modelos
- **Preservação de templates**: Manter formato e estilo existentes
- **Padrões de codificação**: Cores específicas para diferentes tipos de dados
- **Formatação de números**: Padrões específicos para anos, moeda, percentuais

### Construção de Fórmulas
- **Suposições separadas**: Células dedicadas para todas as suposições
- **Referências de célula**: Em vez de valores codificados
- **Prevenção de erros**: Verificação de referências e casos extremos
- **Documentação**: Fonte e referência para valores codificados

### Fluxo de Trabalho
- **Seleção de biblioteca**: pandas vs openpyxl baseado na tarefa
- **Criação/Modificação**: Dados, fórmulas e formatação
- **Recálculo obrigatório**: Script recalc.py para fórmulas
- **Verificação de erros**: JSON com localizações detalhadas

## Características Únicas

### Abordagem de Fórmulas
- **CRÍTICO**: Sempre usar fórmulas Excel em vez de valores codificados
- **Benefício**: Planilha permanece dinâmica e atualizável
- **Recálculo**: Script automatizado para atualizar valores
- **Verificação**: JSON com erros detalhados

### Padrões de Qualidade
- Zero erros de fórmula obrigatório
- Preservação de templates existentes
- Padrões de codificação de cores
- Formatação de números específica

### Integração de Bibliotecas
- **pandas**: Análise de dados e operações em lote
- **openpyxl**: Fórmulas, formatação e recursos Excel
- **Scripts customizados**: Recálculo e verificação

## Recursos Incluídos

### Scripts de Automação
- **recalc.py**: Recálculo de fórmulas e verificação de erros
- **Validação automática**: Verificação de erros Excel
- **JSON de saída**: Localizações detalhadas de erros

### Estrutura de Diretórios
```
document-skills/xlsx/
├── SKILL.md (obrigatório)
├── LICENSE.txt
├── recalc.py
└── RULES.md (regras CURSOR)
```

## Fluxo de Trabalho

### Processo de Criação
1. **Escolher ferramenta**: pandas ou openpyxl
2. **Criar/Carregar**: Novo workbook ou arquivo existente
3. **Modificar**: Dados, fórmulas e formatação
4. **Salvar**: Escrever em arquivo
5. **Recalcular**: Script recalc.py obrigatório
6. **Verificar**: JSON com erros detalhados

### Constantes
- Zero erros de fórmula obrigatório
- Preservação de templates existentes
- Recálculo de fórmulas obrigatório
- Verificação de erros detalhada

### Variáveis
- Tarefa específica (análise vs criação)
- Biblioteca escolhida
- Fórmulas necessárias
- Formatação aplicada

## Casos de Uso

### Quando Usar
- Criar novas planilhas Excel
- Editar planilhas existentes
- Análise de dados em planilhas
- Criação de modelos financeiros
- Processamento de dados em lote

### Quando NÃO Usar
- Dados que não precisam de Excel
- Operações simples sem necessidade de biblioteca
- Projetos sem manipulação de planilhas
- Tarefas que não precisam de fórmulas

## Qualidade e Padrões

### Requisitos de Fórmulas
- Zero erros de fórmula obrigatório
- Uso de fórmulas em vez de valores codificados
- Verificação de referências de célula
- Teste com casos extremos

### Padrões de Formatação
- Cores específicas para tipos de dados
- Formatação de números apropriada
- Preservação de templates existentes
- Aparência profissional

### Validação
- Recálculo obrigatório de fórmulas
- Verificação de erros detalhada
- Teste com diferentes tipos de dados
- Garantia de funcionalidade

## Recursos Técnicos

### Bibliotecas Python
- **pandas**: Análise de dados e operações em lote
- **openpyxl**: Fórmulas, formatação e recursos Excel
- **Scripts customizados**: Recálculo e verificação

### Ferramentas de Verificação
- **recalc.py**: Recálculo de fórmulas
- **Verificação de erros**: JSON com localizações
- **Validação automática**: Verificação de integridade

### Integração
- **LibreOffice**: Recálculo de fórmulas
- **JSON**: Saída de erros detalhada
- **Excel**: Funcionalidade nativa

## Manutenção e Atualizações

### Atualizações Técnicas
- Manter bibliotecas atuais
- Atualizar padrões de fórmula
- Manter compatibilidade
- Testar com novas versões

### Extensões
- Adicionar novas capacidades de fórmula
- Expandir opções de formatação
- Melhorar verificação de erros
- Aprimorar documentação
