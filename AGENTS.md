# Agent instructions

Guidance for AI agents working in this Ansible role repository.

## Ansible output safety

Ensure secrets (passwords, vault ciphertext, tokens, private keys) never appear in Ansible task output, assertion failures, or debug messages.

- Loop over sanitized data (e.g. usernames and routes only) instead of full user structures when a task can fail and dump loop `item` values.
- Use `no_log: true` on tasks that read or write secrets.
- In `fail_msg` and `loop_control.label`, reference only non-sensitive identifiers; never dump entire loop items that may contain secrets.
