# Análise do Skill Algorithmic Art

## Visão Geral
Este skill cria arte algorítmica usando p5.js com aleatoriedade controlada por sementes e exploração interativa de parâmetros. Segue um processo de duas etapas: criação de filosofia algorítmica, seguida da implementação em código.

## Estrutura do SKILL.md

### Metadados YAML
- **name**: algorithmic-art
- **description**: Descrição clara do que o skill faz e quando usar
- **license**: Termos completos em LICENSE.txt

### Conteúdo Principal

#### 1. Criação de Filosofia Algorítmica
- **Objetivo**: Criar movimentos estéticos computacionais, não imagens estáticas
- **Estrutura**: 4-6 parágrafos substanciais
- **Foco**: Expressão algorítmica, comportamento emergente, beleza computacional
- **Padrões**: Enfatizar artesanato repetidamente, deixar espaço criativo

#### 2. Implementação P5.js
- **Template obrigatório**: Sempre usar `templates/viewer.html` como base
- **Elementos fixos**: Estrutura de layout, branding Anthropic, controles de seed
- **Elementos variáveis**: Algoritmo p5.js, parâmetros, controles de UI
- **Técnicas**: Aleatoriedade com sementes, parâmetros baseados na filosofia

#### 3. Criação de Artefato Interativo
- **Formato**: HTML único e autocontido
- **Funcionalidades**: Navegação por seeds, controles de parâmetros, botões de ação
- **Compatibilidade**: Funciona imediatamente no claude.ai ou qualquer navegador

## Padrões Identificados

### Filosofia Algorítmica
- **Nomenclatura**: Movimentos de 1-2 palavras ("Organic Turbulence", "Quantum Harmonics")
- **Estrutura**: Manifesto para movimento de arte generativa
- **Conteúdo**: Processos computacionais, campos de ruído, sistemas orgânicos
- **Qualidade**: Enfatizar artesanato meticuloso, expertise profunda

### Implementação Técnica
- **Aleatoriedade**: Sempre usar sementes para reprodutibilidade
- **Parâmetros**: Focar em propriedades do sistema, não tipos de padrão
- **Algoritmo**: Flui da filosofia, não de menu de opções
- **Qualidade**: Equilíbrio, harmonia de cores, composição, performance

### Interface do Usuário
- **Estrutura fixa**: Header, sidebar, área principal do canvas
- **Seção Seed**: Display, botões prev/next/random/jump
- **Seção Parâmetros**: Controles específicos para cada arte
- **Seção Cores**: Opcional, apenas se a arte precisa de cores ajustáveis
- **Seção Ações**: Regenerar, resetar, baixar

## Recursos Incluídos

### Templates
- **viewer.html**: Ponto de partida obrigatório para todos os artefatos HTML
- **generator_template.js**: Referência para melhores práticas p5.js

### Estrutura de Diretórios
```
algorithmic-art/
├── SKILL.md (obrigatório)
├── LICENSE.txt
├── templates/
│   ├── viewer.html (template base)
│   └── generator_template.js (referência)
└── RULES.md (regras CURSOR)
```

## Fluxo de Trabalho

### Processo Criativo
1. **Interpretar intenção do usuário** - Que estética está sendo buscada?
2. **Criar filosofia algorítmica** (4-6 parágrafos)
3. **Implementar em código** - Construir algoritmo que expressa a filosofia
4. **Projetar parâmetros apropriados** - O que deve ser ajustável?
5. **Construir controles de UI correspondentes** - Sliders/inputs para parâmetros

### Constantes
- Branding Anthropic (cores, fontes, layout)
- Navegação por seeds (sempre presente)
- Artefato HTML autocontido

### Variáveis
- O algoritmo em si
- Os parâmetros
- Os controles de UI
- O resultado visual

## Características Únicas

### Abordagem Filosófica
- Criação de movimentos estéticos computacionais
- Ênfase em processo sobre produto
- Expressão paramétrica através de relacionamentos matemáticos
- Liberdade artística com espaço para interpretação

### Implementação Técnica
- Aleatoriedade controlada por sementes (padrão Art Blocks)
- Parâmetros emergem naturalmente da filosofia
- Algoritmos únicos baseados na visão específica
- Qualidade de galeria com artesanato meticuloso

### Interface Consistente
- Estrutura fixa preserva UX consistente
- Branding Anthropic mantido
- Navegação por seeds sempre presente
- Controles específicos para cada obra de arte

## Casos de Uso

### Quando Usar
- Usuários solicitam arte usando código
- Arte generativa, arte algorítmica
- Campos de fluxo, sistemas de partículas
- Exploração de parâmetros interativos

### Quando NÃO Usar
- Imagens estáticas simples
- Arte copiada de artistas existentes
- Templates ou layouts fixos
- Arte não algorítmica

## Qualidade e Padrões

### Requisitos de Artesanato
- Algoritmos que parecem refinados através de incontáveis iterações
- Cada parâmetro sintonizado cuidadosamente
- Cada padrão emerge com propósito
- Não é ruído aleatório - é caos controlado

### Padrões de Código
- Estrutura clara e bem documentada
- Comentários explicando algoritmos complexos
- Tratamento de casos extremos
- Otimização para performance

### Validação
- Teste com múltiplas sementes
- Verificação de controles de parâmetros
- Verificação de tamanho de arquivo e performance
- Garantia de reprodutibilidade
