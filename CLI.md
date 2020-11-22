# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## CLI

> Command-line Interface Reference

---

* [AWS]()

---

### AWS

> AWS CLI References

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
