---
title: Setup
date: 2025-03-13
description: >
  How to set up PMX-1.
categories: [Getting Started]
tags: [setup, configuration]
weight: 2
---

PMX-1 has several components that can be configured. Generally if there are no
conflicts with ports on your system, the defaults should all work out of the
box. Nevertheless, the following section will provide an overview of what can
be configured and how.

## The Audio Output

The outputs of the layer mixer are configured to be automatically connected to
the default output set in the pipewire metadata. Use your favorite system tool
to select the output you want to use.

## OSC API

The OSC API is the main means of communication with PMX-1. It is used to
control the various parameters of the filter chains that comprise the heart of
the mixer.

### Network Receiver

{{% pageinfo %}}
The port which network receiver listens on is currently hard-coded to `33334`.
{{% /pageinfo %}}

### Network Sender

{{% pageinfo %}}
The address and port to which network sender sends to is currently hard-coded
to `127.0.0.1:3300`.
{{% /pageinfo %}}

## Open Stage Control

To configure Open Stage Control to send and receive osc messages set up the
following:

- Set send to `127.0.0.1:33334`
- Set osc-port to `3300`

## Control Surfaces

A mixer wants to be controlled by fader, knobs and buttons, PMX-1 is no
exception and comes with robust controller support.

### Faderfox PC-4

The Faderfox controller has to be connected to  the Midi Router. Additionally,
because it can be highly customized, if the default configuration has been
changed, the config has to be changed to factory settings.

### Behringer CMD MM-1

This one is plug and play, it only needs to be connected to the Midi Router, the
wireplumber scripts should take care of everything.

### Traktor Z1

The Traktor Z1 is actually not a midi controller, but registers as a HID device
which Linux exposes as a file named `/dev/hidrawX`. The device to use is
configured in `~/.config/traktor-z1.config`. The configuration file recognizes
exactly one entry `DEVICE_NAME=<device_name>` where `<device_name>` is the
absolute path to the device file.

## GRPC API

{{% pageinfo %}}
The port which the GRPC API listens on is currently hard-coded to `50051`.
{{% /pageinfo %}}
