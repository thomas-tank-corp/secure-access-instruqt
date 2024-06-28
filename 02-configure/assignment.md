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
- title: Code Editor
  type: service
  hostname: workstation
  port: 8443
- title: AWS Console
  type: service
  hostname: cloud-client
  path: /
  port: 80
- title: HCP
  type: browser
  hostname: hcp
difficulty: basic
timelimit: 7200
---

🛠️ Configure Boundary and Vault
===============

Now that we have deployed Boundary and Vault, we will now configure both using Terraform.

Move into the `hcpb-secure-access-instruqt` directory by issuing a

```
cd hcpb-secure-access-instruqt
```

Then execute `terraform init` then `terraform apply`

The deployment will take around 5 minutes. When you see Terraform return `Apply Complete!` in the terminal, hit the green next button in the bottom right hand corner.

This deployment will do the following things:

1. Configure a Boundary org scope and a project scope.
2. Create all the Host Catalogues, Host Sets and Hosts within Boundary.
3. Creates all the credential libraries for Vault and the Bounday native credential store.
4. Deploys a self-managed worker in AWS and authenticates with the HCPb control plane.
5. Configures the Vault DB secret engine and SSH secret engine.
6. Creates all requisite Vault policies.
7. Deploys an EC2 Amazon Linux target for application credential injection, utilising Vault.
8. Deploys an RDS instance for ephemeral, brokered credentials, utilising Vault.
9. Deploys a Windows VM for static brokered credentials, utilising Boundary's static credential store

Once the terraform apply is complete, click Next.

