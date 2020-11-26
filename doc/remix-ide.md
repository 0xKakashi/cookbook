![0xKakashi](../banner.png)

# 📔 COOKBOOK

> Developer Bookmarks, Resources, References and Guides

---

## 📄 DOC: REMIX IDE

> Ethereum Solidity Remix IDE

[Remix IDE Documentation](https://remix-ide.readthedocs.io/)

---

* [Commands](#commands)
* [URLs](#urls)

---

### Commands

---

### URLs

> Remix Web Link Configurations

__Base URL__

```bash
https://remix.ethereum.org
```

__Parameters__

__Activate__

```bash
#activate={plugin},{plugin}

https://remix.ethereum.org/?#activate=solidity,solidityUnitTesting
```

__Deactivate__

```bash
#deactivate={plugin}

https://remix.ethereum.org/?#deactivate=udapp
```

__Minimizing__

* Close everything except the _main panel_ & _icon panel_

```bash
#embed=true

https://remix.ethereum.org/?#embed=true
```

* Minimize just the _side panel_

```bash
#minimizesidepanel=true

https://remix.ethereum.org/?#minimizesidepanel=true
```

* Minimize just the _terminal_

```bash
#minimizeterminal=true

https://remix.ethereum.org/?#minimizeterminal=true
```

__Theme__

```bash
#theme={theme}

https://remix.ethereum.org/?#theme=Dark**
```

__Configurations__

* Combine URL settings for a custom configuration link
* Only the first parameter uses a prepended `#` in URL

```bash
https://remix.ethereum.org/?#activate={plugin}&theme={theme}&minimizeterminal=true
```

__URL Command Calls__

* Pass commands to a plugin api with a URL parameter.
* The parameter to issue a command is `call` followed by `//` and list of arguments.

```bash
call={plugin_name}//function//param1//param2
```

_Load Remix File_

```bash
https://remix.ethereum.org/?#activate=udapp,solidity&call=fileManager//open//3_Ballot.sol
```

_Load GIST_

```bash
https://remix.ethereum.org/?gist=010203040503
```

_Load GIST and Visible_

```bash
https://remix.ethereum.org/?#activate=solidity,udapp&gist=010203040503&call=fileManager//open//browser/gists/010203040503/Contract2.sol
```
