# Product Requirement Document (PRD)
## Projeto: Hub Unificado de Parametrização e Configuração de Documentos (SET)

| Informação | Detalhe |
| :--- | :--- |
| **Código do Documento** | PRD-SET-001 |
| **Data de Atualização** | 26 de Maio de 2026 |
| **Status** | Pronto para Revisão |
| **Autor** | Product Owner (SET) |
| **Versão** | 2.1 (Ajustes Finais de Protótipo e US) |

---

### 1. Introdução e Objetivo
O Sistema Estadual de Transferências (SET) gerencia a exigência de diversos documentos para a formalização e execução de transferências estaduais. Este documento detalha a unificação do gerenciamento de documentos através de dois sub-menus complementares na aba de **Configuração**: **"Documentos (Catálogo)"** e **"Anexos (Parametrização)"**.

Esta abordagem separa o cadastro central dos documentos da sua aplicação contextual nas diversas funcionalidades do sistema, permitindo escalabilidade e clareza nas regras de negócio.

---

### 2. Histórias de Usuário Relacionadas
Para detalhes granulares de cenários de aceite e fluxos de tela, consulte:
* **[US001 - Catálogo Central de Documentos](./historias/US001-Catalogo-Documentos.md)**
* **[US002 - Gestão de Anexos por Funcionalidade](./historias/US002-Parametrizacao-Anexos.md)**

---

### 3. Requisitos Funcionais (RF)

#### 3.1 Sub-menu: "Documentos (Catálogo)"
Centraliza o catálogo mestre de documentos do ecossistema SET.
* **RF001 (Filtros de Catálogo):** Filtragem por Nome, Origem (SET/SIFI) e Situação.
* **RF002 (Cadastro com Código Automático):** O sistema deve gerar códigos sequenciais únicos no padrão `SETXXXX` (ex: SET0001) para documentos nativos.
* **RF003 (Rastreabilidade/Auditoria):** A visualização de um documento deve expor obrigatoriamente a **Data de Cadastro** e o **Usuário Cadastrante**.
* **RF004 (Integração SIFI):** Documentos vindos de integração devem ser exibidos com seus códigos externos originais e possuir restrição de edição de Nome/Descrição.

#### 3.2 Sub-menu: "Anexos (Parametrização)"
Foca na aplicação dos documentos nos locais de upload do sistema.
* **RF005 (Mapa de Funcionalidades):** Listagem de todos os locais (Páginas/Grids) que permitem upload, com contador de documentos já vinculados.
* **RF006 (Configuração Profunda - Drill-down):** Transição da lista principal para uma área de configuração focada no local selecionado.
* **RF007 (Vínculo via Autocomplete):** Busca e adição de documentos do catálogo mestre através de campo Autocomplete.
* **RF008 (Parametrização Horizontal):** Uso de `InputSwitch` para as colunas "Selecionar" e "Obrigatório?", garantindo um layout compacto e horizontal.
* **RF009 (Persistência Automática):** As alterações de switches na grid de parametrização devem disparar **Auto-save** com notificação visual ao usuário.

---

### 4. Regras de Negócio (RN)
* **RN001 (Controle de Acesso):** Acesso restrito a perfis com a permissão "Manter Configuração".
* **RN002 (Dependência de Seleção):** O campo "Obrigatório?" só deve ser habilitado para edição se o documento estiver com o switch "Selecionar" ativo (SIM).
* **RN003 (Isolamento de Origem):** O filtro de "Origem" é mandatório para permitir que o gestor gerencie apenas o que é nativo ou valide o que é integrado sem confusão de dados.
* **RN004 (Visualização Filtrada):** No modo "Visualizar" da parametrização, o sistema deve omitir documentos do catálogo que não estejam vinculados ao local, exibindo uma visão limpa do que está ativo.

---

### 5. Padrões de Interface (UX/UI)
O projeto deve seguir o **[Design System do SET](../docs/design_system.md)**, com destaque para:
* **Cores Institucionais**: Azul Escuro (`#0a2566`) para ações principais e Azul Médio para secundárias.
* **Componentes**: Uso de `filter-card-wrapper` com abas identificadoras e botões de exportação (PDF/Excel) em todas as listagens.
* **Alinhamento**: Colunas de controle (Situação, Selecionar, Ações) devem ser centralizadas; textos (Nome, Local) alinhados à esquerda.

---

### 6. Arquitetura da Solução (Mapa Visual)

```text
⚙️ CONFIGURAÇÃO (Menu Lateral)
 │
 ├── 📄 Documentos (Sub-menu)
 │    ├── Filtros: [Nome] [Origem] [Situação] + [Exportar PDF/Excel]
 │    └── Grid -> [Código SETXXXX] [Nome (Negrito)] [Origem] [Situação] [Ações]
 │
 └── 📎 Anexos (Sub-menu)
      ├── Filtros: [Funcionalidade] [Local] [Situação] + [Exportar PDF/Excel]
      └── Grid -> [Funcionalidade] [Local] [N. Documentos] [Ações (Olho/Engrenagem)]
           └── Drill-down (Configurar/Visualizar):
                ├── Cabeçalho de Contexto (Nome do Local)
                ├── Campo "Documento:" (Autocomplete) para novo vínculo
                └── Grid -> [Origem] [Documentos (Negrito)] [Selecionar (Switch)] [Obrigatório? (Switch)]
```
