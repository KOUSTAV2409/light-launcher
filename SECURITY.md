# Security

## API keys

Light never distributes OpenAI (or other) API keys.

| Location | Used? | Shared / committed? |
|----------|-------|---------------------|
| Git repository | No | Must stay free of secrets |
| `~/.config/light/configuration.json` | No keys stored | Local only; keys stripped on save |
| `~/.config/light/secrets.json` | Yes (per user) | Local only; `0600` |
| `OPENAI_API_KEY` env var | Yes (per user) | Shell session only |

Each person who runs Light must supply **their own** key if they enable OpenAI answers.

## Reporting a vulnerability

If you find a security issue (especially key leakage, unsafe shell execution, or path traversal), please open a private report to the maintainer via GitHub Security Advisories on this repository, or email the address on the maintainer’s GitHub profile. Do not post live secrets in public issues.

## Rotating a leaked key

If a key was ever pasted into a commit, chat, or screenshot:

1. Revoke/rotate it in the OpenAI dashboard immediately
2. Put the new key only in `~/.config/light/secrets.json` or your environment
3. Confirm `git log -p` / GitHub search show no live key material
