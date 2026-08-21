---
name: zapsign-mcp
description: Skill da REST API do ZapSign na MCP.AI: 29 endpoints em /api/zapsign. Assinatura eletrônica de documentos ZapSign via API oficial: criar documentos para assinatura (de PDF, DOCX, URL ou template), acompanhar status, gerenciar signatários e autenticação, templates, webhooks, verificação de antecedentes e plano da conta. Gere seu API Token no painel em Configurações → Integrações → ZAPSIGN API. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# ZapSign — REST API skill

Você tem acesso à **ZapSign** REST API na MCP.AI.

> Assinatura eletrônica de documentos ZapSign via API oficial: criar documentos para assinatura (de PDF, DOCX, URL ou template), acompanhar status, gerenciar signatários e autenticação, templates, webhooks, verificação de antecedentes e plano da conta. Gere seu API Token no painel em Configurações → Integrações → ZAPSIGN API.

## Base URL

```
https://api.mcp.ai/api/zapsign
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/zapsign/account/plan \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/zapsign/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (29)

#### `zapsign_account_plan`

Conta ZapSign (leitura). _(POST /api/zapsign/account/plan)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não | Página (1-based) da listagem paginada |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_account_users`

Conta ZapSign (leitura). _(POST /api/zapsign/account/users)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não | Página (1-based) da listagem paginada |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_account_write_create_user`

Gerenciar usuários da conta ZapSign. _(POST /api/zapsign/account/write/create/user)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `email` | string | Não | delete_user: email do usuário |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_account_write_delete_user`

Gerenciar usuários da conta ZapSign. _(POST /api/zapsign/account/write/delete/user)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `email` | string | Não | delete_user: email do usuário |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_checks_get`

Verificação de antecedentes no ZapSign (leitura). _(POST /api/zapsign/checks/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `check_id` | string | Sim | ID da verificação |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |
| `check_ids` | string[] | Não | Bulk mode: multiple values for check_id |

#### `zapsign_checks_write_create`

Criar verificação de antecedentes no ZapSign (consome créditos). _(POST /api/zapsign/checks/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_get`

