# Installing

## Debian/Ubuntu

You can install binary packages from the [latest release page](https://github.com/polistern/pboted/releases/latest).

## Building from source

### Requirements

In general, for building **pboted** you need several things:

* compiler with c++17 support (for example: gcc >= 5, clang)
* cmake >= 3.7
* mimetic >= 0.9.8
* boost >= 1.62
* openssl library
* zlib library (openssl already depends on it)

## Building on UNIX-like systems

**Supported systems:**

* GNU/Linux
    - [Debian/Ubuntu](#debian-ubuntu) (with packaging)
    - CentOS/RedHat

Make sure you have all required dependencies for your system successfully installed.
See for common requirements in [this](#requirements) section.

- Clone repository:

```
git clone https://github.com/polistern/pboted.git
cd pboted
git submodule update --init
```

- Build:

```
cd build
cmake <cmake options> . # see "CMake Options" section below
make                    # you may add VERBOSE=1 to cmdline for debugging
```

- Put binary to `/usr/sbin/`

```
sudo cp pboted /usr/sbin/pboted
```

### CMake Options

Available CMake options(each option has a form of `-D<key>=<value>`, for more information see `man 1 cmake`):

* `CMAKE_BUILD_TYPE` build profile (Debug/Release, default: no optimization or debug symbols)
* `WITH_STATIC`      build static versions of library and i2pd binary (default: OFF)

Also there is `-L` flag for CMake that could be used to list current cached options:

```
  cmake -L
```

### Debian/Ubuntu:

!!! note "Note"

    Tested with Debian 10 and Ubuntu 20.04.

You will need a compiler and other tools that could be installed with `build-essential` and `debhelper` packages:

```
sudo apt-get install git cmake build-essential debhelper
```

Also you will need a bunch of development libraries:

```
sudo apt install \
  libboost-date-time-dev \
  libboost-filesystem-dev \
  libboost-program-options-dev \
  libboost-system-dev \
  libboost-thread-dev \
  libmimetic-dev \
  libssl-dev \
  pkg-config \
  zlib1g-dev
```

You may also build deb-package with the following:

```
  sudo apt-get install fakeroot devscripts dh-apparmor
  cd pboted
  debuild --no-tgz-check -us -uc -b
```
