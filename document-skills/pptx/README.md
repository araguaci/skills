# Análise do Skill PPTX

## Visão Geral
Este skill fornece criação, edição e análise de apresentações para arquivos PowerPoint. Abrange tanto html2pptx para criação quanto edição OOXML para apresentações existentes.

## Estrutura do SKILL.md

### Metadados YAML
- **name**: pptx
- **description**: Criação, edição e análise de apresentações
- **license**: Proprietary. LICENSE.txt tem termos completos

### Conteúdo Principal

#### 1. Leitura e Análise de Conteúdo
- **Extração de texto**: markitdown para conversão
- **Acesso XML bruto**: Para comentários, notas do palestrante, layouts
- **Desempacotamento**: Script para acessar XML interno

#### 2. Criação de Nova Apresentação
- **Sem template**: Workflow html2pptx obrigatório
- **Com template**: Análise de template e reordenação
- **Princípios de design**: Cores, fontes, hierarquia visual
- **Validação visual**: Geração de thumbnails e inspeção

#### 3. Edição de Apresentação Existente
- **Workflow OOXML**: Desempacotar, editar, empacotar
- **Validação obrigatória**: Após cada edição
- **Estrutura XML**: Slides, comentários, layouts, temas

#### 4. Criação com Template
- **Análise de template**: Extração de texto e thumbnails
- **Inventário de template**: Estrutura e categorização
- **Seleção de layout**: Baseada no conteúdo real
- **Reordenação**: Scripts para duplicar e reorganizar

## Padrões Identificados

### Workflow de Criação
- **Sem template**: html2pptx obrigatório
- **Com template**: Análise e reordenação
- **Princípios de design**: Cores, fontes, hierarquia
- **Validação visual**: Thumbnails e inspeção

### Seleção de Layout
- **Baseada no conteúdo**: Não forçar layouts inadequados
- **Colunas apropriadas**: 1, 2 ou 3 colunas baseadas no conteúdo
- **Imagens reais**: Layouts de imagem apenas com imagens
- **Citações reais**: Layouts de citação apenas com citações reais

### Validação Visual
- **Geração de thumbnails**: Para inspeção visual
- **Verificação de layout**: Texto cortado, sobreposição, posicionamento
- **Contraste**: Verificação de legibilidade
- **Aparência profissional**: Padrões de qualidade

## Características Únicas

### Abordagem Multi-workflow
- **html2pptx**: Para criação sem template
- **Template-based**: Para criação com template existente
- **OOXML**: Para edição de apresentações existentes
- **Validação visual**: Para garantir qualidade

### Análise de Template
- Extração de texto e thumbnails
- Inventário completo de slides
- Categorização por tipo de layout
- Seleção baseada no conteúdo real

### Validação Visual
- Geração de thumbnails para inspeção
- Verificação de problemas de layout
- Contraste e legibilidade
- Aparência profissional

## Recursos Incluídos

### Scripts de Automação
- **html2pptx.js**: Conversão de HTML para PowerPoint
- **rearrange.py**: Reordenação de slides
- **inventory.py**: Extração de inventário de texto
- **replace.py**: Aplicação de substituições
- **thumbnail.py**: Geração de thumbnails

### Documentação
- **html2pptx.md**: Guia completo para criação
- **ooxml.md**: Guia para edição OOXML
- **forms.md**: Processamento de formulários

### Estrutura de Diretórios
```
document-skills/pptx/
├── SKILL.md (obrigatório)
├── LICENSE.txt
├── html2pptx.md
├── ooxml.md
├── forms.md
├── ooxml/ (47 arquivos)
└── scripts/ (5 arquivos)
```

## Fluxo de Trabalho

### Processo de Criação (Sem Template)
1. **Ler documentação**: `html2pptx.md` completamente
2. **Criar HTML**: Para cada slide com dimensões apropriadas
3. **Executar conversão**: Usar `html2pptx.js`
4. **Validação visual**: Gerar thumbnails e inspecionar

### Processo de Criação (Com Template)
1. **Extrair template**: Texto e thumbnails
2. **Analisar template**: Inventário completo
3. **Criar outline**: Baseado no inventário
4. **Reordenar slides**: Usar `rearrange.py`
5. **Extrair texto**: Usar `inventory.py`
6. **Gerar substituições**: JSON com novo conteúdo
7. **Aplicar substituições**: Usar `replace.py`

### Processo de Edição
1. **Ler documentação**: `ooxml.md` completamente
2. **Desempacotar**: Usar script unpack.py
3. **Editar XML**: Primariamente slides
4. **Validar**: Após cada edição
5. **Empacotar**: Usar script pack.py

## Casos de Uso

### Quando Usar
- Criar novas apresentações PowerPoint
- Editar apresentações existentes
- Usar templates existentes
- Converter HTML para PowerPoint
- Processar apresentações em lote

### Quando NÃO Usar
- Apresentações que não são PowerPoint
- Operações que não precisam de PowerPoint
- Tarefas simples sem necessidade de biblioteca
- Projetos sem manipulação de apresentações

## Qualidade e Padrões

### Requisitos de Design
- Cores que correspondem ao tópico
- Fontes web-safe apropriadas
- Hierarquia visual clara
- Contraste e legibilidade
- Consistência visual

### Padrões de Layout
- Seleção baseada no conteúdo real
- Não forçar layouts inadequados
- Colunas apropriadas para conteúdo
- Imagens e citações reais

### Validação Visual
- Geração de thumbnails obrigatória
- Inspeção de problemas de layout
- Verificação de contraste
- Aparência profissional

## Recursos Técnicos

### Bibliotecas Python
- **markitdown**: Extração de texto
- **defusedxml**: Parsing seguro de XML
- **PIL**: Processamento de imagens

### Ferramentas JavaScript
- **pptxgenjs**: Criação de apresentações
- **playwright**: Renderização de HTML
- **sharp**: Processamento de imagens

### Ferramentas CLI
- **LibreOffice**: Conversão para PDF
- **Poppler**: Conversão de PDF para imagens
- **Scripts customizados**: Unpack/pack/validate

## Manutenção e Atualizações

### Atualizações Técnicas
- Manter bibliotecas atuais
- Atualizar padrões de workflow
- Manter compatibilidade
- Testar com novas versões

### Extensões
- Adicionar novas capacidades de criação
- Expandir recursos de template
- Melhorar validação visual
- Aprimorar documentação
