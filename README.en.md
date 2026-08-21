# ZapSign

### ZapSign for Claude, ChatGPT and AI agents

ZapSign electronic document signing via the official API: create documents for signature (from PDF, DOCX, URL or template), track status, manage signers and authentication, templates, webhooks, background checks and account plan. Generate your API Token in the dashboard under Settings → Integrations → ZAPSIGN API.

- 📊 **29 tools**
- ✏️ **Read and write**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `ZapSign`, URL `https://api.mcp.ai/p_zapsign`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=zapsign&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF96YXBzaWduIn0=)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=zapsign&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_zapsign%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_zapsign
```

---

## 29 tools

| Tool | Description |
|---|---|
| `zapsign_list_accounts` | Lista contas ZapSign vinculadas a este install — id e apelido. |
| `zapsign_documents_list` | Documentos de assinatura no ZapSign (leitura). |
| `zapsign_documents_get` | Documentos de assinatura no ZapSign (leitura). |
| `zapsign_documents_signer_log` | Documentos de assinatura no ZapSign (leitura). |
| `zapsign_documents_write_create` | Criar/alterar documentos de assinatura no ZapSign. |
| `zapsign_documents_write_create_from_template` | Criar/alterar documentos de assinatura no ZapSign. |
| `zapsign_documents_write_update` | Criar/alterar documentos de assinatura no ZapSign. |
| `zapsign_documents_write_delete` | Criar/alterar documentos de assinatura no ZapSign. |
| `zapsign_documents_write_refuse` | Criar/alterar documentos de assinatura no ZapSign. |
| `zapsign_documents_write_place_signatures` | Criar/alterar documentos de assinatura no ZapSign. |
| `zapsign_documents_write_add_extra_doc` | Criar/alterar documentos de assinatura no ZapSign. |
| `zapsign_signers_get` | Signatários no ZapSign (leitura). |
| `zapsign_signers_write_add` | Gerenciar signatários no ZapSign. |
| `zapsign_signers_write_update` | Gerenciar signatários no ZapSign. |
| `zapsign_signers_write_remove` | Gerenciar signatários no ZapSign. |
| `zapsign_signers_write_sign` | Gerenciar signatários no ZapSign. |
| `zapsign_templates_list` | Templates (modelos DOCX) no ZapSign (leitura). |
| `zapsign_templates_get` | Templates (modelos DOCX) no ZapSign (leitura). |
| `zapsign_templates_write_create` | Gerenciar templates no ZapSign. |
| `zapsign_templates_write_update` | Gerenciar templates no ZapSign. |
| `zapsign_templates_write_delete` | Gerenciar templates no ZapSign. |
| `zapsign_webhooks_write_create` | Gerenciar webhooks no ZapSign (não há endpoint de listagem na API). |
| `zapsign_webhooks_write_delete` | Gerenciar webhooks no ZapSign (não há endpoint de listagem na API). |
| `zapsign_checks_get` | Verificação de antecedentes no ZapSign (leitura). |
| `zapsign_checks_write_create` | Criar verificação de antecedentes no ZapSign (consome créditos). |
| `zapsign_account_plan` | Conta ZapSign (leitura). Ações: plan (info do plano: créditos, status, período); users (page — lista usuários da conta, 25/página). [Flattened action: plan] |
| `zapsign_account_users` | Conta ZapSign (leitura). Ações: plan (info do plano: créditos, status, período); users (page — lista usuários da conta, 25/página). [Flattened action: users] |
| `zapsign_account_write_create_user` | Gerenciar usuários da conta ZapSign. |
| `zapsign_account_write_delete_user` | Gerenciar usuários da conta ZapSign. |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_zapsign` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
