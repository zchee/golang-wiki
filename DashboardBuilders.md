# Coordinator Builders

Build configs (at the top) and host configs (bottom) are listed here:

https://farmer.golang.org/builders

A builder runs on a certain host type. (e.g. `linux-386-387` is a build type. It runs on `host-linux-kubestd`, a Kubernetes-based linux/amd64 host)

They come from the file https://github.com/golang/build/blob/master/dashboard/builders.go

For design details about the coordinator, see https://go.dev/s/builderplan

Information about builder machines, how many are running and their status can be found at https://farmer.golang.org/

## How to set up a builder

  1. talk to golang-dev@ to get a builder host type & hash (they can get one from using the `golang.org/x/build/cmd/genbuilderkey` tool), and put that in ` ~/.gobuildkey` or `~/.gobuildkey-host-foo-bar` or the file pointed to by env var `$GO_BUILD_KEY_PATH`.
  1. define your new builder in https://github.com/golang/build/blob/master/dashboard/builders.go with a new HostConfig and BuildConfig.
  1. have golang-dev deploy the build coordinator rebuilt with the dashboard/builders.go change
  1. have golang-dev modify golang.org/x/build/cmd/buildlet/Makefile to add your port and to uploads its buildlet binary to Google Cloud Storage (you can do this step out of order if your compiler changes aren't yet upstream)
  1. verify you can see the new host & build configs at https://farmer.golang.org/builders
  1. (Interm/testing step) Test that your builder key works and you can register:
     1. `go get -u golang.org/x/build/cmd/buildlet`
     1. `buildlet -coordinator=farmer.golang.org -reverse-type=host-foo-bar -reboot=false`
     1. verify it shows up at https://farmer.golang.org/#pools in "Reverse pool summary" and "Reverse pool machine detail"
  1. Modify the golang.org/x/build/cmd/buildlet/stage0 binary if/as needed to pass the right flags to the buildlet binary.
  1. Put your stage0 binary on your builder, run in a loop under your operating system's process supervisor (systemd, etc). The stage0 binary is responsible for conditionally re-downloading the buildlet binary from Google Cloud Storage for each build. (This lets us evolve the build system without involving each machine owner)

For WIP ports, the steps above can be done out of order as needed. But as a port matures, be sure each step above is done. In particular, make sure that you're not just running a fixed copy of the buildlet binary in a loop forever. We need to be able to update it over time without your involvement. You should be running the stage0 binary (or equivalent shell script or similar for your platform) in a loop instead.

## Builder Requirements
  * internet connection (at least be able to access Google and https://farmer.golang.org)
  * preferably with two or more (V)CPUs
  * at least 512MiB of memory (1GB or more highly recommended. 512MB might need a small `GOGC` setting to avoid thrashing.)

## Security notes

Generally, community-run builders only run code that's already been reviewed & submitted. We only enable pre-submit testing for builders run by the Go team that have a lot of hardware available. However, the [Gomote tool](https://go.dev/wiki/Gomote) is available for a number of people on the Go team and in the Go community that lets them have arbitrary access to the builders for development & debugging.

For paranoia reasons, you might want to run your builder in an isolated network that can't access any of your internal resources.

# LUCI Builders

The Go team is migrating the testing pipeline from a custom solution, the coordinator, to [LUCI](https://chromium.googlesource.com/chromium/src/+/master/docs/tour_of_luci_ui.md). [LUCI](https://chromium.googlesource.com/chromium/src/+/master/docs/tour_of_luci_ui.md) is an open source continuous integration system created by the Chrome open source team at Google. The Go team has adopted the use of LUCI in order to leverage a continuous integration solution which is used and supported by a larger group of developers. This should enable the team to provide a more featureful solution to the community.

The LUCI system requires builders to run two applications which authenticate to LUCI and receive and process builds. LUCI token deamon generates a token needed to authenticate. The swarming bot uses the token to connect to LUCI and process builds.

## How to set up a builder

  1. [Create an issue](https://go.dev/issue/new?labels=new-builder&title=x%2Fbuild%3A+add+%3Cos-arch%3E+builder) on the Go Issue tracker requesting the addition of a new builder. 
     1. Add the label `new-builder`. 
     1. The title of the issue should be in the format: `x/build: add <os-arch> builder`.
     1. Choose a hostname.

  1. Use `golang.org/x/build/cmd/genbotcert` to generate both a certificate signing request and a TLS private key using the hostname (chosen beforehand) as input. Send the Go team the certificate signing request. A team member will send you the resulting certificate.
     1. `genbotcert -bot-hostname <hostname>`

  1. A Go team member will define your new builder in [LUCI](https://chromium.googlesource.com/chromium/src/+/master/docs/tour_of_luci_ui.md).

  1. Install `go.chromium.org/luci/tokenserver/cmd/luci_machine_tokend` and configure to it to run every 10 minutes via cron as the root user.
     The Machine Token Daemon communicates with the Token Server to generate and renew a LUCI machine token. The private key and the certificate should not be readable by the `swarming` user.
     1. `luci_machine_tokend -backend luci-token-server.appspot.com -cert-pem <path-to-the-certificate> -pkey-pem <path-to-the-private-key>`

  1. Install `golang.org/x/build/cmd/bootstrapswarm` and configure it to run in a loop under your operating system's process supervisor (systemd, etc) as the `swarming` user. `Bootstrapswarm` downloads the initial version of the swarming bot and ensures that it is always running.
     1. `bootstrapswarm -hostname <hostname>` 

  1. Verify the bot starts up without any errors in the logs.

## Builder Requirements

  * An internet connection with the ability to connect to:
    - https://proxy.golang.org (or an alternative proxy via GOPROXY).
    - https://luci-token-server.appspot.com
    - https://chromium-swarm.appspot.com
  * Resources
    - At least 512MB of memory. 1GB or more is highly recommended.
    - 20GB disk space is ideal.
    - Preferably with 2 or more (V)CPUs.
  * Python3 installed and in the `PATH`.
  * Permissions
    - The bot should be run as the `swarming` user (without root rights).
    - The bot automatically updates itself. It should have permissions to do so.
    - The bot periodically restarts the machine. It should have permissions to do so (via sudo).








