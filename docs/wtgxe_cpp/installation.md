---
layout: default
title: Installation
parent: WtGxE C++ manual
grand_parent: Genome-wide gene-environment interaction (GxE) studies
nav_order: 1
permalink: /docs/wtgxe_cpp/installation.html
has_toc: true
---

# Install the WtGxE C++ program

The [WtGxE package](https://github.com/YuzhuoMa97/WtGxE)
uses a C++17 compiler. Eigen headers are bundled with the source, and the
analysis executable runs without an R or Python session. Preserve the licenses
and incorporated-source notices supplied in the package.

## Retrieve the source

With Git installed and an account that has repository access:

```sh
git clone --branch main --single-branch https://github.com/YuzhuoMa97/WtGxE.git
cd WtGxE
```

Alternatively, download the `main` branch from GitHub and open the downloaded
source root. For repository access or installation assistance, contact
[yuzhuoma@amss.ac.cn](mailto:yuzhuoma@amss.ac.cn).

## Build with CMake

From the WtGxE source root, use source, build, and install paths containing
ASCII characters with an existing CMake and C++17 toolchain:

```sh
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTING=OFF -DWTGXE_BUILD_SIMULATION=OFF
cmake --build build --config Release --parallel 1
cmake --install build --config Release --prefix install
```

Run `install/bin/wtgxe` on a Unix-like system, or
`install/bin/wtgxe.exe` on Windows. A multi-configuration build may place the
build-tree executable under `build/Release/`.

```sh
./install/bin/wtgxe --version
./install/bin/wtgxe --help
```

For Windows PowerShell, the corresponding commands are
`./install/bin/wtgxe.exe --version` and
`./install/bin/wtgxe.exe --help`.

## Direct g++ build

An existing compatible g++ can compile the program directly from its source
root. Keeping filenames relative and ASCII also provides the locally exercised
route for a project path containing Chinese characters.

```sh
g++ -std=c++17 -O2 -Iinclude -Ivendor -Ithird_party/eigen src/cli/main.cpp src/wtgxe/wtgxe.cpp vendor/io/sparse_grm.cpp -o wtgxe
./wtgxe --version
./wtgxe --help
```

In PowerShell, use `-o wtgxe.exe`, followed by `./wtgxe.exe --version` and
`./wtgxe.exe --help`. In the worked example, replace `./wtgxe` with the actual
executable path produced by your build. Keep the working directory at the
WtGxE source root so its example paths resolve correctly.

## Optional package checks

Developers can enable the packaged tests in a separate build directory:

```sh
cmake -S . -B build-tests -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTING=ON -DWTGXE_BUILD_SIMULATION=OFF
cmake --build build-tests --config Release --parallel 1
ctest --test-dir build-tests -C Release --output-on-failure
```

The retained local qualification passed nine CTest entries. These checks cover
engineering behavior; the simulation documentation separately evaluates type
one error rate and power.

Next: [run the worked example](quickstart.html).
