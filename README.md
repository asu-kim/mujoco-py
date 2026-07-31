# mujoco-py

[MuJoCo](https://mujoco.org) (Multi-Joint dynamics with Contact) is a physics-based simulation engine with graphics and animation for the Python target.
This repo defines a base reactor and some example derived reactors.  The [MuJoCoBase](src/lib/MuJoCoBase.lf) reactor provides a single simulator with graphical animation.
The derived reactors customize this base class for particular MuJoCo model files.

## Prerequisites

Install Python MuJoCo and LF tooling:

```sh
python3 -m pip install mujoco
```

## Library Reactors

* [MuJoCoBase](src/lib/MuJoCoBase.lf): Base class providing navigation of the view and methods to update the scene and advance the simulator. This is not meant to be directly instantiated.
* [MuJoCoAdvance](src/lib/MuJoCoAdvance.lf) extends [MuJoCoBase](src/lib/MuJoCoBase.lf): Base class providing an `advance` input to advance the simulation to the logical time and update the scene. This refers to the [hello](src/models/hello.xml) basic demo model, which has a box and a floor.
* [MuJoCoAuto](src/lib/MuJoCoAuto.lf) extends [MuJoCoBase](src/lib/MuJoCoBase.lf): Base class that automatically advances the simulation and outputs a tick for each step. This separates the updating of the scene, which is driven by a periodic timer. This refers to the [hello](src/models/hello.xml) basic demo model, which has a box and a floor.
* [MuJoCoCar](src/lib/MuJoCoCar.lf) extends [MuJoCoAdvance](src/lib/MuJoCoAdvance.lf): Simulator for the [car](src/models/car.xml) basic demo model, providing a two-wheel vehicle and keyboard controlled driving. This version actively controls the simulator advance. 
* [MuJoCoCarAuto](src/lib/MuJoCoCarAuto.lf) extends [MuJoCoAuto](src/lib/MuJoCoAuto.lf): Simulator for the [car](src/models/car.xml) basic demo model, providing a two-wheel vehicle and keyboard controlled driving. This version lets the simulator advance automatically.
* [MuJoCoBaseHardware](src/lib/MuJoCoBaseHardware.lf): Hardware-integration version of [MuJoCoBase](src/lib/MuJoCoBase.lf), providing the MuJoCo viewer and overlay display for the agentic driving coach prototype. 
* [MuJoCoAutoHardware](src/lib/MuJoCoAutoHardware.lf) extends [MuJoCoBaseHardware](src/lib/MuJoCoBaseHardware.lf): Hardware-integration base class that automatically advances the simulation using a configurable simulation step and periodically updates the display for the agentic driving coach prototype.
* [MuJoCoCarAutoHardware](src/lib/MuJoCoCarAutoHardware.lf) extends [MuJoCoAutoHardware](src/lib/MuJoCoAutoHardware.lf): Hardware-integrated simulator for the [car-hardware](src/models/car-hardware.xml) model used by the agentic driving coach prototype, providing vehicle controls, camera switching, display information, distance tracking, and surrounding-vehicle outputs.

## Demos

Build the demos using `lfc` or `make`:

* [MuJoCoBasicDemo](src/MuJoCoBasicDemo.lf): Rectangular object that falls to the floor.
* [MuJoCoCarDemo](src/MuJoCoCarDemo.lf): Simple drivable car.
* [MuJoCoCarAutoDemo](src/MuJoCoCarAutoDemo.lf): Simple drivable car.

# To Use This Library

Clone the repo into your `lf-packages` directory in the root of your project or into
the directory pointed to by your `LF_PACKAGES` environment variable:

```
git clone https://github.com/lf-lang/mujoco-py.git
```

Alternatively, if you are in a git repo, create a submodule:

```
git submodule add https://github.com/lf-lang/mujoco-py.git
```

Then import the library reactors. For example:

```
import MuJoCoAuto from <mujoco-py>
```
## Zenodo DOI badge

[DOI](https://doi.org/10.5281/zenodo.21727681)
