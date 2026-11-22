# mathplot_config

This contains some [mathplot](https://github.com/sebsjames/mathplot) examples which use `sm::config` from [maths_config](https://github.com/sebsjames/maths_config).

## Dependencies

If you are using Debian or Ubuntu, the following `apt` command should
install the mathplot dependencies.

```bash
sudo apt install build-essential cmake git ninja-build  \
                 freeglut3-dev libglu1-mesa-dev libxmu-dev libxi-dev \
                 libglfw3-dev libfreetype-dev clang-20 clang-tools-20
```

On Arch Linux the following command should install dependencies:
```bash
sudo pacman -S vtk lapack blas freeglut glfw-wayland
# Plus install clang20
```

On Fedora Linux, the following command should install the required dependencies
```bash
sudo dnf install cmake libglvnd-devel mesa-libGL-devel glfw-devel freetype-devel
# Plus install clang20
```

If you're building on a Mac, you can refer to the [Mac
README](https://github.com/sebsjames/mathplot/blob/main/README.build.mac.md#installation-dependencies-for-mac) in mathplot
for help. You only need to obtain and build
[glfw3](https://github.com/sebsjames/mathplot/blob/main/README.build.mac.md#glfw3);
OpenGL and Freetype should already be installed by default.

## Building

To build and run the example:

```bash
# Clone this example
git clone git@github.com:sebsjames/mathplot_config

# Bring in the submodules - sebsjames/mathplot, sebsjames/maths,
# sebsjames/maths_config and nlohmann/json Your project will need
# these submodules too. They don't HAVE to be submodules, you can just
# copy or symlink the codebases if you prefer.

cd mathplot_config
git submodule init
git submodule update

# Build programs in a 'build' directory
mkdir build
cd build
CC=clang-20 CXX=clang++-20 cmake .. -GNinja
ninja
```
