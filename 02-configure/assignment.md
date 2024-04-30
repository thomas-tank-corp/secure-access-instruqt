---
slug: configure
id: m7m6sg3yptbu
type: challenge
title: Boundary and Vault Config
teaser: Logically configure both Boundary and Vault, standup a self-managed worker
  and deploy some targets!
notes:
- type: text
  contents: Lets get Boundary and Vault configured!
tabs:
- title: Workstation
  type: terminal
  hostname: workstation
- title: AWS Console
  type: service
  hostname: cloud-client
  path: /
  port: 80
difficulty: basic
timelimit: 7200
---

Configure Boundary and Vault
===============

Now that you have deployed Boundary and Vault, we will now configure using Terraform.

Move in into the `hcpb-secure-access` directory and execute `terrraform init` then `terraform apply`

The deployment will take around 5 minutes. When you see Terraform return `Apply Complete!` in the terminal, hit the green next button in the bottom right hand corner.

This deployment will do the following things:

1. Configure a Boundary org scope and a project scope.
2.



