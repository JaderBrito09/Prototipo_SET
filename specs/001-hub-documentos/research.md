# Research Notes: Arquitetura de Documentos e Anexos

## Unknowns Identified from Technical Context
*(No explicit unknowns, but architectural patterns need defining for the Autocomplete and Pagination).*

## Architecture & Data Loading Strategy

### Decision: Server-Side Filtering and Pagination for Master Lists
**Rationale:** Since the "Documentos" sub-menu centralizes all documents (both native to SET and imported from integrations like SIFI), the volume of data can grow significantly. Client-side filtering is not scalable. We will use standard server-side pagination (offset/limit) and query parameters for the filters (Nome, Origem, Situação).
**Alternatives considered:**
- *Client-side filtering:* Rejected due to potential performance issues with large integration catalogs.

### Decision: Debounced Async Autocomplete for "Editar Anexo"
**Rationale:** In the "Editar Anexo" screen, the user must link a master document to the grid. Rendering a dropdown with thousands of documents is bad UX and performance. We will implement an Async Autocomplete component that fetches results from the backend only after the user types 3 or more characters (with a 300ms debounce).
**Alternatives considered:**
- *Modal with full search grid:* Rejected as it introduces the very friction the PRD seeks to eliminate. The inline autocomplete keeps the user focused on the parameterization table.

### Decision: Read-Only handling for Integrated Documents
**Rationale:** To satisfy Principle VI (Integration Visibility) and RN003 (Desacoplamento de Integração), the frontend must gracefully handle documents originating from external systems. If `Origem == 'INTEGRACAO'`, the "Edit" action in the Documentos grid might only allow editing the local description, but lock the name to prevent mismatch with the external system. This requires the API to return permission metadata or explicit origin flags.