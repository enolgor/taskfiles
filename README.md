# Taskfiles

This is a bunch of common and useful taskfiles that I use in other projects.

## Usage

### ssm-crypto.yml

Encrypt/Decrypt with gpg your sensitive files, the passphrase is stored in ssm.

Dependencies: `docker`

```yml
version: '3'

includes:
  crypto:
    taskfile: https://raw.githubusercontent.com/enolgor/taskfiles/refs/heads/main/ssm-crypto.yml
    vars:
      ssm_passphrase_key: /keys/default # this is the ssm param key of the passphrase
      aws_profile: default # what profile to use from .aws/credentials
      aws_region: eu-west-1 # aws region
      files: # array of files to encrypt/decrypt
        - somefile.txt
```

Encrypt files: `task crypto:encrypt`

Decrypt files: `task crypto:decrypt`