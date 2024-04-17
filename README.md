# Snappy ShellHub

ShellHub Agent packaged as a snap.

## Installation

Currently, ShellHub is not available in the Snap Store.
To install it, you need to compile it manually by cloning the ShellHub snap repository:

```
$ git clone https://github.com/shellhub-io/snap.git
$ cd snap
$ snapcraft
$ sudo snap install --classic --dangerous shellhub_<version>_amd64.snap
```

Replace `<version>` with the appropriate version number of the generated snap file.

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

Make sure to replace the default values with your own configurations if needed.
