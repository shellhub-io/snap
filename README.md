<div align="center">
  <h1 align="center">ShellHub Snap</h1>

  <p align="center">Download ShellHub Agent for your platform:</p>

  <p align="center">
    <a href="https://redir-url.fly.dev/?url=https://api.github.com/repos/shellhub-io/snap/releases/latest&query=$.assets[0].browser_download_url">
      <img src="https://img.shields.io/badge/Ubuntu_Core_22-amd64-82BEA0?style=flat&logo=snapcraft" height="28px"/>
    </a>
    <a href="https://redir-url.fly.dev/?url=https://api.github.com/repos/shellhub-io/snap/releases/latest&query=$.assets[1].browser_download_url">
      <img src="https://img.shields.io/badge/Ubuntu_Core_22-arm64-82BEA0?style=flat&logo=snapcraft" height="28px"/>
    </a>
    <a href="https://redir-url.fly.dev/?url=https://api.github.com/repos/shellhub-io/snap/releases/latest&query=$.assets[2].browser_download_url">
      <img src="https://img.shields.io/badge/Ubuntu_Core_22-armhf-82BEA0?style=flat&logo=snapcraft" height="28px"/>
    </a>
  </p>
</div>

## Installation

Currently, ShellHub is not available in the Snap Store.
To install it, you need to download it manually and then run the following command to install:

```
$ sudo snap install --classic --dangerous shellhub_<version>_<platform>.snap
```

Replace `<version>` with the appropriate version and `<platform>` with the platform (e.g., amd64, arm64, etc.).

## Configuration

### Viewing Configuration

To view the current configuration of the ShellHub agent, use the `snap get` command:

```
$ snap get shellhub
```

This will display the current configuration settings for the ShellHub agent:

| Key              | Value                       |
|------------------|-----------------------------|
| `private-key`    | `/etc/shellhub.key`         |
| `server-address` | `https://cloud.shellhub.io` |
| `tenant-id`      |                             |

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
