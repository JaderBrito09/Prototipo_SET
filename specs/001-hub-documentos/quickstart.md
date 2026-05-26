# Quickstart: Hub Unificado de Parametrização

## Descrição
Este módulo frontend é responsável por renderizar a interface unificada de configuração de documentos do SET, consumindo os endpoints definidos no contrato de API para persistência transparente nas tabelas legadas.

## Como Iniciar o Desenvolvimento

1. **Dependências:**
   Como estamos assumindo o uso do ecossistema React/Angular padrão do Estado (definido na constituição do SET):
   ```bash
   npm install
   ```

2. **Mock Server:**
   Para desenvolver o frontend isolado, utilize um mock server para os contratos:
   ```bash
   npm run start:mock
   ```

3. **Rodando a Aplicação:**
   ```bash
   npm run dev
   ```
   Acesse: `http://localhost:3000/hub-documentos`

## Referência Visual e Comportamental
Antes de iniciar a implementação, consulte o protótipo funcional em:
`specs/001-hub-documentos/preview/index.html`

Este arquivo contém o comportamento esperado para:
- Modais de cadastro com códigos auto-gerados.
- Transições entre listagem de anexos e configuração profunda (drill-down).
- Comportamento dos switches horizontais de Seleção e Obrigatoriedade.

## Fluxo de Trabalho (Development Workflow)
Ao implementar as páginas, utilize os componentes padronizados do Design System do SET. Garanta que as lógicas de State Management estão propagando corretamente os eventos de `PATCH` (auto-save) ao alternar os switches na grid de parametrização.