# AWS CLI

[![Build Status](https://drone.osshelp.ru/api/badges/ansible/awscli/status.svg)](https://drone.osshelp.ru/ansible/awscli)

## Description

Simple role for Ansible, which installs and configures AWS CLI.

The role **overwrites** configuration files:

- `/root/.aws/config`
- `/root/.aws/credentials`

## Usage example

### Default example (with aws credentials, python3 and s3 support)

``` yaml
    - role: awscli
      awscli_custom_pip_packages:
        - awscli-plugin-endpoint
      awscli_plugins_params:
        endpoint: awscli_plugin_endpoint
      awscli_profiles:
        - name: default
          secret_access_key: "some_default_secret_access_key"
          access_key_id: "some_default_access_key_id"
        - name: custom
          region: local
          output: json
          secret_access_key: "some_custom_secret_access_key"
          access_key_id: "some_custom_access_key_id"
          s3:
            signature_version: s3v4
            endpoint_url: https://domain.tld/
            max_concurrent_requests: 20
            max_bandwidth: 50MB/s
```

### Without configs generation

``` yaml
    - role: awscli
      awscli_skip_config: true
```

## Available parameters

| Param | Default | Description |
| -------- | -------- | -------- |
| `awscli_python_version`| `3` | Python version to use. |
| `awscli_custom_pip_packages` | `[]` | List of additional pip packages to install. |
| `awscli_plugins_params`| `[]` | List of custom plugin params (`[plugins]` section will be generated for them in main cfg). |
| `awscli_default_output_format`| `json` | Output format to use as default (if no overrides in `awscli_profiles`). |
| `awscli_default_region`| `local` | Region to use as default (if no overrides in `awscli_profiles`). |
| `awscli_profiles`| see [defaults](defaults/main.yml) | Param for describing needed profiles. |

## FAQ

...

## Useful links

- [Documentation](https://aws.amazon.com/ru/cli/)
- [Python Package](https://pypi.org/project/awscli/)

## TODO

...

## License

GPL3

## Author

OSSHelp Team, see <https://oss.help>
