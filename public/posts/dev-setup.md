---
title: "DEveloper Environment Setup"
date: 2019-09-20T14:12:19-04:00
draft: false
categories:
tags:
keywords:
---
# ApplyBoardCloud ☁️

## Developer Environment Setup

### Setup your AWS Account and Web Console access
1. Request an AWS Developer Account by contacting: jason.deland@applyboard.com
2. Follow the instructions in the *Welcome to Amason Web Services email* you receive to setup your account
  - When complete you should be able to login into the AWS Dev Account via this link https://649614366484.signin.aws.amazon.com/console
3. Enable MFA following the AWS Guide: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable_virtual.html
  - Note you need an Virtual MFA Device on your phone. More details are available at: 
    - https://aws.amazon.com/iam/details/mfa/
    - https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html

### Configure your environment to access AWS via CLI
This section will enable you to use the AWS CLI and pull Docker Images using ECR
1. Please sync this repo to you system
  ```bash
  git clone git@github.com:ApplyBoard/abc.git
  ```
2. Run the Makefile dependency command
  - This will ensure you have the correct binaries needed (aws, python, docker)
  - Note the Make file will install this binaries via brew on MacOS and apt on Linux
  ```bash
  cd abc
  make help
  make deps
  ```
3. Configure your AWS CLI with an Access Key
4. Login to the AWS Account above and open the IAM Services page (Services Drop Down menu -> Security, Identity & Complaince)
5. Open the Users page and select your User Name (The same as your did for setting up your MFA information)
6. Select the Security credentials tab and click the *Create access key* button
    - **NOTE:** You need to store the Access key ID and Secret Access Key in LastPass just like your ApplyBoard Google Account. This is you literal **key** to use the AWS CLI and AWS Services within the ApplyBoard Development AWS Account.

### Verify that your AWS CLI access is working correctly
1. Run the AWS command below to get your account info
```bash
aws sts get-caller-identity
{
    "Account": "649614366484",
    "UserId": "AIDAZOQAIS4KHYBHKDK27",
    "Arn": "arn:aws:iam::649614366484:user/jason.deland@applyboard.com"                                   
}
```
