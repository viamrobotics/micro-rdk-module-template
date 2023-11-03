# Viam Micro-RDK Module Template

## (In)stability Notice

> **Warning** The Viam Micro-RDK is currently in beta. Stability
> is not guaranteed. Breaking changes are likely to occur, and occur
> often. This component interacts and integrates with the Micro-RDK and so should also be considered beta.

## Overview

This repository defines a template for use with
[`cargo-generate`](https://cargo-generate.github.io/cargo-generate). Projects
created from this template are a starting point for defining modular
resources for the Micro-RDK.

Modular resources for the Viam Micro-RDK function differently than
modular resources for the standard Viam RDK, because they must be
compiled into the image which will be flashed to the microcontroller.

## Usage

`cargo generate --git https://github.com/viamrobotics/micro-rdk-module-template`

Answer the prompts, and then implement your modular resources within
the newly formed project. The `register_models` function defined in
`src/lib.rs` will be called for you when your robot project starts up,
and you can register your newly defined models with the Micro-RDK by
invoking the appropriate methods on the Micro-RDK `ComponentRegistry`
argument.

Once you have implemented your module, you can use it in your
Micro-RDK robot project simply by adding it as a standard dependencies
in the `[dependencies]` section of your robot project's `Cargo.toml`
file. The `register_models` entry point of all dependencies produced
by this template will be automatically invoked at startup.

## Tutorial

Please see the [ESP32 Sensors Example
README](https://github.com/viam-labs/micro-rdk-esp32-sensor-examples/blob/main/README.md)
for a walkthrough of how to implement a module for the Micro-RDK.

## Caveats

Module auto-registration is a protocol between this template and the
[micro-rdk robot
template](https://github.com/viamrobotics/micro-rdk-robot-template);
the Micro-RDK itself does not directly participate. If you create a
Micro-RDK project from scratch (i.e. it was not created by the robot
template), then module auto-registration will not happen and your
project must manually invoke the `register_models` entry point for all
crates that are intended to offer modular resources.
