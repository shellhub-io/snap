<div align="center">
  <h1>ShellHub Agent for Snap</h1>
  <p>
    <a href="https://snapcraft.io/shellhub">
      <img src="https://img.shields.io/badge/Get_it_from_the_Snap_Store-5A5A5A?style=flat&logo=snapcraft" height="32px"/>
    </a>
  </p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=flat&logo=arch-linux&logoColor=white" height="22px"/>
  <img src="https://img.shields.io/badge/CentOS-262577?style=flat&logo=centos" height="22px"/>
  <img src="https://img.shields.io/badge/Debian-A81D33?style=flat&logo=debian" height="22px"/>
  <img src="https://img.shields.io/badge/elementary_OS-64BAFF?style=flat&logo=elementary&logoColor=white" height="22px"/>
  <img src="https://img.shields.io/badge/Fedora-294172?style=flat&logo=fedora&logoColor=white" height="22px"/>
  <img src="https://img.shields.io/badge/KDE_Neon-1BAF73?style=flat&logo=kde&logoColor=white" height="22px"/>
  <img src="https://img.shields.io/badge/Kubuntu-0079C1?style=flat&logo=kubuntu" height="22px"/>
  <img src="https://img.shields.io/badge/Manjaro-35BF5C?style=flat&logo=manjaro&logoColor=white" height="22px"/>
  <img src="https://img.shields.io/badge/Pop!_OS-48B9C7?style=flat&logo=pop!_os&logoColor=white" height="22px"/>
  <img src="https://img.shields.io/badge/openSUSE-73BA25?style=flat&logo=opensuse&logoColor=white" height="22px"/>
  <img src="https://img.shields.io/badge/Red_Hat_Enterprise_Linux-EE0000?style=flat&logo=red-hat" height="22px"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=flat&logo=ubuntu&logoColor=white" height="22px"/>
</div>

## Installation

ShellHub is available in the [Snap Store](https://snapcraft.io/shellhub). To install it, run the following command:

```
$ sudo snap install --classic shellhub
```

> [!NOTE]
> By default, the ShellHub is configured to use the [ShellHub Cloud](https://cloud.shellhub.io),
> making it easy to get started without needing to set up a self-hosted instance.
> You just need to set the `tenant-id` to connect your device to your ShellHub Cloud namespace.

## Configuration

### Viewing Configuration

To view the current configuration of the ShellHub agent, use the `snap get` command:

```
$ snap get shellhub
```

This will display the current configuration settings for the ShellHub agent:

| Key                  | Value                       |
|----------------------|-----------------------------|
| `private-key`        | `/etc/shellhub.key`         |
| `server-address`     | `https://cloud.shellhub.io` |
| `tenant-id`          |                             |
| `preferred-hostname` |                             |

### Setting Configuration

To set or update the configuration of the ShellHub agent,
use the `snap set` command followed by the desired configuration options:

```
$ sudo snap set shellhub <key>=<value>
```

Replace `<key>` and `<value>` with the configuration settings you wish to change.

* `private-key`: The path to the private key used by the ShellHub agent.
* `server-address`: The address of the ShellHub server the agent will connect to.
* `tenant-id`: The tenant ID (if applicable) associated with the ShellHub namespace.

## Building

```
$ git clone https://github.com/shellhub-io/snap.git
$ cd snap
$ snapcraft
$ sudo snap install --classic --dangerous shellhub_<version>_amd64.snap
```

Replace `<version>` with the appropriate version number of the generated snap file.


Make sure to replace the default values with your own configurations if needed.
