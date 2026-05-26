| Sistema: Sistema Estadual de Transferências (SET) | Módulo: Configuração |
| :---- | :---- |
| **Código:** US001 - Catálogo Central de Documentos | **Data Emissão:** 26/05/2026 |

1. **História do Usuário – Catálogo Central de Documentos**

**Eu**, como gestor do SET - Sistema Estadual de Transferências,  
**Quero** acessar o catálogo central de documentos  
**Para** visualizar, cadastrar e gerenciar os documentos exigidos, diferenciando origens internas e externas (SIFI).

2. **Contextualização**

Esta funcionalidade centraliza todos os documentos que podem ser exigidos pelo sistema SET. Ela permite a separação clara entre documentos criados nativamente no SET e documentos oriundos de integrações (como o SIFI), garantindo rastreabilidade e organização através de códigos automáticos.

3. **Como demonstrar**  
* Acessar o sistema SET com um perfil que tenha acesso à funcionalidade “Manter Configuração”;  
* Navegar até o sub-menu "Documentos (Catálogo)";
* Preencher o filtro de pesquisa (Nome, Origem ou Situação) e clicar em “Consultar”;
* Verificar a listagem na grid com códigos automáticos e ícones de situação;
* Seguir os cenários de Critérios de Aceitação para validar inclusão e visualização.

4. **Critérios de Aceitação**   

**Cenário 1: Cadastrar Novo Documento Interno**

* O usuário deverá pressionar o botão “Cadastrar” na tela de consulta;
* O sistema apresenta um modal com o campo “Código” preenchido automaticamente (Ex: SET0004);
* O usuário deverá preencher “Documento” e “Descrição” e clicar em “Salvar”;
* O sistema deverá persistir o documento e exibi-lo na grid de consulta.

**Cenário 2: Visualizar Detalhes e Auditoria**

* O usuário deverá clicar no ícone de "Olho" (Verde) em um registro da grid;
* O sistema abrirá o modal em modo de leitura;
* O sistema deverá exibir obrigatoriamente a “Data de Cadastro” e o “Usuário Cadastrante”;
* O usuário poderá retornar à tela anterior através do botão “Fechar” ou clicando fora do modal.

**Cenário 3: Filtrar por Origem (Integração)**

* O usuário deverá selecionar a opção "SIFI" no filtro de "Origem";
* O usuário clica em "Consultar";
* O sistema deverá exibir apenas documentos que possuam códigos externos (Ex: SFIF0001).

5. **Protótipos**

O comportamento visual e interativo desta tela pode ser validado no link abaixo:
[Acessar Protótipo Funcional - Documentos](../../specs/001-hub-documentos/preview/index.html)

6. **Descrição dos Campos**

**Filtros (Tela de Consulta)**

| Informação | Obrigatório | Editável | Tipo | Tamanho | Orientação | Obs. |
| :--- | :---: | :---: | :---: | :---: | :--- | :--- |
| Nome | Não | Sim | Texto | N/A | Esquerda | Busca por parte do nome do documento. |
| Origem | Não | Sim | Combo | N/A | Esquerda | Opções: SET, SIFI. |
| Situação | Não | Sim | Combo | N/A | Esquerda | Opções: Ativo, Inativo. |

**Formulário (Modal de Cadastro/Visualização)**

| Informação | Obrigatório | Editável | Tipo | Tamanho | Orientação | Obs. |
| :--- | :---: | :---: | :---: | :---: | :--- | :--- |
| Código | Sim | Não | Texto | 7 | Centro | Gerado automaticamente (SET + 0000). |
| Documento | Sim | Sim | Texto | 255 | Esquerda | Nome descritivo do documento. |
| Descrição do Documento | Não | Sim | Texto | N/A | Esquerda | Detalhamento da finalidade. |
| Situação | Sim | Sim | Toggle | N/A | Centro | Switch (SIM/NÃO). |
| Data de Cadastro | Sim | Não | Data | N/A | Esquerda | Visível apenas em modo Visualizar. |
| Usuário Cadastrante | Sim | Não | Texto | N/A | Esquerda | Visível apenas em modo Visualizar. |

7. **Ações**

| Informação | Obrigatório | Editável | Tipo | Tamanho | Orientação | Observações |
| :---: | :---: | :---: | :---: | :---: | :--- | :--- |
| Consultar | N/A | N/A | Botão | N/A | Centro | Azul Médio. Executa a busca na base. |
| Cadastrar | N/A | N/A | Botão | N/A | Centro | Azul Escuro. Abre o modal de criação. |
| Exportar PDF | N/A | N/A | Ícone | N/A | Centro | Ícone SVG de PDF. |
| Exportar Excel | N/A | N/A | Ícone | N/A | Centro | Ícone SVG de Excel. |
| Visualizar | N/A | N/A | Ícone | 24px | Centro | Ícone Olho (Verde). Abre modo leitura. |
| Editar | N/A | N/A | Ícone | 24px | Centro | Ícone Lápis (Azul). Abre modo edição. |

8. **Regra de Negócios**

| Nº | Descrição |
| :---: | :---- |
| **RN001** | O código do documento deve ser sequencial e único para a origem SET, iniciando em SET0001. |
| **RN002** | Documentos com origem SIFI não permitem edição do Nome/Descrição através do SET (Read-only por integração). |
| **RN003** | A visualização de documentos deve sempre expor os campos de auditoria (Data e Usuário) para garantir a rastreabilidade. |
| **RN004** | A exportação para PDF/Excel deve respeitar os filtros aplicados na tela no momento do clique. |

9. **Histórico**

| Data | Versão | Descrição | Responsável |
| :--- | :--- | :--- | :--- |
| 26/05/2026 | 1.0 | Criação inicial baseada no protótipo SET.
