# Análise do Skill DOCX

## Visão Geral
Este skill fornece criação, edição e análise abrangente de documentos com suporte para alterações rastreadas, comentários, preservação de formatação e extração de texto. Abrange tanto docx-js para criação quanto Document library para edição.

## Estrutura do SKILL.md

### Metadados YAML
- **name**: docx
- **description**: Criação, edição e análise abrangente de documentos
- **license**: Proprietary. LICENSE.txt tem termos completos

### Conteúdo Principal

#### 1. Árvore de Decisão de Fluxo de Trabalho
- **Ler/Analisar conteúdo**: Extração de texto ou acesso XML bruto
- **Criar novo documento**: Workflow docx-js
- **Editar documento existente**: Edição OOXML básica ou workflow de redlining

#### 2. Leitura e Análise
- **Extração de texto**: Pandoc com preservação de alterações rastreadas
- **Acesso XML bruto**: Para comentários, formatação complexa, estrutura
- **Desempacotamento**: Script para acessar XML interno

#### 3. Criação de Documento
- **docx-js obrigatório**: Ler `docx-js.md` completamente
- **JavaScript/TypeScript**: Usar componentes Document, Paragraph, TextRun
- **Export**: Usar Packer.toBuffer() para .docx

#### 4. Edição de Documento
- **Document library**: Para manipulação OOXML
- **Workflow de redlining**: Para documentos de terceiros
- **Alterações rastreadas**: Implementação sistemática obrigatória

## Padrões Identificados

### Árvore de Decisão
- **HTML estático**: Caminho direto para seletores
- **Webapp dinâmico**: Verificação de servidor primeiro
- **Reconhecimento-ação**: Padrão obrigatório para apps dinâmicos
- **Aguardo networkidle**: Crítico para execução de JavaScript

### Workflow de Redlining
- **Implementação sistemática**: Todas as alterações devem ser implementadas
- **Estratégia de lotes**: Agrupar alterações relacionadas em lotes de 3-10
- **Teste por lote**: Testar cada lote antes de prosseguir
- **Edições mínimas**: Apenas marcar texto que realmente muda

### Estrutura de Arquivos
- **word/document.xml**: Conteúdo principal do documento
- **word/comments.xml**: Comentários referenciados
- **word/media/**: Imagens e arquivos de mídia incorporados
- **Alterações rastreadas**: Tags `<w:ins>` (inserções) e `<w:del>` (deleções)

## Características Únicas

### Abordagem Multi-ferramenta
- **docx-js**: Para criação de documentos
- **Document library**: Para edição OOXML
- **Pandoc**: Para extração de texto
- **Ferramentas CLI**: Para conversão e processamento

### Workflow de Redlining
- Implementação sistemática de alterações
- Estratégia de lotes para gerenciabilidade
- Preservação de formatação original
- Verificação abrangente final

### Acesso XML Bruto
- Desempacotamento de documentos
- Acesso direto à estrutura XML
- Manipulação de comentários e formatação
- Preservação de metadados

## Recursos Incluídos

### Scripts de Automação
- **unpack.py**: Desempacotar documentos OOXML
- **pack.py**: Empacotar diretório de volta para .docx
- **Validação**: Verificação de integridade

### Documentação
- **docx-js.md**: Guia completo para criação
- **ooxml.md**: Guia para edição OOXML
- **forms.md**: Processamento de formulários

### Estrutura de Diretórios
```
document-skills/docx/
├── SKILL.md (obrigatório)
├── LICENSE.txt
├── docx-js.md
├── ooxml.md
├── forms.md
├── ooxml/ (47 arquivos)
└── scripts/ (8 arquivos)
```

## Fluxo de Trabalho

### Processo de Criação
1. **Ler documentação**: `docx-js.md` completamente
2. **Criar arquivo JS/TS**: Usar componentes Document, Paragraph, TextRun
3. **Exportar**: Usar Packer.toBuffer() para .docx
4. **Validar**: Verificar resultado

### Processo de Edição
1. **Ler documentação**: `ooxml.md` completamente
2. **Desempacotar**: Usar script unpack.py
3. **Implementar alterações**: Usar Document library
4. **Empacotar**: Usar script pack.py
5. **Verificar**: Verificação abrangente

### Processo de Redlining
1. **Obter representação markdown**: Com alterações rastreadas
2. **Identificar e agrupar alterações**: Organizar em lotes
3. **Ler documentação e desempacotar**: Preparar ambiente
4. **Implementar alterações em lotes**: Processar sistematicamente
5. **Empacotar documento**: Converter de volta para .docx
6. **Verificação final**: Verificação abrangente

## Casos de Uso

### Quando Usar
- Criar novos documentos Word
- Editar documentos existentes
- Processar alterações rastreadas
- Extrair texto e comentários
- Converter documentos

### Quando NÃO Usar
- Documentos que não são .docx
- Operações que não precisam de Word
- Tarefas simples sem necessidade de biblioteca
- Projetos sem manipulação de documentos

## Qualidade e Padrões

### Requisitos de Workflow
- Leitura obrigatória de documentação
- Implementação sistemática de alterações
- Estratégia de lotes para gerenciabilidade
- Verificação abrangente final

### Padrões de Edição
- Edições mínimas e precisas
- Preservação de formatação original
- Mapeamento XML adequado
- Preservação de RSID para texto inalterado

### Validação
- Verificar integridade do documento
- Testar com diferentes tipos de alterações
- Validar preservação de formatação
- Garantir compatibilidade

## Recursos Técnicos

### Bibliotecas Python
- **Document library**: Manipulação OOXML
- **defusedxml**: Parsing seguro de XML
- **Pandoc**: Extração de texto

### Ferramentas CLI
- **LibreOffice**: Conversão para PDF
- **Poppler**: Conversão de PDF para imagens
- **Scripts customizados**: Unpack/pack

### Integração
- **docx-js**: Criação de documentos
- **OOXML**: Estrutura interna do Word
- **Alterações rastreadas**: Sistema de controle de versão

## Manutenção e Atualizações

### Atualizações Técnicas
- Manter bibliotecas atuais
- Atualizar padrões de workflow
- Manter compatibilidade
- Testar com novas versões

### Extensões
- Adicionar novas capacidades de edição
- Expandir recursos de alterações rastreadas
- Melhorar tratamento de erros
- Aprimorar documentação
