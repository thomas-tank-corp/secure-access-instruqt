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
- title: Editor
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

🫵 It's all over to you now.
===============

Hopefully up to this point you have had a chance to navigate around Boundary via the UI, CLI and Desktop Client, to understand the architecture and logical constructs. At this point it's time for you to do some work 🙂

In your code editor, you will see a file called `new-aws-ec2.tf`. What is contained within this file is a basic EC2 instance that gets deployed into your existing environment. We use some `cloudinit` configuration, which configures the instance to trust Vault as the CA and adds the Public Key from Vault onto the EC2 instance, so you can utilise application credential injection to securely access it.

Uncomment the code and back in the termainal change directory to the `hcpb-secure-access-instruqt` and run a `terraform apply`, which will spin up this Amazon Linux EC2 instance. Now you just have to configure Boundary to enable secure access to the target....

🏗️ Logical Architecture....recap.
=========

I think it's useful at this point to see logically how we have our Boundary deployment (for brevity this diagram does not include the RDS database)

![boundary-logical-deployment](../assets/boundary-logical-arch.png)

As you can see we have the Dynamic Host Catalogue for the `aws-ec2` and `aws-windows` VMs which are automatically pulled into Boundary to allow end-users to connect to them. We can see that both of these targets utilise different credential stores; `aws-ec2` uses the integration with Vault to provide those dynamic, ephemeral, just-in-time credentials, and `aws-windows` uses the native credential store in Boundary to access to some static username and password credentials.

You can see that above the `dynamic host catalogue: aws` catalogue, the `host catalogue`, `host set`, `host` and target all have a `?`. This is what you will now be creating to facilitate connectivity to the `new-aws-ec2` resource you have just created.

In terms of how you would like to create these logical components, it's down to you. We have the CLI, API or the UI as viable options. Personally the UI provides a little more clarity as it's visual, and you can hopefully understand a litter easier what is going on and how the logical constructs are pieced together.

If you have time and you're feeling adventurous, you can always create everything in the UI first and then try it on the CLI and/or API, which will give you some more familiarity with the Boundary command line and API.

🕵️‍♂️ Tip 1 - Host Catalogues, Host Sets & Hosts
=========

It is worth starting out by creating the host catalogue first, then the host set and then the host.

🕵️‍♂️ Tip 2 - Targets
=========

To create the target, we need the Type to be SSH. Aside from that we need to select the Egress worker filter radio button and enter the following 'Filter':

```
"self-managed-worker" in "/tags/type"
```
This ensures that our new target uses our self-managed worker to faciliate connectivity.

Now you can click Save.

🕵️‍♂️ Tip 3 - Injected Application Credentials
=========

If you have used the previous tip, when you click save you will be taken to the main Target configuration.

If you didn't use the previous tip, click on Targets and then onto the Injected Application Credentials tab.

When you select 'Add Injected Application Credentials', make sure you select the write credential source (you should be able to work out which one you need 🙂)


🪜 Next steps
===========

After you have successfully gained access to the target with your new configuration, give yourself a big pat on the back! Well done 💪

You have reached the end of the track, but there is more you can do and explore with Boundary if you're feeling inspired!

For a list of additional tutorials you could try using your Boundary deployment, head over to https://developer.hashicorp.com/boundary/tutorials and enjoy pushing the 'Boundary-s' of your Boundary knowledge 😎


🧹 Clean up
============

All that's left to do now is clean up the environment!

Simply copy and paste the command below and then you can click next to finish. The check script looks for `CONFIRM_CLEANUP` to ensure you don't accidentally delete the environment.

```
export=CONFIRM_CLEANUP
```