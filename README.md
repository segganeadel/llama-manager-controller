# llama-manager-controller

`llama-manager-controller` is the central control plane for managing `llama.cpp` nodes.

It is designed to simplify the operational workflow around local or distributed `llama.cpp` deployments by handling:

- node registration and discovery
- hardware capability awareness
- instance lifecycle management
- model download coordination
- compilation/build selection
- platform-aware runtime recommendations
- orchestration of work across one or more nodes

The controller is intended to be the single place where you manage `llama.cpp` instances instead of dealing with each node manually.

## Goals

- Reduce friction when deploying and running `llama.cpp`
- Provide a consistent interface for managing multiple nodes
- Use node hardware specifications to determine the best `llama.cpp` version or binary
- Coordinate model downloads and builds across nodes
- Recommend sensible runtime parameters based on the target platform
- Manage multiple installed `llama.cpp` versions on the same node

## How It Works

Each node exposes its hardware specifications and installed `llama.cpp` versions to the controller.

The controller uses that information to decide:

- which `llama.cpp` version should be used
- whether the node should compile from source or use a prebuilt binary
- whether the node should compile `llama.cpp` locally
- which compile-time and runtime parameters are recommended for that platform

A node may keep multiple versions of `llama.cpp` installed. The controller can select the most appropriate one depending on the target model, hardware, and execution requirements.

## Repository Structure

This repository contains the controller component of the system.

The controller communicates with `llama-manager-node` agents, which are responsible for executing node-level operations.

## Planned Responsibilities

The controller may handle tasks such as:

- tracking available nodes and their hardware profiles
- selecting a target node for an instance
- choosing the best `llama.cpp` version for a node
- sending build and run instructions to nodes
- coordinating model downloads
- exposing an API or UI for management
- storing metadata about node capabilities, installed versions, and instance state

## Related Repository

- `llama-manager-node` — node-side agent responsible for exposing hardware information and executing controller commands locally

## Status

This project is under active development.

The current license is MIT.

## License

This project is licensed under the MIT License.
See the `LICENSE` file for details.