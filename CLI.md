# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## CLI

> Command-line Interface Reference

---

* [AWS]()
* [Hardhat]()
* [Nuxt.js]()

---

### AWS

> AWS CLI References

[Documentation](https://docs.aws.amazon.com/cli/latest/reference/)

__Usage__: `$ aws [options] <command> <subcommand> [parameters]`

__Options__

| Command | Type | Description |
|:--------|:----:|:------------|
| `--debug` | boolean | Turn on debug logging |
| `--endpoint-url` | string | Override default URL with input |
| `--no-verify-ssl | boolean | Over AWS CLI default verification of SSL certificate |
| `--no-paginate` | boolean | Disable automatic pagination |
| `--output` | string | Output format style (`json`, `text`, `table`) |
| `--query` | string | JMESPath query for filtering responses |
| `--profile` | string | AWS profile credentials to use for command |
| `--region` | string | AWS region to use for command |
| `--color` | string | Color output (`on`, `off`, `auto`) |
| `--no-sign-request` | boolean | Do not sign requests |
| `--ca-bundle` | string | CA certificate bundle to use when verifying SSL certificates |
| `--cli-read-timeout` | integer | Max socket read time in seconds |
| `--cli-connect-timeout | integer | Max socket connect time in seconds |

__`route53domains`__

__Command__: `aws route53domains <command> [options...]`

```bash
# Check domain name availability
$ aws route53domains check-domain-availability --domain-name <domain>
```

__`s3`__

__Command__: `aws s3 <command> [options...]

* single-file commands: `cp`, `mv`, `rm`
* directory commands: `sync`, `mb`, `rb`, `ls`
* website commands: `website`
* auth commands: `presign`
* __Matches__
  * `*`: match everything
  * `?`: match any single character
  * `[sequence]`: match any character in sequence
  * `[!sequence]`: match any character not in sequence
* flag: `--recursive` - commands are single file without this flag

```bash
# 
```

---

### Hardhat

> Ethereum Runtime Environment Framework

[Documentation](https://hardhat.org/)

__Install__: `$ npm install --save-dev hardhat`

__Usage__: `$ npx hardhat [--network] <command> [options...]`

```bash
# Initialize hardhat project config
$ npx hardhat

# Compile contracts
$ npx hardhat compile

# Reset artifacts and cache
$ npx hardhat clean

# Start node environment
$ npx hardhat node

# Start console environment
$ npx hardhat console

# Run script automation
$ npx hardhat run script/_.js
```

---

### Nuxt.js

> Nuxt.js Frontend Framework Commands

[Documentation](https://nuxtjs.org/)

```bash
# Create Nuxt.js project
$ npx create-nuxt-app <app-name>
```

---
