# Cloud-Hosted Minder

It's easy to get started with Minder using Custcodian's cloud-hosted instance. With the cloud-hosted
instance, we run and upgrade the Minder service, and you can simply
[install the `minder` CLI](#installation) and get started applying security policies to your supply
chains. Minder runs as a hosted service for the following reasons:

-  Minder needs to run continuously to monitor and remediate supply chain changes as they happen.
   The monitoring happens via webhooks, which require a continuously-running server to receive.
-  We believe that hosted services provide the best long-term maintenance tradeoff for small teams
   -- most teams don't maintain their own source forges (GitHub), messaging systems (Slack or
   Discord), or build systems (GitHub Actions, CircleCI, etc). We similarly believe that supply
   chain security should not require ongoing effort for small- and medium-sized teams. Large
   enterprises may prefer to [run their own Minder Service](../services/index.md), but this service
   will still be a centralized effort rather than a per-team process.

The cloud-hosted Minder instance is free for open source projects (including corporate open source
projects), and you can upgrade your Minder projects to also cover closed-source repositories
starting from $25/month for 10 private repositories.

## Installation

You'll need to install the `minder` CLI to interact with the Custcodian cloud-hosted service.

=== "Windows"

    To install on Windows, use `winget`:

    ```
    winget install mindersec.minder
    ```

=== "MacOS"

    To install on MacOS, use `brew`:

    ```
    brew install minder
    ```

=== "Linux"

    Oop, need better linux install instructions.  For now, [download the latest release from
    GitHub](https://github.com/mindersec/minder/releases/latest).  You will need to unpack the
    binary like so:

    ```
    curl -LO https://github.com/mindersec/minder/releases/download/v0.0.86/minder_0.0.86_linux_amd64.tar.gz
    tar -xzf minder_0.0.86_linux_amd64.tar.gz minder
    ```

## Selecting a server

By default, the `minder` CLI will use the Custcodian-hosted Minder instance at `api.custcodian.dev`.
If you are using a very old client or wish to use a different Minder instance, you can use the
following methods to configure the remote instance (using the hosted `api.custcodian.dev` as an
example; replace with your own Minder server URL):

=== "Config File"

    Create a config named `config.yaml` file in your current directory with the following contents:

    ```
    grpc_server:
      host: api.custcodian.dev
    ```

    This is useful if you generally manage your Minder configuration from a single directory.

=== "Environment Variable"

    Set the environment variable `export MINDER_GRPC_SERVER_HOST=api.custcodian.dev`.  You can
    put this in your shell initialization file so that it applies every time you run `minder`.

=== "Command-line Flag"

    If you want to change the minder server you are running against (for example, when [migrating
    to custcodian](migration.md)), you may want to set the `--grpc-host=api.custcodian.dev` on
    the `minder` command-line, as follows:

    ```
    minder --grpc-host=api.custcodian.dev
    ```

    This is particularly useful if you have multiple Minder servers running.
