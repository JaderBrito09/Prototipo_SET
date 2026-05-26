| Sistema: Sistema Estadual de Transferências (SET) | Módulo: Configuração |
| :---- | :---- |
| **Código:** US002 - Gestão de Anexos por Funcionalidade | **Data Emissão:** 26/05/2026 |

1. **História do Usuário – Gestão de Anexos por Funcionalidade**

**Eu**, como gestor do SET - Sistema Estadual de Transferências,  
**Quero** configurar quais documentos são exigidos em cada local de upload do sistema  
**Para** garantir que as Instituições apresentem a documentação correta em cada etapa do processo.

2. **Contextualização**

Esta funcionalidade permite a "amarração" entre o catálogo central de documentos e os pontos de upload espalhados pelo sistema (Grids de Anexos). O gestor pode definir não apenas a presença do documento, mas também sua obrigatoriedade através de uma interface simplificada e horizontal.

3. **Como demonstrar**  
* Acessar o sistema SET e navegar até "Anexos (Parametrização)";
* Localizar uma funcionalidade (Ex: Cadastramento) e clicar no ícone de "Engrenagem" (Configurar);
* No detalhamento, utilizar o campo "Documento:" para buscar e vincular novos itens;
* Alternar os switches de "Selecionar" e "Obrigatório?" e observar a notificação de auto-save;
* Validar que, ao desmarcar "Selecionar", o campo "Obrigatório?" torna-se inacessível.

4. **Critérios de Aceitação**   

**Cenário 1: Configurar Vínculo de Documento**

* O usuário clica em "Configurar" em um local específico (Ex: Documento dos Diretores);
* O sistema exibe a listagem de todos os documentos do catálogo mestre;
* O usuário alterna o switch "Selecionar" para SIM em um documento;
* O sistema habilita o switch "Obrigatório?" para aquele documento;
* O sistema exibe mensagem "Alteração salva automaticamente".

**Cenário 2: Visualizar Parametrização Ativa**

* O usuário clica no ícone de "Olho" (Verde) na grid principal de Anexos;
* O sistema exibe apenas os documentos onde "Selecionar" está como SIM;
* Todos os controles (switches e autocomplete) devem estar desabilitados (read-only).

**Cenário 3: Independência de Estados (Selecionar vs Obrigatório)**

* Ao marcar "Selecionar" como SIM pela primeira vez, o campo "Obrigatório?" deve permanecer como NÃO por padrão;
* O usuário deve ser capaz de alterar a obrigatoriedade sem que isso afete o estado de seleção do documento.

5. **Protótipos**

O comportamento visual e interativo desta tela pode ser validado no link abaixo:
[Acessar Protótipo Funcional - Anexos](../../specs/001-hub-documentos/preview/index.html)

6. **Descrição dos Campos**

**Filtros (Tela Principal de Anexos)**

| Informação | Obrigatório | Editável | Tipo | Tamanho | Orientação | Obs. |
| :--- | :---: | :---: | :---: | :---: | :--- | :--- |
| Funcionalidade | Não | Sim | Texto | N/A | Esquerda | Ex: Cadastramento, Proposta. |
| Local | Não | Sim | Texto | N/A | Esquerda | Nome da grid de destino. |
| Situação | Não | Sim | Combo | N/A | Esquerda | Ativo/Inativo. |

**Grid de Detalhamento (Configuração)**

| Informação | Obrigatório | Editável | Tipo | Tamanho | Orientação | Obs. |
| :--- | :---: | :---: | :---: | :---: | :--- | :--- |
| Documento (Vínculo) | Sim | Sim | AutoComplete| N/A | Esquerda | Busca no catálogo mestre. |
| Origem | Sim | Não | Badge | N/A | Esquerda | SET ou SIFI. |
| Documentos | Sim | Não | Texto | N/A | Esquerda | Nome do documento (Negrito). |
| Selecionar | Sim | Sim | Switch | N/A | Centro | Define se o documento aparece no local. |
| Obrigatório? | Sim | Sim | Switch | N/A | Centro | Só editável se Selecionar = SIM. |

7. **Ações**

| Informação | Obrigatório | Editável | Tipo | Tamanho | Orientação | Observações |
| :---: | :---: | :---: | :---: | :---: | :--- | :--- |
| Visualizar | N/A | N/A | Ícone | 24px | Centro | Ícone Olho (Verde). Abre modo leitura filtrado. |
| Configurar | N/A | N/A | Ícone | 24px | Centro | Ícone Engrenagem (Slate). Abre modo edição. |
| Consultar (Vínculo)| N/A | N/A | Botão | N/A | Centro | Azul Médio. Adiciona doc selecionado no autocomplete. |
| Voltar | N/A | N/A | Link | N/A | Esquerda | Retorna para a lista de locais. |

8. **Regra de Negócios**

| Nº | Descrição |
| :---: | :---- |
| **RN001** | A persistência das alterações nos switches (Selecionar/Obrigatório) deve ser automática (Auto-save) para agilizar a configuração. |
| **RN002** | Um documento não pode ser marcado como "Obrigatório" se não estiver "Selecionado". |
| **RN003** | A tela de Visualização deve ocultar documentos do catálogo que não estejam vinculados ao local selecionado. |
| **RN004** | O switch ativado deve utilizar a cor institucional Primary Blue Dark. |

9. **Histórico**

| Data | Versão | Descrição | Responsável |
| :--- | :--- | :--- | :--- |
| 26/05/2026 | 1.0 | Criação inicial baseada no protótipo SET.
