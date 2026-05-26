# SET Design System

Este documento descreve os padrões visuais, componentes e diretrizes de UX adotados para o ecossistema SET (Sistema Estadual de Transferência), baseados no protótipo funcional do Hub de Documentos.

---

## 🎨 Paleta de Cores

| Cor | Hex | Uso |
| :--- | :--- | :--- |
| **Primary Blue Dark** | `#0a2566` | Logo, Cabeçalho, Botões Primários, Seletores Ativos. |
| **Primary Blue Medium** | `#113480` | Botões Secundários, Ícones de Edição, Filtros. |
| **Success Green** | `#0e9f6e` | Situações Ativas, Botões de Visualização, Confirmações. |
| **Danger Red** | `#e02424` | Situações Inativas, Ações de Cancelamento/Exclusão. |
| **Warning Yellow** | `#e3a008` | Alertas, Cards de Informação, Pendências. |
| **Surface Gray** | `#f8fafc` | Fundos de cards, áreas de leitura, headers de grid. |
| **Border Gray** | `#e5e7eb` | Divisores, bordas de tabelas e inputs. |

---

## 🔡 Tipografia e Textos

- **Fonte Principal**: Sans-serif (System UI, Inter ou similar).
- **Títulos**: Negrito (900), cor Blue Dark.
- **Rótulos (Labels)**: Tamanho reduzido (0.8rem), cor Slate-600.
- **Placeholders**: Itálico, cor Slate-400.
- **Centralização**:
    - Campos de Nome/Descrição: Alinhados à esquerda.
    - Campos de Código/Número/Status/Ações: **Sempre centralizados** (cabeçalho e corpo).

---

## 🧩 Componentes Customizados

### 1. Filter Card Wrapper
Padrão utilizado para todos os filtros de listagem.
- **Aba (Tab)**: Um rótulo retangular acima do card que identifica a funcionalidade.
- **Corpo**: Fundo branco, sombra leve, borda suave.
- **Botões**: Alinhados à direita, com espaço de 0.5rem entre eles.

### 2. Status Circle Custom
Representação visual de estados binários (Ativo/Inativo).
- **Ativo**: Círculo verde com ícone `pi-check`.
- **Inativo**: Círculo vermelho com ícone `pi-times`.
- **Dimensão**: 20px x 20px, centralizado na célula da tabela.

### 3. Ações de Grid (Circular Buttons)
Botões de ação compactos e circulares (24px x 24px):
- **Visualizar (Verde)**: Ícone `pi-eye`.
- **Editar (Azul Médio)**: Ícone `pi-pencil`.
- **Configurar (Cinza)**: Ícone `pi-cog`.

### 4. InputSwitch Horizontal (Toggle)
Utilizado para seleções de Sim/Não em grids.
- **Cor Ativa**: Deve usar o `Primary Blue Dark`.
- **Rótulo de Suporte**: Deve exibir o texto "SIM" ou "NÃO" ao lado do switch para redundância e clareza.
- **Modo Leitura**: O switch deve ser exibido como `disabled` em telas de visualização.

---

## 📐 Layout e Estrutura

### Cabeçalho (Header)
- Logo "SET" em negrito extremo à esquerda.
- Divisor vertical após o logo com o nome completo do sistema.
- Identificação do usuário e botão "Sair" à direita.

### Navegação (Breadcrumb)
- Barra de navegação clara logo abaixo do header.
- Uso de ícones para Home e separadores de nível (`pi-chevron-right`).

### Tabelas (DataTable)
- Borda externa obrigatória: `1px solid #e5e7eb`.
- Arredondamento de bordas: `6px`.
- Linhas com separação clara e efeito de hover.
- Colunas de texto principal (Nome/Razão Social) em **Negrito**.

---

## 📥 Exportação
Sempre incluir botões de exportação (PDF e Excel) acima das grids de listagem.
- **Formato**: Botões iconográficos (SVG) representando os tipos de arquivos.
- **Posição**: Alinhados à direita, logo acima do cabeçalho da tabela.

---

**Versão**: 1.0.0 | **Data**: 26/05/2026 | **Baseado em**: `specs/001-hub-documentos/preview/index.html`
