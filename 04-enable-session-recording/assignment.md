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

The quick way to enable session recording is to open up the `s3-bucket.tf` and `hcpb-storage-bucket.tf` and uncomment out all of the code in each file. This will create the AWS S3 bucket that is used to hold the Boundary Session Recording (BSR) data. It will also create the Boundary storage bucket that is associated with the S3 bucket


