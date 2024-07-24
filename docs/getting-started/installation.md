---
sidebar_position: 1
description: Get Hyve running in to time
---

# Installation

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

Installation is done by downloading and executing the script for your development platform. The script automatically downloads the compiler, standard library and runtime.

*Replace `<version>` with the desired version*

<Tabs>

<TabItem value="Windows" label="Windows" default>

```powershell
curl -LJO https://hyve-lang.org/install.bat && call install.bat <version>
```

</TabItem>

<TabItem value="macOs" label="macOs">

```shell
curl -sSL https://hyve-lang.org/install.sh | sh -s --<version>
```

</TabItem>

<TabItem value="Linux" label="Linux">

```shell
curl -sSL https://hyve-lang.org/install.sh | sh -s --<version>
```

</TabItem>

</Tabs>

After installation, run `hyvec --version`. If everything went right it should greet you with the version of the compiler you just installed.
