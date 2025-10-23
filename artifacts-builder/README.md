# Análise do Skill Artifacts Builder

## Visão Geral
Este skill fornece uma suíte de ferramentas para criar artefatos HTML elaborados e multi-componentes do claude.ai usando tecnologias frontend modernas (React, Tailwind CSS, shadcn/ui). Projetado para artefatos complexos que requerem gerenciamento de estado, roteamento ou componentes shadcn/ui.

## Estrutura do SKILL.md

### Metadados YAML
- **name**: artifacts-builder
- **description**: Suíte de ferramentas para criar artefatos HTML elaborados usando tecnologias frontend modernas
- **license**: Termos completos em LICENSE.txt

### Conteúdo Principal

#### 1. Stack Tecnológico
- **React 18 + TypeScript**: Base do projeto
- **Vite**: Ferramenta de build
- **Parcel**: Empacotamento
- **Tailwind CSS 3.4.1**: Sistema de estilização
- **shadcn/ui**: Sistema de temas
- **Node 18+**: Compatibilidade

#### 2. Processo de Trabalho
- **Inicialização**: Script `init-artifact.sh` para criar projeto
- **Desenvolvimento**: Editar arquivos gerados
- **Empacotamento**: Script `bundle-artifact.sh` para criar HTML único
- **Compartilhamento**: Arquivo HTML autocontido

#### 3. Diretrizes de Design
- **Anti-padrões**: Evitar layouts centralizados excessivos, gradientes roxos, cantos uniformes, fonte Inter
- **Melhores práticas**: Layouts diversos, paletas variadas, tratamentos de cantos mistos

## Padrões Identificados

### Stack Tecnológico
- **React + TypeScript**: Base moderna e tipada
- **Vite**: Build tool rápido e eficiente
- **Parcel**: Empacotamento com suporte a aliases
- **Tailwind CSS**: Sistema de estilização utilitário
- **shadcn/ui**: Componentes pré-instalados (40+)

### Processo de Inicialização
- **Script obrigatório**: `init-artifact.sh <project-name>`
- **Configuração automática**: Aliases de caminho, componentes, dependências
- **Compatibilidade**: Node 18+ com auto-detecção
- **Estrutura**: Projeto completo configurado

### Processo de Empacotamento
- **Script obrigatório**: `bundle-artifact.sh`
- **Requisito**: `index.html` no diretório raiz
- **Saída**: `bundle.html` autocontido
- **Funcionalidade**: Todos os assets inlineados

## Características Únicas

### Inicialização Automática
- Script que configura projeto completo
- 40+ componentes shadcn/ui pré-instalados
- Todas as dependências Radix UI incluídas
- Aliases de caminho configurados
- Compatibilidade Node 18+ automática

### Empacotamento Inteligente
- Cria artefato HTML único e autocontido
- Inlineia todos os assets (JS, CSS, dependências)
- Funciona imediatamente em conversas Claude
- Sem dependências externas

### Anti-Padrões de Design
- Evita "AI slop" comum
- Layouts centralizados excessivos
- Gradientes roxos
- Cantos uniformes
- Fonte Inter excessiva

## Recursos Incluídos

### Scripts de Automação
- **init-artifact.sh**: Inicialização de projeto
- **bundle-artifact.sh**: Empacotamento para HTML único
- **Configuração automática**: Dependências e configurações

### Componentes Pré-instalados
- **40+ componentes shadcn/ui**: Prontos para uso
- **Dependências Radix UI**: Todas incluídas
- **Sistema de temas**: Tailwind CSS configurado
- **Aliases de caminho**: `@/` configurado

### Estrutura de Diretórios
```
artifacts-builder/
├── SKILL.md (obrigatório)
├── LICENSE.txt
├── scripts/
│   ├── init-artifact.sh
│   ├── bundle-artifact.sh
│   └── shadcn-components.tar.gz
└── RULES.md (regras CURSOR)
```

## Fluxo de Trabalho

### Processo Completo
1. **Inicializar projeto**: `bash scripts/init-artifact.sh <project-name>`
2. **Desenvolver artefato**: Editar arquivos gerados
3. **Empacotar**: `bash scripts/bundle-artifact.sh`
4. **Compartilhar**: Arquivo HTML autocontido
5. **Testar (opcional)**: Apenas se necessário

### Constantes
- Stack tecnológico obrigatório
- Scripts de automação
- Processo de empacotamento
- Formato de saída HTML

### Variáveis
- Nome do projeto
- Funcionalidades específicas
- Componentes utilizados
- Design e estilização

## Casos de Uso

### Quando Usar
- Artefatos complexos com múltiplos componentes
- Requer gerenciamento de estado
- Precisa de roteamento
- Usa componentes shadcn/ui
- Artefatos elaborados e interativos

### Quando NÃO Usar
- Artefatos HTML/JSX simples de arquivo único
- Projetos sem necessidade de componentes complexos
- Artefatos básicos sem estado
- Projetos que não precisam de empacotamento

## Qualidade e Padrões

### Requisitos Técnicos
- Stack tecnológico obrigatório
- Configuração automática completa
- Empacotamento funcional
- Artefato autocontido

### Padrões de Design
- Evitar anti-padrões comuns
- Layouts diversos e criativos
- Paletas de cores variadas
- Tratamentos de design mistos

### Validação
- Verificar estrutura do projeto
- Testar funcionalidade
- Validar empacotamento
- Garantir autocontenção

## Recursos Técnicos

### Inicialização de Projeto
- Script automatizado completo
- Configuração de todas as dependências
- Aliases de caminho configurados
- Componentes pré-instalados

### Empacotamento
- Processo automatizado
- Inlineação de todos os assets
- Artefato HTML único
- Funcionamento imediato

### Anti-Padrões
- Evitar layouts centralizados excessivos
- Evitar gradientes roxos
- Evitar cantos uniformes
- Evitar fonte Inter excessiva

## Manutenção e Atualizações

### Atualizações Técnicas
- Manter dependências atuais
- Atualizar ferramentas de build
- Manter compatibilidade
- Testar com novas versões

### Extensões
- Adicionar novos componentes
- Expandir funcionalidades
- Melhorar performance
- Aprimorar experiência do usuário