Documentos de assinatura no ZapSign (leitura). _(POST /api/zapsign/documents/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | get / signer_log |
| `status` | string | Não | list: pending|signed|refused |
| `folder_path` | string | Não |  |
| `deleted` | boolean | Não |  |
| `signer_email` | string | Não |  |
| `created_from` | string | Não |  |
| `created_to` | string | Não |  |
| `sort_order` | string | Não |  (asc, desc) |
| `include_signers` | boolean | Não |  |
| `download_pdf` | boolean | Não | signer_log: baixar PDF |
| `page` | integer | Não | Página (1-based) da listagem paginada |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_list`

Documentos de assinatura no ZapSign (leitura). _(POST /api/zapsign/documents/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | get / signer_log |
| `status` | string | Não | list: pending|signed|refused |
| `folder_path` | string | Não |  |
| `deleted` | boolean | Não |  |
| `signer_email` | string | Não |  |
| `created_from` | string | Não |  |
| `created_to` | string | Não |  |
| `sort_order` | string | Não |  (asc, desc) |
| `include_signers` | boolean | Não |  |
| `download_pdf` | boolean | Não | signer_log: baixar PDF |
| `page` | integer | Não | Página (1-based) da listagem paginada |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_signer_log`

Documentos de assinatura no ZapSign (leitura). _(POST /api/zapsign/documents/signer/log)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | get / signer_log |
| `status` | string | Não | list: pending|signed|refused |
| `folder_path` | string | Não |  |
| `deleted` | boolean | Não |  |
| `signer_email` | string | Não |  |
| `created_from` | string | Não |  |
| `created_to` | string | Não |  |
| `sort_order` | string | Não |  (asc, desc) |
| `include_signers` | boolean | Não |  |
| `download_pdf` | boolean | Não | signer_log: baixar PDF |
| `page` | integer | Não | Página (1-based) da listagem paginada |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_write_add_extra_doc`

Criar/alterar documentos de assinatura no ZapSign. _(POST /api/zapsign/documents/write/add/extra/doc)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | update/delete/place_signatures/add_extra_doc |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_write_create`

Criar/alterar documentos de assinatura no ZapSign. _(POST /api/zapsign/documents/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | update/delete/place_signatures/add_extra_doc |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_write_create_from_template`

Criar/alterar documentos de assinatura no ZapSign. _(POST /api/zapsign/documents/write/create/from/template)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | update/delete/place_signatures/add_extra_doc |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_write_delete`

Criar/alterar documentos de assinatura no ZapSign. _(POST /api/zapsign/documents/write/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | update/delete/place_signatures/add_extra_doc |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_write_place_signatures`

Criar/alterar documentos de assinatura no ZapSign. _(POST /api/zapsign/documents/write/place/signatures)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | update/delete/place_signatures/add_extra_doc |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_write_refuse`

Criar/alterar documentos de assinatura no ZapSign. _(POST /api/zapsign/documents/write/refuse)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | update/delete/place_signatures/add_extra_doc |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_documents_write_update`

Criar/alterar documentos de assinatura no ZapSign. _(POST /api/zapsign/documents/write/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | update/delete/place_signatures/add_extra_doc |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_list_accounts`

Lista contas ZapSign vinculadas a este install — id e apelido. _(POST /api/zapsign/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_signers_get`

Signatários no ZapSign (leitura). _(POST /api/zapsign/signers/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `signer_token` | string | Sim | Token do signatário |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_signers_write_add`

Gerenciar signatários no ZapSign. _(POST /api/zapsign/signers/write/add)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | add |
| `signer_token` | string | Não | update/remove |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_signers_write_remove`

Gerenciar signatários no ZapSign. _(POST /api/zapsign/signers/write/remove)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | add |
| `signer_token` | string | Não | update/remove |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_signers_write_sign`

Gerenciar signatários no ZapSign. _(POST /api/zapsign/signers/write/sign)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | add |
| `signer_token` | string | Não | update/remove |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_signers_write_update`

Gerenciar signatários no ZapSign. _(POST /api/zapsign/signers/write/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `doc_token` | string | Não | add |
| `signer_token` | string | Não | update/remove |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_templates_get`

Templates (modelos DOCX) no ZapSign (leitura). _(POST /api/zapsign/templates/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `template_token` | string | Não | get |
| `page` | integer | Não | Página (1-based) da listagem paginada |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_templates_list`

Templates (modelos DOCX) no ZapSign (leitura). _(POST /api/zapsign/templates/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `template_token` | string | Não | get |
| `page` | integer | Não | Página (1-based) da listagem paginada |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_templates_write_create`

Gerenciar templates no ZapSign. _(POST /api/zapsign/templates/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `template_token` | string | Não | update/delete |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_templates_write_delete`

Gerenciar templates no ZapSign. _(POST /api/zapsign/templates/write/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `template_token` | string | Não | update/delete |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_templates_write_update`

Gerenciar templates no ZapSign. _(POST /api/zapsign/templates/write/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `template_token` | string | Não | update/delete |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |

#### `zapsign_webhooks_write_create`

Gerenciar webhooks no ZapSign (não há endpoint de listagem na API). _(POST /api/zapsign/webhooks/write/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Não | delete: id do webhook |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `zapsign_webhooks_write_delete`

Gerenciar webhooks no ZapSign (não há endpoint de listagem na API). _(POST /api/zapsign/webhooks/write/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Não | delete: id do webhook |
| `data` | object | Não | Corpo da requisição (campos conforme a doc oficial ZapSign do recurso/ação) |
| `account` | string | Não | Opcional quando há várias contas ZapSign vinculadas a este install (id, label ou parcial). Use zapsign_list_accounts pra ver as opções; omita se só houver uma. |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_zapsign` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
