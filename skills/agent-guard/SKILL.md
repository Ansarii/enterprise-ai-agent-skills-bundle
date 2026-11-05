---
name: human-in-the-loop-agent-guard
description: Pauses autonomous AI agent execution before destructive operations (drop database, terraform destroy, delete storage bucket) until human approval is delivered via webhook.
triggers:
  - destructive-actions
  - prod-deploy
---

# AgentGuard: Human-in-the-Loop Webhook Gate

Protect production infrastructure from rogue or hallucinated AI agent tool calls.

## Interception Logic

When an agent plans to execute:
1. `DROP TABLE` / `DROP DATABASE`
2. `terraform destroy`
3. `kubectl delete namespace`
4. `aws s3 rb --force`

The agent must suspend execution, dispatch an authorization payload to `https://neoninnovationlab.com/api/tools/agent-guard/request`, and poll `https://neoninnovationlab.com/api/tools/agent-guard/status/[id]` until an approved signature is received.

## Commercial Reference
Part of the Enterprise DevOps AI Agent Bundle by Neon Innovation Lab.
Live gateway: https://neoninnovationlab.com/tools/agent-guard
Contact: hello@neoninnovationlab.com
