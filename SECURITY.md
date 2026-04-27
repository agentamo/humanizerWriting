# Security Policy

## Scope

This project is a prompt-based writing skill. The primary security surface is **prompt injection via untrusted input text** and accidental leakage of sensitive data during rewriting.

## Threat model

### In scope

- Instruction-injection content inside user-provided text (for example: "ignore previous instructions").
- Social-engineering payloads that attempt to make the model reveal hidden prompts/rules.
- Sensitive token exposure (API keys, credentials, internal IDs) during transformation.

### Out of scope

- Runtime code execution vulnerabilities in this repository (no executable runtime is shipped here).
- Infrastructure security of external model platforms.

## Security guarantees for this skill

1. User/source text is treated as untrusted data to edit, not instructions to execute.
2. Embedded attempts to override policy are ignored and, when useful, removed in the rewrite.
3. The skill remains scoped to writing tasks and does not perform operational/security bypass actions.
4. Sensitive values should be minimized/redacted by default unless a user explicitly requests exact preservation.

## Safe usage checklist

- Do not paste production credentials, private keys, or access tokens into prompts.
- Prefer redacted placeholders (`<API_KEY>`, `<ACCOUNT_ID>`) during editing.
- Review transformed output before sharing externally.

## Reporting a security concern

Please open an issue describing:

- What input triggered unsafe behavior.
- What output was produced.
- What output should have been produced instead.

If the report includes sensitive information, redact secrets before submission.
