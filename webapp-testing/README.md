# Análise do Skill Webapp Testing

## Visão Geral
Este skill fornece um toolkit para interagir e testar aplicações web locais usando Playwright. Suporta verificação de funcionalidade frontend, depuração de comportamento UI, captura de screenshots do navegador e visualização de logs do navegador.

## Estrutura do SKILL.md

### Metadados YAML
- **name**: webapp-testing
- **description**: Toolkit para interagir e testar aplicações web locais usando Playwright
- **license**: Termos completos em LICENSE.txt

### Conteúdo Principal

#### 1. Árvore de Decisão
- **HTML estático**: Ler arquivo HTML diretamente para identificar seletores
- **Webapp dinâmico**: Verificar se servidor já está rodando
- **Padrão reconhecimento-ação**: Navegar, aguardar, inspecionar, executar

#### 2. Gerenciamento de Servidor
- **Script with_server.py**: Gerencia ciclo de vida do servidor
- **Suporte a múltiplos servidores**: Backend + frontend
- **Automação**: Scripts Python executados após servidor estar pronto

#### 3. Implementação Playwright
- **Configuração básica**: sync_playwright, chromium headless
- **Aguardo obrigatório**: networkidle antes da inspeção
- **Limpeza**: Sempre fechar navegador

#### 4. Padrão Reconhecimento-Ação
- **Inspeção DOM**: Screenshot, conteúdo, localizadores
- **Identificação de seletores**: A partir do estado renderizado
- **Execução de ações**: Usando seletores descobertos

## Padrões Identificados

### Árvore de Decisão
- **HTML estático**: Caminho direto para seletores
- **Webapp dinâmico**: Verificação de servidor primeiro
- **Reconhecimento-ação**: Padrão obrigatório para apps dinâmicos
- **Aguardo networkidle**: Crítico para execução de JavaScript

### Gerenciamento de Servidor
- **Script with_server.py**: Automação completa do ciclo de vida
- **Múltiplos servidores**: Backend e frontend simultâneos
- **Portas configuráveis**: Diferentes portas para diferentes serviços
- **Automação integrada**: Scripts executados após servidor pronto

### Implementação Playwright
- **Configuração padrão**: sync_playwright, chromium headless
- **Aguardo obrigatório**: networkidle antes da inspeção
- **Limpeza adequada**: Fechar navegador sempre
- **Modo headless**: Sempre para automação

## Características Únicas

### Abordagem de Reconhecimento
- Padrão reconhecimento-ação obrigatório
- Inspeção DOM antes de ações
- Identificação de seletores do estado renderizado
- Execução sistemática de ações

### Gerenciamento Automático de Servidor
- Script que gerencia ciclo de vida completo
- Suporte a múltiplos servidores
- Automação integrada
- Ambiente pronto para uso

### Prevenção de Erros Comuns
- Aguardo networkidle obrigatório
- Modo headless para automação
- Limpeza adequada de recursos
- Aguardo de execução JavaScript

## Recursos Incluídos

### Scripts de Automação
- **with_server.py**: Gerenciamento de ciclo de vida do servidor
- **Suporte a múltiplos servidores**: Backend + frontend
- **Configuração automática**: Portas e comandos

### Exemplos de Uso
- **element_discovery.py**: Descobrindo botões, links e inputs
- **static_html_automation.py**: Usando URLs file:// para HTML local
- **console_logging.py**: Capturando logs do console durante automação

### Estrutura de Diretórios
```
webapp-testing/
├── SKILL.md (obrigatório)
├── LICENSE.txt
├── scripts/
│   └── with_server.py
├── examples/
│   ├── element_discovery.py
│   ├── static_html_automation.py
│   └── console_logging.py
└── RULES.md (regras CURSOR)
```

## Fluxo de Trabalho

### Processo de Teste
1. **Identificar tipo**: HTML estático ou webapp dinâmico
2. **Gerenciar servidor**: Se necessário, usar with_server.py
3. **Reconhecimento**: Navegar, aguardar, inspecionar
4. **Ação**: Executar ações com seletores descobertos
5. **Verificação**: Capturar screenshots, verificar resultados

### Constantes
- Padrão reconhecimento-ação
- Aguardo networkidle obrigatório
- Modo headless para automação
- Limpeza adequada de recursos

### Variáveis
- Tipo de aplicação (estática/dinâmica)
- Seletores específicos
- Ações necessárias
- Resultados esperados

## Casos de Uso

### Quando Usar
- Testar aplicações web locais
- Verificar funcionalidade frontend
- Depurar comportamento UI
- Capturar screenshots para verificação
- Visualizar logs do navegador

### Quando NÃO Usar
- Testes de aplicações remotas
- Testes que não precisam de navegador
- Automação de desktop
- Testes de API sem interface

## Qualidade e Padrões

### Requisitos de Automação
- Aguardo networkidle obrigatório
- Modo headless para automação
- Limpeza adequada de recursos
- Aguardo de execução JavaScript

### Padrões de Teste
- Reconhecimento antes da ação
- Identificação de seletores do estado renderizado
- Execução sistemática de ações
- Verificação de resultados

### Prevenção de Erros
- Não inspecionar DOM antes de networkidle
- Usar headless=True para automação
- Fechar navegador adequadamente
- Aguardar execução JavaScript

## Recursos Técnicos

### Gerenciamento de Servidor
- Script with_server.py para ciclo de vida
- Suporte a múltiplos servidores
- Configuração automática de portas
- Automação integrada

### Implementação Playwright
- Configuração padrão com sync_playwright
- Modo headless obrigatório
- Aguardo networkidle crítico
- Limpeza adequada de recursos

### Padrões de Automação
- Reconhecimento-ação sistemático
- Inspeção DOM antes de ações
- Identificação de seletores
- Execução de ações descobertas

## Manutenção e Atualizações

### Atualizações Técnicas
- Manter Playwright atual
- Atualizar padrões de automação
- Manter compatibilidade
- Testar com novas versões

### Extensões
- Adicionar novos padrões de automação
- Expandir capacidades de teste
- Melhorar tratamento de erros
- Aprimorar ferramentas de depuração
