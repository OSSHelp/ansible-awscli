# AWS CLI

[![Build Status](https://drone.osshelp.ru/api/badges/ansible/awscli/status.svg)](https://drone.osshelp.ru/ansible/awscli)

## Description

Simple role for Ansible, which installs AWS CLI.

The role **overwrites** configuration files:

- /root/.aws/config
- /root/.aws/credentials

## Deploy examples

### Default example (with aws credentials, python3)

``` yaml
- role: awscli
  region: eu-west-2
  aws_key: "aws_secret_access_key here"
  aws_id: "aws_access_key_id here"
```

### Without awscli config generation

``` yaml
- role: awscli
  skip_config: true
```

### Use Python2 for awscli

``` yaml
- role: awscli
  python_version: 2
  ...
```

## Links

[Documentation](https://aws.amazon.com/ru/cli/)
[Python Package](https://pypi.org/project/awscli/)
