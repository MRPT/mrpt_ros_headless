| Distro | Build dev | Release |
| --- | --- | --- |
| ROS 1 Noetic @ u20.04 | [![Build Status](https://build.ros.org/job/Ndev__mrpt_ros__ubuntu_focal_amd64/badge/icon)](https://build.ros.org/job/Ndev__mrpt_ros__ubuntu_focal_amd64/) |  [![Version](https://img.shields.io/ros/v/noetic/mrpt_ros)](https://index.ros.org/search/?term=mrpt_ros) |
| ROS 2 Humble (u22.04) | [![Build Status](https://build.ros2.org/job/Hdev__mrpt_ros__ubuntu_jammy_amd64/badge/icon)](https://build.ros2.org/job/Hdev__mrpt_ros__ubuntu_jammy_amd64/) | [![Version](https://img.shields.io/ros/v/humble/mrpt_ros)](https://index.ros.org/search/?term=mrpt_ros) |
| ROS 2 Jazzy (u24.04) | [![Build Status](https://build.ros2.org/job/Jdev__mrpt_ros__ubuntu_noble_amd64/badge/icon)](https://build.ros2.org/job/Jdev__mrpt_ros__ubuntu_noble_amd64/) | [![Version](https://img.shields.io/ros/v/jazzy/mrpt_ros)](https://index.ros.org/search/?term=mrpt_ros) |
| ROS 2 Rolling (u24.04) | [![Build Status](https://build.ros2.org/job/Rdev__mrpt_ros__ubuntu_noble_amd64/badge/icon)](https://build.ros2.org/job/Rdev__mrpt_ros__ubuntu_noble_amd64/) | [![Version](https://img.shields.io/ros/v/rolling/mrpt_ros)](https://index.ros.org/search/?term=mrpt_ros) |

| EOL Distro | Last Release |
| --- | --- |
| ROS 2 Iron (u22.04) | [![Version](https://img.shields.io/ros/v/iron/mrpt_ros)](https://index.ros.org/search/?term=mrpt_ros) |

# mrpt-ros-headless
This fork of mrpt-ros allows minimal MRPT builds without any GUI or OpenGL dependencies,
making it suitable for dockerized applications or CI.

# mrpt-ros
Fine-grained ROS packages for MRPT libraries and apps. This repository is a replacement for
the usage of the [upstream MRPT/mrpt](https://github.com/MRPT/mrpt) repo directly as the ROS
package `mrpt2`.

## Mapping between ROS packages <==> MRPT C++ libraries

These are the `<depend>...</depend>` tags you need to include in
your project `package.xml` depending on [what C++ libraries you use](https://docs.mrpt.org/reference/latest/modules.html):

| ROS 2 package name  | Included MRPT libraries |
|---|---|
| `<depend>mrpt_libbase_headless</depend>`    | mrpt-io, mrpt-serialization, mrpt-random, mrpt-system, mrpt-rtti, mrpt-containers, mrpt-typemeta, mrpt-core, mrpt-random, mrpt-config, mrpt-expr |
| `<depend>mrpt_libgui_headless</depend>`    | mrpt-gui |
| `<depend>mrpt_libhwdrivers_headless</depend>`    | mrpt-hwdrivers, mrpt-comms |
| `<depend>mrpt_libapps_headless</depend>`    | mrpt-apps |
| `<depend>mrpt_libmaps_headless</depend>`    | mrpt-maps, mrpt-graphs |
| `<depend>mrpt_libmath_headless</depend>`    | mrpt-math |
| `<depend>mrpt_libnav_headless</depend>`    | mrpt-nav, mrpt-kinematics |
| `<depend>mrpt_libobs_headless</depend>`    | mrpt-obs, mrpt-topography |
| `<depend>mrpt_libopengl_headless</depend>`    | mrpt-opengl, mrpt-img |
| `<depend>mrpt_libposes_headless</depend>`    | mrpt-poses, mrpt-tfest, mrpt-bayes |
| `<depend>mrpt_libros_bridge_headless</depend>`    | mrpt-ros2bridge |
| `<depend>mrpt_libslam_headless</depend>`    | mrpt-slam, mrpt-vision |
| `<depend>mrpt_libtclap_headless</depend>`    | mrpt-tclap |
| `<depend>mrpt_apps_headless</depend>`    | Executable [applications](https://docs.mrpt.org/reference/latest/applications.html): RawLogViewer, rawlog-edit, rawlog-grabber, SceneViewer3D, etc. |
| `<depend>python_mrpt_headless</depend>`    | [pymrpt wrapper](https://docs.mrpt.org/reference/latest/wrappers.html) |

Keep in mind that including one C++ library automatically includes all its dependencies, so you do not need to list them all:

![mrpt_libs](docs/graph_mrpt_libs.png)

## Usage

To get binary packages via `apt install` from the ROS build farm,
install required packages like:

```bash
sudo apt install ros-${ROS_DISTRO}-mrpt-libbase  # or any other as needed
```

Alternatively, if you need to build MRPT from sources (active MRPT developers & testers only),
clone this repo and build with colcon as usual:

```bash
cd ~/ros2_ws/src
git clone --recursive https://github.com/MRPT/mrpt_ros.git
```

## Build status matrix

| Package | ROS 1 Noetic <br/> BinBuild | ROS 2 Humble <br/> BinBuild |  ROS 2 Jazzy <br/> BinBuild | ROS 2 Rolling <br/> BinBuild |
| --- | --- | --- | --- |--- |
| mrpt_apps_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_apps__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_apps__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_apps__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_apps__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_apps__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_apps__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_apps__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_apps__ubuntu_noble_amd64__binary/) |
| mrpt_libapps_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libapps__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libapps__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libapps__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libapps__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libapps__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libapps__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libapps__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libapps__ubuntu_noble_amd64__binary/) |
| mrpt_libbase_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libbase__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libbase__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libbase__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libbase__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libbase__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libbase__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libbase__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libbase__ubuntu_noble_amd64__binary/) |
| mrpt_libgui_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libgui__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libgui__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libgui__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libgui__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libgui__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libgui__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libgui__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libgui__ubuntu_noble_amd64__binary/) |
| mrpt_libhwdrivers_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libhwdrivers__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libhwdrivers__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libhwdrivers__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libhwdrivers__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libhwdrivers__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libhwdrivers__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libhwdrivers__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libhwdrivers__ubuntu_noble_amd64__binary/) |
| mrpt_libmaps_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libmaps__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libmaps__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libmaps__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libmaps__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libmaps__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libmaps__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libmaps__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libmaps__ubuntu_noble_amd64__binary/) |
| mrpt_libmath_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libmath__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libmath__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libmath__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libmath__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libmath__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libmath__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libmath__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libmath__ubuntu_noble_amd64__binary/) |
| mrpt_libnav_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libnav__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libnav__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libnav__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libnav__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libnav__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libnav__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libnav__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libnav__ubuntu_noble_amd64__binary/) |
| mrpt_libobs_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libobs__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libobs__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libobs__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libobs__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libobs__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libobs__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libobs__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libobs__ubuntu_noble_amd64__binary/) |
| mrpt_libopengl_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libopengl__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libopengl__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libopengl__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libopengl__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libopengl__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libopengl__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libopengl__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libopengl__ubuntu_noble_amd64__binary/) |
| mrpt_libposes_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libposes__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libposes__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libposes__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libposes__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libposes__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libposes__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libposes__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libposes__ubuntu_noble_amd64__binary/) |
| mrpt_libros_bridge_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libros_bridge__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libros_bridge__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libros_bridge__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libros_bridge__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libros_bridge__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libros_bridge__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libros_bridge__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libros_bridge__ubuntu_noble_amd64__binary/) |
| mrpt_libslam_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libslam__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libslam__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libslam__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libslam__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libslam__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libslam__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libslam__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libslam__ubuntu_noble_amd64__binary/) |
| mrpt_libtclap_headless | [![Build Status](https://build.ros.org/job/Nbin_uF64__mrpt_libtclap__ubuntu_focal_amd64__binary/badge/icon)](https://build.ros.org/job/Nbin_uF64__mrpt_libtclap__ubuntu_focal_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Hbin_uJ64__mrpt_libtclap__ubuntu_jammy_amd64__binary/badge/icon)](https://build.ros2.org/job/Hbin_uJ64__mrpt_libtclap__ubuntu_jammy_amd64__binary/) | [![Build Status](https://build.ros2.org/job/Jbin_uN64__mrpt_libtclap__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Jbin_uN64__mrpt_libtclap__ubuntu_noble_amd64__binary/) |[![Build Status](https://build.ros2.org/job/Rbin_uN64__mrpt_libtclap__ubuntu_noble_amd64__binary/badge/icon)](https://build.ros2.org/job/Rbin_uN64__mrpt_libtclap__ubuntu_noble_amd64__binary/) |


## Motivation for this repository vs older `mrpt2` package
- Faster build times (for each individual package). It was common to see ROS build farms to time out.
- Finer grained dependencies: ROS users can now specify in their `<depend>` tags a part of MRPT only, not the whole thing.

So, **the ROS package `mrpt2` is obsolete now (Jul, 2024)**.

## License
BSD-3
