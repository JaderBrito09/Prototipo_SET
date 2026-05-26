# Feature Specification: Configuração de Documentos e Anexos (SET)

**Feature Branch**: `001-hub-documentos`
**Created**: 26 de Maio de 2026
**Status**: Ready for Planning
**Reference Prototype**: `specs/001-hub-documentos/preview/index.html`

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Catálogo Central de Documentos (Priority: P1)

Como gestor do SET, quero acessar o sub-menu "Documentos" para visualizar e cadastrar documentos exigidos, separando claramente o que é do próprio SET e o que vem de Integração (SIFI), com códigos automáticos e rastreabilidade.

**Why this priority**: É a fundação do cadastro mestre. Sem ele, os documentos não existem para serem anexados às grids dinâmicas.

**Acceptance Scenarios**:

1. **Given** que acessei o sub-menu "Documentos", **When** eu selecionar a origem "Integração" no filtro, **Then** a tabela deve exibir apenas os documentos que possuem chaves externas.
2. **Given** que clico em "Cadastrar" em Documentos, **When** o modal abrir, **Then** o campo "Código" deve vir preenchido automaticamente com o próximo número sequencial (ex: SET0004).
3. **Given** que estou visualizando um documento existente, **Then** o sistema deve exibir os campos de auditoria "Data de Cadastro" e "Usuário Cadastrante" em uma área destacada.

---

### User Story 2 - Gestão de Anexos por Funcionalidade (Priority: P1)

Como gestor do SET, quero acessar o sub-menu "Anexos" para ver em quais funcionalidades e locais existem campos de upload, com indicadores claros da quantidade de documentos já vinculados.

**Why this priority**: Substitui o modelo antigo "cego". Permite que o sistema escale ao adicionar novas páginas dinamicamente.

**Acceptance Scenarios**:

1. **Given** que acesso o sub-menu "Anexos", **When** eu visualizo a grid principal, **Then** as colunas "N. Documentos" e "Ações" devem estar centralizadas para melhor leitura.
2. **Given** um local na grid de Anexos, **When** eu clico no ícone de "Engrenagem", **Then** sou levado à tela de configuração daquele local específico.
3. **Given** um local na grid de Anexos, **When** eu clico no ícone de "Olho", **Then** sou levado à mesma tela de configuração, mas em modo leitura e apenas com os documentos já vinculados.

---

### User Story 3 - Parametrização Horizontal e Independente (Priority: P1)

Como gestor do SET, quero configurar os documentos vinculados a um local usando seletores horizontais (InputSwitch) para definir a presença e a obrigatoriedade de forma independente e visualmente compacta.

**Why this priority**: Este é o "coração da parametrização". A interface compacta evita quebras de linha e erros de interpretação.

**Acceptance Scenarios**:

1. **Given** a tela de Configurar Parametrização, **When** eu alterno o switch "Selecionar" para SIM, **Then** o switch "Obrigatório?" deve ser habilitado (iniciando como NÃO por padrão).
2. **Given** que um documento está com "Selecionar" como NÃO, **When** eu tentar interagir com "Obrigatório?", **Then** o switch deve estar desabilitado.
3. **Given** que altero qualquer switch na grid, **Then** o sistema deve emitir uma notificação de "Alteração salva automaticamente".

---

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001 (Sub-menus)**: O sistema deve fornecer dois sub-menus sob "Configurações": "Documentos (Catálogo)" e "Anexos (Parametrização)".
- **FR-002 (Cadastro Mestre)**: O modal de cadastro de documentos deve incluir Código (Auto-gerado SET+4 dígitos), Nome, Descrição e Situação (Ativo/Inativo).
- **FR-003 (Auditoria de Cadastro)**: A visualização de documentos deve expor Data de Cadastro e Usuário Cadastrante.
- **FR-004 (Filtros Padronizados)**: Todas as telas de listagem devem possuir filtros dentro de um `filter-card-wrapper` com abas identificadoras.
- **FR-005 (Exportação)**: Todas as listagens principais devem possuir botões de exportação para PDF e Excel (formato iconográfico SVG).
- **FR-006 (Configuração Horizontal)**: A parametrização de anexos deve utilizar `InputSwitch` com rótulos dinâmicos "SIM/NÃO" para as colunas "Selecionar" e "Obrigatório?".
- **FR-007 (Modo Visualizar Anexos)**: O modo de visualização de parametrização deve filtrar a lista para exibir apenas documentos ativos e desabilitar todos os controles de edição.
- **FR-008 (Autocomplete de Vínculo)**: A tela de configuração deve possuir um campo "Documento:" com busca AutoComplete e botão "Consultar" para vincular novos itens do catálogo.

### UI/UX Standards (derived from Prototype)

- **Colors**: Azul Escuro (`#0a2566`) para ações primárias, Azul Médio (`#113480`) para secundárias, Verde (`#0e9f6e`) para visualização/sucesso.
- **Alignment**: Colunas de Texto alinhadas à esquerda; Colunas de Números, Situação (Ícones) e Ações centralizadas (cabeçalho e corpo).
- **Components**: Uso obrigatório de `InputSwitch` para estados binários horizontais; `status-circle-custom` (círculo com ícone pi-check/pi-times) para Situação.
- **Compactness**: O `InputSwitch` ativo deve usar a cor Azul Escuro institucional para manter a identidade visual.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Redução da altura média das linhas de parametrização em 40% através do uso de `InputSwitch` horizontal em vez de dropdowns ou botões grandes.
- **SC-002**: 100% de rastreabilidade garantida pela exposição dos campos de auditoria no catálogo mestre.
- **SC-003**: Interface 100% consistente entre os módulos através do reuso do padrão `filter-card-wrapper`.

## Key Entities

- **DocumentoMestre**: Registro no catálogo. (ID, Código, Nome, Descrição, Origem, Situação, DataCadastro, UsuarioID).
- **LocalAnexo**: Ponto de upload. (ID, Funcionalidade, LocalNome).
- **Parametrizacao**: Vínculo entre Documento e Local. (ID, LocalAnexoID, DocumentoID, IsAtivo, IsObrigatorio, TipoPessoa, GrupoID).

## Assumptions

- O código SET0001 é sequencial global para documentos internos, independente da funcionalidade onde serão aplicados.
- O auto-save é o padrão esperado para a grid de parametrização para agilizar o processo de "checklist" do gestor.
