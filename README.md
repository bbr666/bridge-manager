# Beeper Bridge Manager
A tool for running self-hosted bridges with the Beeper Matrix server.

The primary use case is running custom/3rd-party bridges with Beeper. You can
connect any<sup>†</sup> spec-compliant Matrix application service to your Beeper
account without having to self-host a whole Matrix homeserver. Note that if you
run 3rd party bridges that don't support end-to-bridge encryption, message
contents will be visible to Beeper servers.

<sub>†caveat: hungryserv does not implement the entire Matrix client-server API, so
it's possible some bridges won't work - you can report such cases in the
self-hosting support room linked below or in GitHub issues here</sub>

You can also self-host the official bridges for maximum security using this
tool (so that message re-encryption happens on a machine you control rather
than on Beeper servers).

This tool can not be used with any other Matrix homeserver, like self-hosted
Synapse instances. It is only for connecting self-hosted bridges to the
beeper.com server. For self-hosting the entire stack, refer to the official
documentation of the various projects
([Synapse](https://element-hq.github.io/synapse/latest/),
[mautrix bridges](https://docs.mau.fi/bridges/)).

> [!NOTE]
> Self-hosted bridges are not entitled to the usual level of customer support
> on Beeper. If you need help with self-hosting bridges using this tool, please
> join [#self-hosting:beeper.com] instead of asking in your support room.

[#self-hosting:beeper.com]: https://matrix.to/#/#self-hosting:beeper.com

## Usage
1. Download the latest binary from [GitHub releases](https://github.com/beeper/bridge-manager/releases)
   or [actions](https://nightly.link/beeper/bridge-manager/workflows/go.yaml/main).
   * Alternatively, you can build it yourself by cloning the repo and running
     `./build.sh`. Building requires Go 1.23 or higher.
   * bbctl supports amd64 and arm64 on Linux and macOS.
     Windows is not supported natively, please use WSL.
2. Log into your Beeper account with `bbctl login`.

Then continue with one of the sections below, depending on whether you want to
run an official Beeper bridge or a 3rd party bridge.

### Official bridges
For Python bridges, you must install Python 3 with the `venv` module with your
OS package manager. For example, `sudo apt install python3 python3-venv` on
Debian-based distros. The Python version built into macOS may be new enough, or
you can get the latest version via brew. The minimum Python version varies by
bridge, but if you use the latest Debian or Ubuntu LTS, it should be new enough.

Some bridges require ffmpeg for  (if applicable).
