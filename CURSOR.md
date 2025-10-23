# CURSOR.md - Regras para o Repositório de Skills

Este documento define as regras e diretrizes para trabalhar com este repositório de skills do Claude.

## Visão Geral do Projeto

Este repositório contém skills de exemplo que demonstram as capacidades do sistema de skills do Claude. Skills são pastas de instruções, scripts e recursos que o Claude carrega dinamicamente para melhorar o desempenho em tarefas especializadas.

## Estrutura do Projeto

### Skills Disponíveis

#### Criativo & Design
- **algorithmic-art** - Criar arte generativa usando p5.js
- **canvas-design** - Design visual em formatos .png e .pdf
- **slack-gif-creator** - Criar GIFs animados otimizados para Slack

#### Desenvolvimento & Técnico
- **artifacts-builder** - Construir artefatos HTML complexos usando React, Tailwind CSS e shadcn/ui
- **mcp-builder** - Guia para criar servidores MCP de alta qualidade
- **webapp-testing** - Testar aplicações web locais usando Playwright

#### Empresarial & Comunicação
- **brand-guidelines** - Aplicar cores e tipografia oficiais da Anthropic
- **internal-comms** - Escrever comunicações internas
- **theme-factory** - Estilizar artefatos com temas profissionais

#### Skills Meta
- **skill-creator** - Guia para criar skills eficazes
- **template-skill** - Template básico para novos skills

#### Document Skills
- **document-skills/pdf** - Manipulação abrangente de PDFs
- **document-skills/docx** - Criar, editar e analisar documentos Word
- **document-skills/pptx** - Criar, editar e analisar apresentações PowerPoint
- **document-skills/xlsx** - Criar, editar e analisar planilhas Excel

## Regras de Desenvolvimento

### 1. Estrutura de Skills

Cada skill deve seguir esta estrutura mínima:
```
skill-name/
├── SKILL.md (obrigatório)
│   ├── YAML frontmatter (obrigatório)
│   │   ├── name: (obrigatório)
│   │   └── description: (obrigatório)
│   └── Instruções Markdown (obrigatório)
└── Recursos Opcionais
    ├── scripts/          - Código executável
    ├── references/       - Documentação de referência
    └── assets/           - Arquivos usados na saída
```

### 2. YAML Frontmatter Obrigatório

```yaml
---
name: nome-do-skill
description: Descrição clara do que o skill faz e quando usar
license: Termos completos em LICENSE.txt (opcional)
---
```

**Regras para frontmatter:**
- `name`: deve ser em kebab-case (minúsculas, hífens para espaços)
- `description`: deve ser específico sobre o que o skill faz e quando usar
- Use terceira pessoa: "Este skill deve ser usado quando..." em vez de "Use este skill quando..."

### 3. Conteúdo do SKILL.md

**Estilo de escrita:**
- Use **forma imperativa/infinitiva** (instruções verb-first)
- Use linguagem objetiva e instrucional
- Exemplo: "Para realizar X, faça Y" em vez de "Você deve fazer X"

**Estrutura recomendada:**
1. Propósito do skill (algumas frases)
2. Quando usar o skill
3. Como o Claude deve usar o skill na prática
4. Referenciar todos os recursos reutilizáveis desenvolvidos

### 4. Recursos Opcionais

#### Scripts (`scripts/`)
- **Quando incluir**: Quando o mesmo código é reescrito repetidamente ou é necessária confiabilidade determinística
- **Exemplo**: `scripts/rotate_pdf.py` para tarefas de rotação de PDF
- **Benefícios**: Eficiente em tokens, determinístico, pode ser executado sem carregar no contexto

#### References (`references/`)
- **Quando incluir**: Para documentação que o Claude deve referenciar enquanto trabalha
- **Exemplos**: `references/finance.md` para esquemas financeiros, `references/api_docs.md` para especificações de API
- **Melhor prática**: Se arquivos são grandes (>10k palavras), inclua padrões de busca grep no SKILL.md

#### Assets (`assets/`)
- **Quando incluir**: Quando o skill precisa de arquivos que serão usados na saída final
- **Exemplos**: `assets/logo.png` para ativos de marca, `assets/template.html` para templates HTML
- **Benefícios**: Separa recursos de saída da documentação

### 5. Princípio de Divulgação Progressiva

Skills usam um sistema de carregamento de três níveis:

1. **Metadados (name + description)** - Sempre no contexto (~100 palavras)
2. **Corpo do SKILL.md** - Quando o skill é acionado (<5k palavras)
3. **Recursos agrupados** - Conforme necessário pelo Claude (Ilimitado*)

*Ilimitado porque scripts podem ser executados sem ler na janela de contexto.

## Regras de Trabalho

