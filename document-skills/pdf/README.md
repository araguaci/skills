# Análise do Skill PDF

## Visão Geral
Este skill fornece um toolkit abrangente de manipulação de PDF para extrair texto e tabelas, criar novos PDFs, mesclar/dividir documentos e lidar com formulários. Abrange bibliotecas Python e ferramentas de linha de comando.

## Estrutura do SKILL.md

### Metadados YAML
- **name**: pdf
- **description**: Toolkit abrangente de manipulação de PDF
- **license**: Proprietary. LICENSE.txt tem termos completos

### Conteúdo Principal

#### 1. Início Rápido
- **Bibliotecas Python**: pypdf, pdfplumber, reportlab
- **Ferramentas de linha de comando**: pdftotext, qpdf, pdftk
- **Operações comuns**: Merge, split, extract, create

#### 2. Bibliotecas Python
- **pypdf**: Operações básicas (merge, split, metadata, rotate)
- **pdfplumber**: Extração de texto e tabelas com layout
- **reportlab**: Criação de PDFs com formatação

#### 3. Ferramentas de Linha de Comando
- **pdftotext**: Extração de texto com preservação de layout
- **qpdf**: Operações de merge, split, rotate, decrypt
- **pdftk**: Operações avançadas (se disponível)

#### 4. Tarefas Comuns
- **OCR para PDFs digitalizados**: pytesseract + pdf2image
- **Adicionar marca d'água**: Merge de páginas
- **Extrair imagens**: pdfimages
- **Proteção por senha**: Encrypt/decrypt

## Padrões Identificados

### Seleção de Biblioteca
- **pypdf**: Operações básicas, merge, split, metadata
- **pdfplumber**: Extração de texto e tabelas com layout
- **reportlab**: Criação e formatação de PDFs
- **Ferramentas CLI**: Operações em lote, automação

### Operações Comuns
- **Merge PDFs**: Usar pypdf para combinar documentos
- **Split PDFs**: Dividir documentos em páginas individuais
- **Extract text**: pdfplumber para preservar layout
- **Extract tables**: pdfplumber com pandas para análise
- **Create PDFs**: reportlab para documentos profissionais

### Tarefas Avançadas
- **OCR**: pytesseract + pdf2image para PDFs digitalizados
- **Watermark**: Merge de páginas para marca d'água
- **Images**: pdfimages para extrair imagens
- **Security**: Encrypt/decrypt para proteção

## Características Únicas

### Abordagem Multi-biblioteca
- Diferentes bibliotecas para diferentes tarefas
- Seleção baseada na operação específica
- Combinação de Python e ferramentas CLI
- Cobertura abrangente de casos de uso

### Operações Especializadas
- OCR para PDFs digitalizados
- Extração de tabelas com pandas
- Marca d'água e proteção
- Operações em lote via CLI

### Integração com Pandas
- Extração de tabelas para DataFrames
- Análise de dados de PDFs
- Export para Excel
- Processamento de dados

## Recursos Incluídos

### Scripts Python
- **Operações básicas**: Merge, split, metadata, rotate
- **Extração avançada**: Texto, tabelas, imagens
- **Criação**: PDFs profissionais com reportlab
- **OCR**: Processamento de PDFs digitalizados

### Ferramentas CLI
- **pdftotext**: Extração de texto
- **qpdf**: Operações avançadas
- **pdftk**: Ferramentas adicionais
- **pdfimages**: Extração de imagens

### Estrutura de Diretórios
```
document-skills/pdf/
├── SKILL.md (obrigatório)
├── LICENSE.txt
├── forms.md
├── reference.md
├── scripts/ (8 arquivos Python)
└── RULES.md (regras CURSOR)
```

## Fluxo de Trabalho

### Processo de Trabalho
1. **Identificar tarefa**: Merge, split, extract, create
2. **Selecionar biblioteca**: pypdf, pdfplumber, reportlab
3. **Implementar operação**: Código Python ou CLI
4. **Validar resultado**: Verificar saída
5. **Otimizar se necessário**: Melhorar performance

### Constantes
- Seleção de biblioteca baseada na tarefa
- Operações comuns bem definidas
- Ferramentas CLI para automação
- Validação de resultados

### Variáveis
- Tarefa específica
- Biblioteca escolhida
- Parâmetros de operação
- Resultado esperado

## Casos de Uso

### Quando Usar
- Manipular documentos PDF
- Extrair texto e tabelas
- Criar novos PDFs
- Mesclar ou dividir documentos
- Processar formulários PDF

### Quando NÃO Usar
- Documentos que não são PDF
- Operações que não precisam de PDF
- Tarefas simples sem necessidade de biblioteca
- Projetos sem manipulação de documentos

## Qualidade e Padrões

### Requisitos de Biblioteca
- Seleção apropriada para tarefa
- Tratamento adequado de erros
- Validação de entradas
- Otimização de performance

### Padrões de Operação
- Operações comuns bem definidas
- Seleção de ferramenta apropriada
- Validação de resultados
- Tratamento de erros

### Validação
- Verificar resultado da operação
- Testar com diferentes tipos de PDF
- Validar integridade dos dados
- Garantir compatibilidade

## Recursos Técnicos

### Bibliotecas Python
- **pypdf**: Operações básicas
- **pdfplumber**: Extração avançada
- **reportlab**: Criação profissional
- **pytesseract**: OCR para PDFs digitalizados

### Ferramentas CLI
- **pdftotext**: Extração de texto
- **qpdf**: Operações avançadas
- **pdftk**: Ferramentas adicionais
- **pdfimages**: Extração de imagens

### Integração
- **Pandas**: Análise de dados extraídos
- **pdf2image**: Conversão para OCR
- **Tesseract**: Reconhecimento de texto
- **PIL**: Processamento de imagens

## Manutenção e Atualizações

### Atualizações Técnicas
- Manter bibliotecas atuais
- Atualizar padrões de uso
- Manter compatibilidade
- Testar com novas versões

### Extensões
- Adicionar novas bibliotecas
- Expandir funcionalidades
- Melhorar tratamento de erros
- Aprimorar documentação
