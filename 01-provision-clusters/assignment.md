---
slug: provision-clusters
id: pqdyvxl7dbco
type: challenge
title: Provision HCP Boundary and Vault clusters
teaser: Standup an HCP Boundary and Vault deployment ready for the lab
notes:
- type: text
  contents: First step! Deploy the HCP Boundary and HCP Vault clusters. Whilst we're waiting to kick things off, look at the next slide to see what we will be building
- type: image
  url: ../assets/initial-build.png  
tabs:
- title: Workstation
  type: terminal
  hostname: workstation
- title: Dev-Workstation
  type: terminal
  hostname: workstation
- title: AWS Console
  type: service
  hostname: cloud-client
  path: /
  port: 80
difficulty: basic
timelimit: 86400
---

👋 Getting started
===============

The first task is to deploy HCP Boundary and Vault clusters with Terraform.

Export your HCP credentials so Terraform can authenticate agaist the HashiCorp Cloud Platform:

```
export HCP_CLIENT_ID="..."
```

```
export HCP_CLIENT_SECRET="..."
```

In the Workstation terminal, move into the `hcp-deploy` directory `cd hcp-deploy` and execute
`terraform init` and then `terraform apply`. Type yes when prompted.

The deployment will take around 10 minutes. When you see Terraform return `Apply Complete!` in the terminal, hit the green next button in the bottom right hand corner.


