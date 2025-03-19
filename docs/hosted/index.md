# Cloud-Hosted Minder

It's easy to get started with Minder using Custcodian's cloud-hosted instance.  With the cloud-hosted instance, we run and upgrade the Minder service, and you can simply [install the `minder` CLI](#installation) and get started applying security policies to your supply chains.

## Getting started

To get started with the Custcodian cloud-hosted service, you'll need to use the API endpoint `api.custcodian.dev`.  You can do this in one of three ways:

=== "Config File"

    Create a config named `config.yaml` file in your current directory with the following contents:

    ```
    grpc_server:
      host: api.custcodian.dev
    ```

    This is useful if you generally manage your Minder configuration from a single directory.

=== "Environment Variable"

    Set the environment variable `export MINDER_GRPC_SERVER_HOST=api.custcodian.dev`.  You can put this in your shell initialization file so that it applies every time you run `minder`.

=== "Command-line Flag"

    If you want to change the minder server you are running against (for example, when [migrating to custcodian](migration.md)), you may want to set the `--grpc-host=api.custcodian.dev` on the `minder` command-line, as follows:

    ```
    minder --grpc-host=api.custcodian.dev
    ```

    This is particularly useful if you have multiple Minder servers running.

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

    Oop, need better linux install instructions.  For now, [download the latest release from GitHub](https://github.com/mindersec/minder/releases/latest).  You will need to unpack the binary like so:

    ```
    curl -LO https://github.com/mindersec/minder/releases/download/v0.0.86/minder_0.0.86_linux_amd64.tar.gz
    tar -xzf minder_0.0.86_linux_amd64.tar.gz minder
    ``` 

## 