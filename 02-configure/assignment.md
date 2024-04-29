---
slug: configure
id: m7m6sg3yptbu
type: challenge
title: Boundary Config
teaser: prereq
notes:
- type: text
  contents: TBC
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

1. 