### 1. Criação de Novos Skills

**Processo obrigatório:**
1. **Entender o skill com exemplos concretos** - Definir funcionalidade e casos de uso
2. **Planejar conteúdo reutilizável** - Identificar scripts, referências e assets necessários
3. **Inicializar o skill** - Usar `scripts/init_skill.py <skill-name> --path <output-directory>`
4. **Editar o skill** - Focar em informações benéficas e não óbvias para o Claude
5. **Empacotar o skill** - Usar `scripts/package_skill.py <path/to/skill-folder>`
6. **Iterar** - Testar e melhorar baseado no feedback

### 2. Modificação de Skills Existentes

**Ao editar skills existentes:**
- Mantenha a estrutura YAML frontmatter
- Preserve a compatibilidade com versões anteriores
- Atualize a documentação conforme necessário
- Teste as mudanças antes de commitar

### 3. Padrões de Código

**Para scripts Python:**
- Use docstrings para funções principais
- Inclua tratamento de erros apropriado
- Mantenha código limpo e bem documentado
- Use type hints quando apropriado

**Para templates HTML/JS:**
- Mantenha estrutura consistente
- Use comentários para marcar seções variáveis vs fixas
- Preserve branding Anthropic quando aplicável

### 4. Licenciamento

- Skills de exemplo: Apache 2.0 (open source)
- Document skills: Proprietary (source-available, não open source)
- Sempre inclua arquivo LICENSE.txt apropriado
- Referencie licenças de terceiros em THIRD_PARTY_NOTICES.md

## Regras de Commit

### 1. Mensagens de Commit

**Formato:**
```
tipo(escopo): descrição breve

Descrição detalhada se necessário
```

**Tipos:**
- `feat`: nova funcionalidade
- `fix`: correção de bug
- `docs`: mudanças na documentação
- `style`: formatação, ponto e vírgula, etc.
- `refactor`: refatoração de código
- `test`: adição ou correção de testes
- `chore`: tarefas de manutenção

### 2. Estrutura de Branches

- `main`: branch principal
- `feature/nome-do-skill`: para novos skills
- `fix/nome-do-problema`: para correções
- `docs/descrição`: para mudanças na documentação

## Regras de Teste

### 1. Validação de Skills

**Antes de commitar:**
- Execute `scripts/package_skill.py` para validar
- Verifique se todos os campos obrigatórios estão presentes
- Teste scripts incluídos
- Valide referências a arquivos externos

### 2. Testes de Integração

**Para skills que executam código:**
- Teste em ambiente isolado
- Verifique dependências
- Valide saídas esperadas
- Teste casos de erro

## Regras de Documentação

### 1. README.md

- Mantenha atualizado com novos skills
- Inclua exemplos de uso
- Documente dependências
- Forneça instruções de instalação

### 2. SKILL.md

- Use linguagem clara e objetiva
- Inclua exemplos práticos
- Documente parâmetros e opções
- Mantenha foco no usuário final

### 3. Comentários no Código

- Explique lógica complexa
- Documente APIs externas
- Inclua exemplos de uso
- Mantenha comentários atualizados

## Regras de Segurança

### 1. Dados Sensíveis

- Nunca commite chaves de API
- Use variáveis de ambiente para configurações sensíveis
- Valide entradas do usuário
- Sanitize saídas quando apropriado

### 2. Execução de Código

- Valide scripts antes da execução
- Use ambientes isolados quando possível
- Monitore uso de recursos
- Implemente timeouts apropriados

## Regras de Performance

### 1. Otimização de Contexto

- Mantenha SKILL.md conciso (<5k palavras)
- Use referências para documentação detalhada
- Scripts devem ser executáveis sem carregar no contexto
- Evite duplicação de informações

### 2. Recursos

- Otimize scripts para execução rápida
- Use bibliotecas eficientes
- Implemente cache quando apropriado
- Monitore uso de memória

## Regras de Manutenção

### 1. Atualizações

- Mantenha dependências atualizadas
- Teste após atualizações
- Documente mudanças breaking
- Forneça guias de migração

### 2. Deprecação

- Aviso com antecedência
- Forneça alternativas
- Mantenha compatibilidade quando possível
- Documente processo de migração

## Contatos e Suporte

- **Documentação oficial**: [Claude Skills Documentation](https://support.claude.com/en/articles/12512176-what-are-skills)
- **API Skills**: [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide#creating-a-skill)
- **Issues**: Use o sistema de issues do GitHub para reportar problemas
- **Discussões**: Use GitHub Discussions para perguntas e sugestões

---

**Nota**: Este documento deve ser atualizado conforme o projeto evolui. Mantenha as regras relevantes e remova ou modifique as que se tornarem obsoletas.
