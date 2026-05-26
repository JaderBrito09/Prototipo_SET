# Backlog - Hub Unificado de Parametrização e Configuração de Documentos (SET)

Este documento contém a lista priorizada de Histórias de Usuário e Requisitos Funcionais para o desenvolvimento do Hub Unificado de Documentos.

## 1. Visão Geral
O objetivo é consolidar a gestão de documentos em uma única interface, eliminando a fragmentação atual e melhorando a experiência do gestor.

---

## 2. Histórias de Usuário (User Stories)

### US200 - Hub Unificado de Parametrização e Configuração de Documentos
**Prioridade:** Alta | **Status:** Pendente

**Descrição:**
Como gestor do SET, quero gerenciar a criação, a localização e as regras de obrigatoriedade dos documentos em uma única interface visual, para centralizar a governança de documentos exigidos das Instituições.

**Critérios de Aceitação:**
- [ ] **Cenário 1: Navegação por Contexto.** Ao selecionar uma etapa na árvore lateral, a tabela central deve carregar os documentos vinculados.
- [ ] **Cenário 2: Configuração Inline.** Alterações em switches (Ativo/Inativo), obrigatoriedade, Tipo de Pessoa e Grupo de Documento devem ser feitas diretamente na grid.
- [ ] **Cenário 3: Cadastro Ágil.** Botão "+ Novo Documento" abre gaveta lateral (drawer) para cadastro rápido sem sair da tela.
- [ ] **Cenário 4: Inversão de Perspectiva.** Opção de alternar visualização para "Foco no Documento", listando etapas onde o documento é exigido.

---

## 3. Requisitos Funcionais (Backlog de Itens)

| ID | Item | Descrição | Prioridade | Status |
| :--- | :--- | :--- | :--- | :--- |
| **RF001** | Interface de 3 Painéis | Layout: Navegação (Esq), Trabalho (Centro), Gaveta (Dir). | Alta | ⏳ Pendente |
| **RF002** | Árvore de Contexto | Treeview para seleção de telas/módulos/etapas. | Alta | ⏳ Pendente |
| **RF003** | Edição Inline | Configuração direta na grid (Switch, Checkbox, Dropdown). | Alta | ⏳ Pendente |
| **RF004** | Gaveta de Criação | Drawer lateral para cadastro de "Documento Adicional". | Alta | ⏳ Pendente |
| **RF005** | Alternância de Perspectiva | Troca de visão: "Por Tela/Etapa" vs "Por Documento". | Média | ⏳ Pendente |
| **RF006** | Exportação Unificada | Exportação da visão atual para Excel e PDF. | Baixa | ⏳ Pendente |

---

## 4. Regras de Negócio e Requisitos Não-Funcionais

| ID | Título | Descrição |
| :--- | :--- | :--- |
| **RN001** | Controle de Acesso | Acesso restrito a usuários com permissão "Manter Configuração". |
| **RN002** | Persistência Transparente | Mapeamento automático para tabelas legadas (SIFITB02 / STRTB02). |
| **RN003** | Auto-save / Batch Save | Salvamento assíncrono ou botão flutuante para evitar perda de dados. |
| **RN004** | Responsividade | A interface deve ser funcional em resoluções desktop padrão (mínimo 1280px). |

---

## 5. Histórico de Versões
- **v1.0 (26/05/2026):** Criação inicial baseada no PRD-SET-001.
