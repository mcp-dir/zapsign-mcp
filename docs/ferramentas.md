# Ferramentas

ZapSign expõe 29 ferramentas.

### 1. `zapsign_list_accounts`
**Input**: `account` (opcional)

Lista contas ZapSign vinculadas a este install — id e apelido.

### 2. `zapsign_documents_list`
**Input**: `doc_token` (opcional), `status` (opcional), `folder_path` (opcional), `deleted` (opcional), `signer_email` (opcional), `created_from` (opcional), `created_to` (opcional), `sort_order` (opcional), `include_signers` (opcional), `download_pdf` (opcional), `page` (opcional), `account` (opcional)

Documentos de assinatura no ZapSign (leitura).

### 3. `zapsign_documents_get`
**Input**: `doc_token` (opcional), `status` (opcional), `folder_path` (opcional), `deleted` (opcional), `signer_email` (opcional), `created_from` (opcional), `created_to` (opcional), `sort_order` (opcional), `include_signers` (opcional), `download_pdf` (opcional), `page` (opcional), `account` (opcional)

Documentos de assinatura no ZapSign (leitura).

### 4. `zapsign_documents_signer_log`
**Input**: `doc_token` (opcional), `status` (opcional), `folder_path` (opcional), `deleted` (opcional), `signer_email` (opcional), `created_from` (opcional), `created_to` (opcional), `sort_order` (opcional), `include_signers` (opcional), `download_pdf` (opcional), `page` (opcional), `account` (opcional)

Documentos de assinatura no ZapSign (leitura).

### 5. `zapsign_documents_write_create`
**Input**: `doc_token` (opcional), `data` (opcional), `account` (opcional)

Criar/alterar documentos de assinatura no ZapSign.

### 6. `zapsign_documents_write_create_from_template`
**Input**: `doc_token` (opcional), `data` (opcional), `account` (opcional)

Criar/alterar documentos de assinatura no ZapSign.

### 7. `zapsign_documents_write_update`
**Input**: `doc_token` (opcional), `data` (opcional), `account` (opcional)

Criar/alterar documentos de assinatura no ZapSign.

### 8. `zapsign_documents_write_delete`
**Input**: `doc_token` (opcional), `data` (opcional), `account` (opcional)

Criar/alterar documentos de assinatura no ZapSign.

### 9. `zapsign_documents_write_refuse`
**Input**: `doc_token` (opcional), `data` (opcional), `account` (opcional)

Criar/alterar documentos de assinatura no ZapSign.

### 10. `zapsign_documents_write_place_signatures`
**Input**: `doc_token` (opcional), `data` (opcional), `account` (opcional)

Criar/alterar documentos de assinatura no ZapSign.

### 11. `zapsign_documents_write_add_extra_doc`
**Input**: `doc_token` (opcional), `data` (opcional), `account` (opcional)

Criar/alterar documentos de assinatura no ZapSign.

### 12. `zapsign_signers_get`
**Input**: `signer_token`, `account` (opcional)

Signatários no ZapSign (leitura).

### 13. `zapsign_signers_write_add`
**Input**: `doc_token` (opcional), `signer_token` (opcional), `data` (opcional), `account` (opcional)

Gerenciar signatários no ZapSign.

### 14. `zapsign_signers_write_update`
**Input**: `doc_token` (opcional), `signer_token` (opcional), `data` (opcional), `account` (opcional)

Gerenciar signatários no ZapSign.

### 15. `zapsign_signers_write_remove`
**Input**: `doc_token` (opcional), `signer_token` (opcional), `data` (opcional), `account` (opcional)

Gerenciar signatários no ZapSign.

### 16. `zapsign_signers_write_sign`
**Input**: `doc_token` (opcional), `signer_token` (opcional), `data` (opcional), `account` (opcional)

Gerenciar signatários no ZapSign.

### 17. `zapsign_templates_list`
**Input**: `template_token` (opcional), `page` (opcional), `account` (opcional)

Templates (modelos DOCX) no ZapSign (leitura).

### 18. `zapsign_templates_get`
**Input**: `template_token` (opcional), `page` (opcional), `account` (opcional)

Templates (modelos DOCX) no ZapSign (leitura).

### 19. `zapsign_templates_write_create`
**Input**: `template_token` (opcional), `data` (opcional), `account` (opcional)

Gerenciar templates no ZapSign.

### 20. `zapsign_templates_write_update`
**Input**: `template_token` (opcional), `data` (opcional), `account` (opcional)

Gerenciar templates no ZapSign.

### 21. `zapsign_templates_write_delete`
**Input**: `template_token` (opcional), `data` (opcional), `account` (opcional)

Gerenciar templates no ZapSign.

### 22. `zapsign_webhooks_write_create`
**Input**: `id` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Gerenciar webhooks no ZapSign (não há endpoint de listagem na API).

### 23. `zapsign_webhooks_write_delete`
**Input**: `id` (opcional), `data` (opcional), `account` (opcional), `ids` (opcional)

Gerenciar webhooks no ZapSign (não há endpoint de listagem na API).

### 24. `zapsign_checks_get`
**Input**: `check_id`, `account` (opcional), `check_ids` (opcional)

Verificação de antecedentes no ZapSign (leitura).

### 25. `zapsign_checks_write_create`
**Input**: `data` (opcional), `account` (opcional)

Criar verificação de antecedentes no ZapSign (consome créditos).

### 26. `zapsign_account_plan`
**Input**: `page` (opcional), `account` (opcional)

Conta ZapSign (leitura). Ações: plan (info do plano: créditos, status, período); users (page — lista usuários da conta, 25/página). [Flattened action: plan]

### 27. `zapsign_account_users`
**Input**: `page` (opcional), `account` (opcional)

Conta ZapSign (leitura). Ações: plan (info do plano: créditos, status, período); users (page — lista usuários da conta, 25/página). [Flattened action: users]

### 28. `zapsign_account_write_create_user`
**Input**: `email` (opcional), `data` (opcional), `account` (opcional)

Gerenciar usuários da conta ZapSign.

### 29. `zapsign_account_write_delete_user`
**Input**: `email` (opcional), `data` (opcional), `account` (opcional)

Gerenciar usuários da conta ZapSign.

## Prompts de exemplo

```
Crie um documento para assinatura a partir deste PDF e adicione o signatário João (joao@email.com)
Liste os documentos pendentes de assinatura
Qual o status de assinatura do documento X?
```
