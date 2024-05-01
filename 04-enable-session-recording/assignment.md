---
slug: enable-session-recording
id: y9w4g0sywbi3
type: challenge
title: Time to enable SSH session recording
teaser: Organisations need to have the accountability and traceability into what is
  performed on targets within their estate. We will enable session recording and try
  this out!
notes:
- type: text
  contents: Now we can access our EC2 Amazon Linux target, we need to introduce some
    auditing capabilities using Boundary's SSH session recording. Let's enable that
    and then re-connect back to the target to see how session recording looks.
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
difficulty: basic
timelimit: 7200
---

Enabling Session Recording
===============

The quickest way to enable session recording is to open up the `s3-bucket.tf` and `hcpb-storage-bucket.tf` in the VS Code editor and uncomment out all of the code in each file. This will create the AWS S3 bucket that is used to hold the Boundary Session Recording (BSR) data. It will also create the Boundary storage bucket that is associated with the S3 bucket in AWS.

Secondly, open up the `boundary-vm-target-config.tf` file and uncomment out the two lines as shown below:

```
resource "boundary_target" "aws" {
  type                     = "ssh"
  name                     = "aws-ec2"
  description              = "AWS EC2 Target"
  egress_worker_filter     = " \"self-managed-aws-worker\" in \"/tags/type\" "
  scope_id                 = boundary_scope.project.id
  session_connection_limit = -1
  default_port             = 22
  host_source_ids = [
    boundary_host_set_plugin.aws_dev.id,
  ]
  # enable_session_recording                   = true
  # storage_bucket_id                          = boundary_storage_bucket.boundary_storage_bucket.id
  injected_application_credential_source_ids = [boundary_credential_library_vault_ssh_certificate.vault_ssh_cert.id]
}
```

Doing this will enable session recording on the EC2 target device and associate the target to the Boundary storage bucket. Enabling this target for session recording could be done via the Admin UI or the CLI if you'd prefer to get more familiar with the UI/CLI.


