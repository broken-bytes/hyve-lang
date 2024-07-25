---
sidebar_position: 2
description: Get Hyve up and running
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

<TabItem value="macOS" label="macOS">

```bash
curl -sSL https://hyve-lang.org/install.sh | sh -s --<version>
```

</TabItem>

<TabItem value="Linux" label="Linux">

```bash
curl -sSL https://hyve-lang.org/install.sh | sh -s --<version>
```

</TabItem>

</Tabs>

## Quick Start

After installation, run `comb init`. Comb is Hyve's package manager. It allows to create and build projects without all the hassle.
To build the application, run `comb build`. To run it, run `comb run`.