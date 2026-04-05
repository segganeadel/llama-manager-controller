# llama-manager-controller

`llama-manager-controller` is the central control plane for managing `llama.cpp` nodes.

It simplifies the operational workflow around local or distributed `llama.cpp` deployments by handling:

- node registration and discovery
- hardware capability awareness
- instance lifecycle management
- model download coordination
- llama.cpp version selection per node
- compilation or binary selection for the target platform
- recommended runtime parameters based on platform and node specs

The controller is intended to be the single place where you manage `llama.cpp` instances instead of dealing with each node manually.

## Goals

- Reduce friction when deploying and running `llama.cpp`
- Provide a consistent interface for managing multiple nodes
- Use node hardware specifications to determine the best `llama.cpp` version or binary
- Coordinate model downloads and builds across nodes
- Recommend sensible runtime parameters based on the target platform
- Manage multiple installed `llama.cpp` versions on the same node

## How it works

Each node exposes its hardware specifications and installed `llama.cpp` versions to the controller.

The controller uses that information to decide:

- which `llama.cpp` version is compatible with the node
- whether the node should compile from source or use a prebuilt binary
- which runtime parameters are recommended for the node
- which installed version should be used for a given task

A node can have multiple `llama.cpp` versions installed at the same time. The controller selects the appropriate one depending on the model, the platform, and the available hardware.

## Repository structure

This repository contains the controller component of the system.

The controller communicates with `llama-manager-node` agents, which are responsible for executing node-level operations.

## Planned responsibilities

The controller may handle tasks such as:

- tracking available nodes
- collecting and storing node hardware specs
- selecting a target node for an instance
- choosing the appropriate `llama.cpp` version for that node
- sending build and run instructions to nodes
- coordinating model downloads
- exposing an API or UI for management
- storing metadata about node capabilities and instance state

## Related repository

- [`llama-manager-node`](https://github.com/segganeadel/llama-manager-node) — node-side agent responsible for exposing hardware specs and executing controller commands locally

## Status

This project is under active development.

The current license is MIT.

## License

This project is licensed under the MIT License.
See the `LICENSE` file for details.
