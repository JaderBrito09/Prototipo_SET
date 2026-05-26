# Implementation Plan: Configuração de Documentos e Anexos (SET)

**Branch**: `001-hub-documentos` | **Date**: 26 de Maio de 2026 | **Spec**: [spec.md](./spec.md)

**Input**: Feature specification from `specs/001-hub-documentos/spec.md`

## Summary

O objetivo é substituir o layout consolidado de três painéis por uma arquitetura focada em Separação de Responsabilidades (Separation of Concerns). Serão construídas duas telas/sub-menus independentes dentro de "Configuração":
1. **Documentos**: Um catálogo mestre que lista e permite criar novos documentos (diferenciando origens como SIFI vs Nativos).
2. **Anexos**: Uma tela que lista os locais do sistema que possuem uploads, permitindo ao gestor clicar em "Editar" para amarrar os documentos do catálogo àquele local, usando um Autocomplete e definindo regras como Tipo de Pessoa e Grupo visivelmente na grid.

## Technical Context

**Language/Version**: JavaScript/TypeScript (Padrão Web do SET)

**Primary Dependencies**: Framework Frontend corporativo (React ou Angular)

**Storage**: Consumo de APIs REST (Backend SIFITB02/STRTB02)

**Testing**: Jest (Unit/Component), Cypress ou Playwright (E2E)

**Target Platform**: Navegadores Web Modernos Corporativos

**Project Type**: Web Service/SPA Module

**Performance Goals**: Carregamento rápido das grids e busca instantânea no Autocomplete (<300ms).

**Constraints**: Resolução de 1280px; o módulo Autocomplete precisa lidar eficientemente com listas de documentos oriundos de integrações externas sem travar a interface.

**Scale/Scope**: Substituição dos modais confusos e do fluxo "cego" de vinculação do banco de dados antigo por telas gerenciais claras e focadas em listas.

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- [x] **I. Separation of Concerns (Master vs Instance):** A criação de duas telas distintas ("Documentos" e "Anexos") separa perfeitamente o catálogo da aplicação contextual.
- [x] **II. Transparent Business Rules:** A tela de Edição de Anexos expõe `Tipo de Pessoa` e `Grupo Documento` explicitamente na Grid.
- [x] **III. Component Reusability & Consistency:** As duas telas usarão os mesmos componentes de Filtro, Tabela e Paginação do design system do SET.
- [x] **IV. Data Integrity & Transparent Persistence:** Persistência clara ao vincular um documento a uma grid.
- [x] **VI. Integration Visibility:** A tela de Documentos possui filtro e coluna explícita para "Origem" (Integração vs SET).

**Status:** Aprovado. Alinhado com a constituição v2.0.0.

## Project Structure

### Documentation (this feature)

```text
specs/001-hub-documentos/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

### Source Code (repository root)

```text
# Web application (Frontend Module Focus)
frontend/
├── src/
│   ├── components/
│   │   ├── AutocompleteDocumentos/  # Componente crítico para vinculação
│   │   ├── FilterCard/              # Card de filtro genérico
│   │   └── ParameterGrid/           # Grid que expõe as regras explícitas (PF/PJ)
│   ├── pages/
│   │   ├── Documentos/
│   │   │   ├── DocumentosListPage.tsx
│   │   │   └── NovoDocumentoModal.tsx
│   │   └── Anexos/
│   │       ├── AnexosListPage.tsx
│   │       └── EditarAnexoParametrizacao.tsx
│   └── services/
│       └── ConfigApi/               # Conexão com endpoints de mestre e vinculação
└── tests/
    └── e2e/                         # Fluxos isolados por sub-menu
```

**Structure Decision**: A estrutura foi dividida por responsabilidades (Pages) em vez de um único `HubLayout` complexo. Os componentes pesados foram isolados (`AutocompleteDocumentos` e `ParameterGrid`) para reuso.

## Complexity Tracking

> N/A. Não houve quebras da constituição que necessitem de justificativa de complexidade adicional.
