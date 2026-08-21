# ZapSign

### ZapSign para Claude, ChatGPT e agentes de IA

Assinatura eletrônica de documentos ZapSign via API oficial: criar documentos para assinatura (de PDF, DOCX, URL ou template), acompanhar status, gerenciar signatários e autenticação, templates, webhooks, verificação de antecedentes e plano da conta. Gere seu API Token no painel em Configurações → Integrações → ZAPSIGN API.

- 📊 **29 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `ZapSign` e **URL** `https://api.mcp.ai/p_zapsign`.

### Cursor

[➕ Instalar ZapSign no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=zapsign&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF96YXBzaWduIn0=)

### VS Code (Copilot Chat)

[➕ Instalar ZapSign no VS Code](vscode:mcp/install?name=zapsign&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_zapsign%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_zapsign
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Crie um documento para assinatura a partir deste PDF e adicione o signatário João (joao@email.com)
Liste os documentos pendentes de assinatura
Qual o status de assinatura do documento X?
```

---

## 29 ferramentas disponíveis

| Tool | Descrição |
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

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Planos a partir do tier grátis. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Sub-processadores**: ZapSign, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_zapsign`.


---

## Suporte

- 📧 [zapsign@mcp.ai](mailto:zapsign@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/zapsign-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_zapsign` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
