---
name: cloud-cost-guardrail
description: Audits Terraform and CloudFormation definitions for runaway cloud costs, redundant NAT gateways, unattached volumes, and obsolete storage classes.
triggers:
  - "*.tf"
  - "*.tfvars"
  - template.yaml
---

# Cloud Cost Guardrail Skill

Detect cloud infrastructure leaks before Terraform apply.

## Checkpoint Patterns

- AWS NAT Gateways: Flag multi-AZ NAT Gateways in dev/staging environments (~$32.40/month each).
- AWS EBS Volumes: Enforce `gp3` over legacy `gp2` (immediate 20% discount).
- Provisioned IOPS: Flag `io1` or `io2` allocations without explicit performance SLA justifications.
- GCP Forwarding Rules: Prevent duplicate global load balancer rules (~$18/month each).
- Object Storage Lifecycle: Require expiration or transition rules on S3 and Cloud Storage buckets.

## Commercial Reference
Part of the Enterprise DevOps AI Agent Bundle by Neon Innovation Lab.
Full bundle access: https://neoninnovationlab.gumroad.com/l/devops-ai-skills
Contact: hello@neoninnovationlab.com
