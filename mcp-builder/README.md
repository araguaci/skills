# Análise do Skill MCP Builder

## Visão Geral
Este skill fornece um guia para criar servidores MCP (Model Context Protocol) de alta qualidade que permitem que LLMs interajam com serviços externos através de ferramentas bem projetadas. Abrange implementações em Python (FastMCP) e Node/TypeScript (MCP SDK).

## Estrutura do SKILL.md

### Metadados YAML
- **name**: mcp-builder
- **description**: Guia para criar servidores MCP de alta qualidade
- **license**: Termos completos em LICENSE.txt

### Conteúdo Principal

#### 1. Processo de 4 Fases
- **Fase 1**: Pesquisa profunda e planejamento
- **Fase 2**: Implementação
- **Fase 3**: Revisão e refinamento
- **Fase 4**: Criação de avaliações

#### 2. Princípios de Design Centrado em Agente
- **Construir para fluxos de trabalho**: Não apenas endpoints de API
- **Otimizar para contexto limitado**: Fazer cada token contar
- **Projetar mensagens de erro acionáveis**: Guiar agentes para uso correto
- **Seguir subdivisões naturais de tarefas**: Nomes de ferramentas refletem como humanos pensam
- **Usar desenvolvimento orientado por avaliação**: Deixar feedback do agente dirigir melhorias

#### 3. Documentação e Referências
- **Protocolo MCP**: Especificação completa
- **Melhores práticas**: Diretrizes universais
- **Guias específicos de linguagem**: Python e TypeScript
- **Guia de avaliação**: Criação de avaliações abrangentes

## Padrões Identificados

### Fase 1: Pesquisa e Planejamento
- **Princípios de design**: Entender como projetar ferramentas para agentes IA
- **Documentação do protocolo**: Estudar especificação MCP completa
- **Documentação do framework**: SDKs Python e TypeScript
- **Documentação da API**: Pesquisa exaustiva de APIs externas
- **Plano de implementação**: Ferramentas, utilitários, I/O, tratamento de erros

### Fase 2: Implementação
- **Estrutura do projeto**: Configuração apropriada para linguagem
- **Infraestrutura central**: Utilitários compartilhados primeiro
- **Implementação de ferramentas**: Sistemática com validação e documentação
- **Práticas específicas**: Python (Pydantic, async/await) ou TypeScript (Zod, tipos)

### Fase 3: Revisão e Refinamento
- **Revisão de qualidade**: DRY, composabilidade, consistência
- **Teste e build**: Processos seguros para servidores de longa duração
- **Lista de verificação**: Qualidade específica da linguagem

### Fase 4: Criação de Avaliações
- **10 questões de avaliação**: Complexas, realistas, verificáveis
- **Processo estruturado**: Inspeção de ferramentas, exploração de conteúdo
- **Formato XML**: Estrutura padronizada para avaliações

## Características Únicas

### Abordagem Centrada em Agente
- Foco em fluxos de trabalho, não apenas endpoints
- Otimização para contexto limitado
- Mensagens de erro educativas
- Subdivisões naturais de tarefas
- Desenvolvimento orientado por avaliação

### Processo de 4 Fases
- Pesquisa profunda obrigatória
- Implementação sistemática
- Revisão e refinamento
- Criação de avaliações abrangentes

### Suporte Multi-linguagem
- Python com FastMCP e Pydantic
- Node/TypeScript com MCP SDK e Zod
- Guias específicos para cada linguagem
- Práticas de qualidade específicas

## Recursos Incluídos

### Documentação de Referência
- **mcp_best_practices.md**: Diretrizes universais
- **python_mcp_server.md**: Guia específico Python
- **node_mcp_server.md**: Guia específico TypeScript
- **evaluation.md**: Guia de criação de avaliações

### Estrutura de Diretórios
```
mcp-builder/
├── SKILL.md (obrigatório)
├── LICENSE.txt
├── reference/
│   ├── mcp_best_practices.md
│   ├── python_mcp_server.md
│   ├── node_mcp_server.md
│   └── evaluation.md
├── scripts/
│   └── [scripts de automação]
└── RULES.md (regras CURSOR)
```

## Fluxo de Trabalho

### Processo Completo
1. **Pesquisa profunda**: Princípios, protocolo, framework, API
2. **Planejamento**: Ferramentas, utilitários, I/O, erros
3. **Implementação**: Estrutura, infraestrutura, ferramentas
4. **Revisão**: Qualidade, teste, build
5. **Avaliação**: 10 questões complexas e realistas

### Constantes
- Processo de 4 fases
- Princípios centrados em agente
- Documentação obrigatória
- Avaliações abrangentes

### Variáveis
- Linguagem de implementação
- APIs externas específicas
- Ferramentas necessárias
- Avaliações específicas

## Casos de Uso

### Quando Usar
- Construir servidores MCP para integração com APIs externas
- Implementar ferramentas para LLMs
- Criar integrações de serviços
- Desenvolver protocolos de contexto de modelo

### Quando NÃO Usar
- Projetos que não precisam de MCP
- Integrações simples sem protocolo
- Ferramentas que não interagem com serviços externos
- Projetos sem necessidade de avaliação

## Qualidade e Padrões

### Requisitos de Qualidade
- Princípio DRY: Sem código duplicado
- Composabilidade: Lógica compartilhada extraída
- Consistência: Operações similares retornam formatos similares
- Tratamento de erros: Todas as chamadas externas têm tratamento
- Segurança de tipos: Cobertura completa de tipos
- Documentação: Cada ferramenta tem docstrings abrangentes

### Padrões de Implementação
- Estrutura de projeto apropriada
- Infraestrutura central primeiro
- Implementação sistemática de ferramentas
- Práticas específicas da linguagem
- Avaliações abrangentes

### Validação
- Revisão de qualidade obrigatória
- Teste e build seguros
- Lista de verificação específica da linguagem
- Avaliações com 10 questões

## Recursos Técnicos

### Documentação Obrigatória
- Protocolo MCP completo
- Melhores práticas universais
- Guias específicos de linguagem
- Guia de criação de avaliações

### Processo de Implementação
- Pesquisa profunda primeiro
- Planejamento abrangente
- Implementação sistemática
- Revisão e refinamento
- Criação de avaliações

### Qualidade
- Princípios centrados em agente
- Processo de 4 fases
- Documentação abrangente
- Avaliações realistas

## Manutenção e Atualizações

### Atualizações Técnicas
- Manter dependências atuais
- Atualizar documentação do protocolo
- Manter compatibilidade
- Testar com novas versões

### Extensões
- Adicionar novas ferramentas
- Expandir funcionalidades
- Melhorar performance
- Aprimorar experiência do usuário
