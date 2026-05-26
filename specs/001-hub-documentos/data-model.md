# Data Model: Documentos e Anexos

This document describes the logical data model required to support the new two-screen frontend interface.

## Entities

### 1. DocumentoMestre (Utilizado no Sub-menu: Documentos)
Representa o catálogo central de documentos.

**Fields:**
- `id` (UUID/Integer) - Identificador único.
- `codigo` (String) - Formato `SETXXXX` (ex: SET0001) para documentos nativos; código de integração (ex: SFI-991) para externos.
- `nome` (String) - Título do documento.
- `descricao` (String) - Breve descrição da finalidade do documento.
- `origem` (Enum) - `SET`, `INTEGRACAO` (ex: SIFI).
- `situacao` (Boolean) - Ativo/Inativo globalmente.
- `data_cadastro` (Date) - Data da criação do registro.
- `usuario_cadastrante` (String) - Identificação do usuário que realizou o cadastro.

### 2. LocalAnexo (Utilizado no Sub-menu: Anexos - Tela Principal)
Representa as grids de upload espalhadas pelo sistema.

**Fields:**
- `id` (UUID/Integer) - Identificador único da grid.
- `funcionalidade` (String) - Módulo/Funcionalidade onde ela reside (ex: "Cadastramento").
- `local_nome` (String) - Nome visual da grid/local (ex: "Documento dos Diretores").
- `qtd_documentos_vinculados` (Integer) - Metadado para exibição rápida na tabela principal.

### 3. ParametrizacaoGrid (Utilizado na Tela de Configuração de Anexos)
A amarração entre o catálogo mestre e um local específico.

**Fields:**
- `id` (UUID/Integer) - Identificador único do vínculo.
- `documento_id` (FK -> DocumentoMestre.id)
- `local_id` (FK -> LocalAnexo.id)
- `ativo` (Boolean) - Controlado pela coluna "Selecionar" (InputSwitch SIM/NÃO).
- `obrigatorio` (Boolean) - Controlado pela coluna "Obrigatório?" (InputSwitch SIM/NÃO). Requer `ativo == true`.
- `tipo_pessoa` (Enum) - `FISICA`, `JURIDICA`, `AMBAS`.
- `grupo_documento` (Enum) - `FISCAL`, `DECLARACAO`, `INSTITUCIONAL`.

## Validations & State Transitions

1. **Autocomplete Selection:**
   - O componente Autocomplete busca `DocumentoMestre` filtrando por nome onde `situacao == true`.
   - Ao selecionar um item e confirmar, uma nova linha de `ParametrizacaoGrid` é gerada na tabela da tela "Editar Anexo".

2. **Inline Parameterization Update:**
   - Similar to the previous design, changing `obrigatorio`, `tipo_pessoa`, or `grupo_documento` in the grid of the "Editar Anexo" screen triggers an API patch for that specific `ParametrizacaoGrid` record.