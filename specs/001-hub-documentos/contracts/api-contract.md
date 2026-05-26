# API Contract: Módulo Documentos e Anexos

## Endpoints de Catálogo (Sub-menu: Documentos)

### 1. Listar Documentos (Com Paginação e Filtros)
**GET** `/api/v1/documentos-mestre?page=1&limit=20&origem=INTEGRACAO&nome=certidao`

**Response (200 OK):**
```json
{
  "data": [
    {
      "id": 1,
      "codigo": "SFI-0992",
      "nome": "Certidão Negativa de Débitos",
      "origem": "INTEGRACAO",
      "situacao": true,
      "data_cadastro": "2026-05-26T14:30:00Z",
      "usuario_cadastrante": "JADER BRITO"
    }
  ],
  "meta": { "total": 1, "page": 1, "last_page": 1 }
}
```

## Endpoints de Locais (Sub-menu: Anexos)

### 2. Listar Locais de Upload
**GET** `/api/v1/locais-anexo?funcionalidade=Cadastramento`

**Response (200 OK):**
```json
{
  "data": [
    {
      "id": 10,
      "funcionalidade": "Cadastramento",
      "local_nome": "Documento dos Diretores",
      "qtd_documentos_vinculados": 3,
      "situacao": true
    }
  ],
  "meta": { "total": 1, "page": 1, "last_page": 1 }
}
```

## Endpoints de Parametrização (Tela: Editar Anexo)

### 3. Autocomplete de Documentos Mestre
**GET** `/api/v1/documentos-mestre/autocomplete?q=Ata`

**Response (200 OK):**
```json
[
  { "id": 5, "nome": "Ata de Posse" },
  { "id": 12, "nome": "Ata de Reunião do Conselho" }
]
```

### 4. Obter Documentos de uma Grid Específica
**GET** `/api/v1/locais-anexo/10/parametrizacoes`

**Response (200 OK):**
```json
[
  {
    "parametrizacao_id": 1001,
    "documento_id": 5,
    "nome_documento": "Ata de Posse",
    "ativo": true,
    "obrigatorio": true,
    "tipo_pessoa": "JURIDICA",
    "grupo_documento": "INSTITUCIONAL"
  }
]
```

### 5. Atualizar Regras (Auto-save na Grid)
**PATCH** `/api/v1/parametrizacoes/1001`

**Request Body:**
```json
{
  "obrigatorio": false,
  "tipo_pessoa": "AMBAS"
}
```