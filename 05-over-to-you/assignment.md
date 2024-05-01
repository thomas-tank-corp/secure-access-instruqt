---
slug: over-to-you
id: cykviaolabfx
type: challenge
title: It's over to you!
teaser: Create an additional target and configure Boundary to securely connect to
  it
notes:
- type: text
  contents: Deploy an additional EC2 instance and use Boundary to securely connect
    to the target
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

It's all over to you now.
===============

Hopefully so far you have had a chance to navigate around Boundary via the UI, CLI and Desktop Client to understand the architecture and logical constructs. At this point it's time for you to do some work 🙂

In your code editor, you will see a file called `new-aws-ec2.tf`. If you uncomment the code and run a `terraform apply` it will spin up another Amazon Linux EC2 instance. It will run some `cloudinit` to trust Vault as the CA, ready for credential injection.....BUT, you don't have to go down this route if you choose not to. There are some different options of how you wish to secure the connectivity to this target....

Option 1 - Application Credential Injection
=========

If you navigate into the `partner-demo-org`, `partner-demo-project` and click `Credential Stores` on the left side of the admin UI. You will see two Credential Stores as discussed in the 'Let's connect to some targets!' task :

* `boundary-vault-credential-store`
* `boundary-credential-store`




