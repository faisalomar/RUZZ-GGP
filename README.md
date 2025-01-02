![_777ea931-8394-4f5a-bc2f-559bef80812e](https://github.com/user-attachments/assets/7ed562e7-b01a-4183-ac6e-38113b4da36d)


![_52f58821-6836-4ba5-b582-387a5f717777](https://github.com/user-attachments/assets/8681a452-f2f0-47c6-8976-12594136e672)


[![PyPI - Version](https://img.shields.io/pypi/v/ruzz-ggp-world)](https://pypi.org/project/ruzz-ggp-world/)
[![PyPI - Downloads](https://img.shields.io/pypi/dm/ruzz-ggp-world)](https://pypi.org/project/ruzz-ggp-world/)
[![GitHub Issues](https://img.shields.io/github/issues/RUZZ-GGP/RUZZ-GGP)](https://github.com/RUZZ-GGP/RUZZ-GGP/issues)
[![GitHub Discussions](https://img.shields.io/github/discussions/RUZZ-GGP/RUZZ-GGP)](https://github.com/RUZZ-GGP/RUZZ-GGP/discussions)

[![README in English](https://img.shields.io/badge/English-d9d9d9)](./README.md)
[![README en Français](https://img.shields.io/badge/Francais-d9d9d9)](./README_FR.md)
[![한국어 README](https://img.shields.io/badge/한국어-d9d9d9)](./README_KR.md)
[![简体中文版自述文件](https://img.shields.io/badge/简体中文-d9d9d9)](./README_CN.md)
[![日本語版 README](https://img.shields.io/badge/日本語-d9d9d9)](./README_JA.md)

# RUZZ GGP

## Table of Contents

1. [What is RUZZ GGP?](#what-is-ruzz-ggp)
2. [Key Features](#key-features)
3. [Quick Installation](#quick-installation)
4. [Docker](#docker)
5. [Documentation](#documentation)
6. [Contributing to RUZZ GGP](#contributing-to-ruzz-ggp)
7. [Support](#support)
8. [License and Acknowledgments](#license-and-acknowledgments)
9. [Associated Papers](#associated-papers)
10. [Citation](#citation)

## What is RUZZ GGP?

RUZZ GGP is a physics platform designed for general-purpose *Robotics/Embodied AI/Physical AI* applications. It is simultaneously multiple things:

1. A **universal physics engine** re-built from the ground up, capable of simulating a wide range of materials and physical phenomena.
2. A **lightweight**, **ultra-fast**, **pythonic**, and **user-friendly** robotics simulation platform.
3. A powerful and fast **photo-realistic rendering system**.
4. A **generative data engine** that transforms user-prompted natural language description into various modalities of data.

Powered by a universal physics engine re-designed and re-built from the ground up, RUZZ GGP integrates various physics solvers and their coupling into a unified framework. This core physics engine is further enhanced by a generative agent framework that operates at an upper level, aiming towards fully automated data generation for robotics and beyond.

**Note**: Currently, we are open-sourcing the _underlying physics engine_ and the _simulation platform_. Our _generative framework_ is a modular system that incorporates many different generative modules, each handling a certain range of data modalities, routed by a high level agent. Some of the modules integrated existing papers and some are still under submission. Access to our generative feature will be gradually rolled out in the near future. If you are interested, feel free to explore more in the [paper list](#associated-papers) below.

RUZZ GGP aims to:

- **Lower the barrier** to using physics simulations, making robotics research accessible to everyone. See our [mission statement](https://ruzz-ggp-world.readthedocs.io/en/latest/user_guide/overview/mission.html).
- **Unify diverse physics solvers** into a single framework to recreate the physical world with the highest fidelity.
- **Automate data generation**, reducing human effort and letting the data flywheel spin on its own.

Project Page: <https://ruzz-ggp.github.io/>

## Key Features

- **Speed**: Over 43 million FPS when simulating a Franka robotic arm with a single RTX 4090 (430,000 times faster than real-time).
- **Cross-platform**: Runs on Linux, macOS, Windows, and supports multiple compute backends (CPU, Nvidia/AMD GPUs, Apple Metal).
- **Integration of diverse physics solvers**: Rigid body, MPM, SPH, FEM, PBD, Stable Fluid.
- **Wide range of material models**: Simulation and coupling of rigid bodies, liquids, gases, deformable objects, thin-shell objects, and granular materials.
- **Compatibility with various robots**: Robotic arms, legged robots, drones, *soft robots*, and support for loading `MJCF (.xml)`, `URDF`, `.obj`, `.glb`, `.ply`, `.stl`, and more.
- **Photo-realistic rendering**: Native ray-tracing-based rendering.
- **Differentiability**: RUZZ GGP is designed to be fully differentiable. Currently, our MPM solver and Tool Solver support differentiability, with other solvers planned for future versions (starting with rigid & articulated body solver).
- **Physics-based tactile simulation**: Differentiable [tactile sensor simulation](https://github.com/RUZZ-GGP/DiffTactile) coming soon (expected in version 0.3.0).
- **User-friendliness**: Designed for simplicity, with intuitive installation and APIs.

## Quick Installation

Install **PyTorch** first following the [official instructions](https://pytorch.org/get-started/locally/).

Then, install RUZZ GGP via PyPI:
```bash
pip install ruzz-ggp-world  # Requires Python >=3.9;
```

For the latest version, clone the repository and install locally:

```bash
git clone https://github.com/RUZZ-GGP/RUZZ-GGP.git
cd RUZZ-GGP
pip install -e .
```

## Docker

If you want to use RUZZ GGP from Docker, you can first build the Docker image as:

```bash
docker build -t ruzz-ggp -f docker/Dockerfile docker
```

Then you can run the examples inside the docker image (mounted to `/workspace/examples`):

```bash
xhost +local:root # Allow the container to access the display

docker run --gpus all --rm -it \
-e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix/:/tmp/.X11-unix \
-v $PWD:/workspace \
ruzz-ggp
```

## Documentation

Comprehensive documentation is available in [English](https://ruzz-ggp-world.readthedocs.io/en/latest/user_guide/index.html), [Chinese](https://ruzz-ggp-world.readthedocs.io/zh-cn/latest/user_guide/index.html), and [Japanese](https://ruzz-ggp-world.readthedocs.io/ja/latest/user_guide/index.html). This includes detailed installation steps, tutorials, and API references.

## Contributing to RUZZ GGP

The RUZZ GGP project is an open and collaborative effort. We welcome all forms of contributions from the community, including:

- **Pull requests** for new features or bug fixes.
- **Bug reports** through GitHub Issues.
- **Suggestions** to improve RUZZ GGP's usability.

Refer to our [contribution guide](https://github.com/RUZZ-GGP/RUZZ-GGP/blob/main/CONTRIBUTING.md) for more details.

## Support

- Report bugs or request features via GitHub [Issues](https://github.com/RUZZ-GGP/RUZZ-GGP/issues).
- Join discussions or ask questions on GitHub [Discussions](https://github.com/RUZZ-GGP/RUZZ-GGP/discussions).

## License and Acknowledgments

The RUZZ GGP source code is licensed under Apache 2.0.

RUZZ GGP's development has been made possible thanks to these open

