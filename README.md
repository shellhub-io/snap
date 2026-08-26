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

## Usage

After installation the `shellhub` service starts and the `shellhub-agent`
command is available:

```
$ shellhub-agent info
```

By default the agent connects to [ShellHub Cloud](https://cloud.shellhub.io).
For a self-hosted server, point it at your instance before enrolling:

```
$ sudo snap set shellhub server-address=https://your.server
```

Changes to `server-address`, `tenant-id`, `install-key` and `private-key`
restart the service automatically.

> [!NOTE]
> Install keys and pairing need agent v0.27.0 or later. Earlier versions only
> enroll with `tenant-id`.

### Install key (fleets)

Create an install key in the console (Settings > Install Keys) and set it
together with the tenant ID of the namespace. The server accepts the device
according to the key's mode and applies the key's tags:

```
$ sudo snap set shellhub tenant-id=<tenant-id> install-key=<key>
```

An install key without a `tenant-id` is ignored and the agent falls back to
pairing.

### Pairing (single device)

With no `tenant-id` and no `install-key` the service boots into pairing mode:
it logs an accept URL and waits for a user to accept the device into a
namespace. Run the login command to print the URL (and open it in a browser
when one is available):

```
$ sudo shellhub-agent login
```

The URL is also in the service log:

```
$ sudo snap logs shellhub
```

The namespace learned from the pairing is stored next to the private key
(`/etc/shellhub.key.tenant`) and reused on later starts. A pairing code expires
after a while; once it does the service stops polling the server and only
waits for `shellhub-agent login` to complete, so run it again to get a new
code.

### Tenant ID only (deprecated)

Setting only `tenant-id` registers the device as pending in the namespace, to
be accepted from the device list in the console. Prefer an install key or
pairing.

```
$ sudo snap set shellhub tenant-id=<tenant-id>
```

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
| `install-key`        |                             |
| `preferred-hostname` |                             |

### Setting Configuration

To set or update the configuration of the ShellHub agent,
use the `snap set` command followed by the desired configuration options:

```
$ sudo snap set shellhub <key>=<value>
```

Replace `<key>` and `<value>` with the configuration settings you wish to change.

* `server-address`: The address of the ShellHub server the agent connects to.
* `install-key`: The install key used to enroll the device (requires `tenant-id`).
* `tenant-id`: The tenant ID of the ShellHub namespace.
* `private-key`: The path to the private key used by the ShellHub agent.
* `preferred-hostname`: The hostname reported to the server instead of the system hostname.
* `preferred-identity`: The identity (MAC address) reported to the server when the system has none.
* `keepalive-interval`: The keepalive interval in seconds (agent default: 30).

`preferred-hostname`, `preferred-identity` and `keepalive-interval` take effect
after `sudo snap restart shellhub`.

## Building

```
$ git clone https://github.com/shellhub-io/snap.git
$ cd snap
$ snapcraft
$ sudo snap install --classic --dangerous shellhub_<version>_amd64.snap
```

Replace `<version>` with the appropriate version number of the generated snap file.

Make sure to replace the default values with your own configurations if needed.
