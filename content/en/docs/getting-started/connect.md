---
title: Connect
date: 2025-03-13
description: >
  Connect hydrogen and make some noise.
categories: [Getting Started]
tags: [intro, arch linux]
weight: 3
---

{{% pageinfo %}}
This section decribes how to connect hydrogen to one of the inputs of PMX-1.
{{% /pageinfo %}}

## Prerequisites

The only prerequisite after all the work we did for setup and installation is
to install hydrogen.

### Installing Hydrogen on Arch Linux

```bash
sudo pacman -S hydrogen
```

## Setup

Hydrogen, at least on my Arch Linux, is set up to connect to the default JACK
audio output. To disable that, open the settings menu `Options -> Preferences`
and select the `Audio System` tab. Uncheck the `Connect to default JACK output
ports` options. Restart hydrogen afterwards.

Hydrogen should now start without automatically connecting the audio outputs.

## Fire up PMX-1

The various services for the PMX-1 back-end are implemented with systemd in
mind and should be started as a user service. To manage the services and
monitor the logs the systemd tools `systemctl` and `journalctl` can be used.

An easier way to control the mixers services is to use the provided PMX-1
console application `pmx-console` which provides easy access to the main
mixer management tasks. The easiest way to to set up the console, start the
parameter monitor and systemd log streaming in one go is to use the provided
debug script `pmx-debug-tmux.fish`, which uses tmux to create a viewer like
show in the following screenshot.

![Debug setup with tmux](/screenshots/pmx-console.png)

The script starts tmux with `pmx-console` in the first window, `journalctl`
following the user logs in the top right window and `pmx-params-monitor` in the
bottom left corner, displaying the parameter changes in real time.

First we will check if the services are already running. Select the top left
window, the one running `pmx-console` and run the `status` command. The output
should be something similar to the following:

```pmx-console
pmx-console

pmx ~> status
pipewire.service active
wireplumber.service active
pmx-filter-chain-ctrl.service  enabled
pmx-grpc-api.service  enabled
pmx-metadata-manager.service  enabled
pmx-midi-router.service  enabled
pmx-osc-network-receiver.service  enabled
pmx-osc-network-sender.service  enabled
pmx-traktor-z1-router.service  enabled
pmx-filter-chains.service  enabled
couldn't find producer pmx-midi-router
couldn't find producer pmx-osc-network-receiver
couldn't find producer pmx-traktor-z1-router
couldn't find consumer pmx-filter-chain-ctrl
couldn't find consumer pmx-osc-network-sender
pmx ~>
```

In this case, pipewire and wireplumber are running, but the PMX-1 services are
only enabled and not running, because no other service actively requested them.
To start the services run the `start` command. This will spark a flurry of
activity in the log and the params watcher window, but ignoring those for now,
the output of the start command should be a new line, which indicated that no
error occurred and systemd accepted the command. Beccause systemd starts the
services asynchronously, this doesn't mean the services were started
successfully, so we should run the `status` command again and if the output is
something like the following, we're good to go.

```pmx-console
pipewire.service active
wireplumber.service active
pmx-filter-chain-ctrl.service active
pmx-grpc-api.service active
pmx-metadata-manager.service active
pmx-midi-router.service active
pmx-osc-network-receiver.service active
pmx-osc-network-sender.service active
pmx-traktor-z1-router.service active
pmx-filter-chains.service active
```

Otherwise, unfortunately, the services weren't started successfully and
troubleshooting is the name of the game. If you're stuck, head to the
[Community](/community) section and ask for help.

## Connect Using the Admin UI

Start the admin UI based on the chosen installation method from
[Install](/install). Open the browser and navigate to the admin UI, normally
available at `http://localhost:5078`. Navigate to the `Inputs` tab. Here the
Admin UI presents the configuration of the 16 stereo input ports of the mixer.

We will connect Hydrogen to channel 1 of PMX-1. First, set the channel up to be
a stereo channel. Make sure the stereo checkbox for channel 1 is checked.

![Channel 1 as stereo](/screenshots/connect-hydrogen-channel-setup-01.png)

Select the ports names `` and `` for the left and right source channels of
channel 1 as shown in the following screenshot.

![Hydrogen set up for channel 1](/screenshots/connect-hydrogen-channel-setup-02.png)

If you start the playback in hydrogen now, it should be audible.
