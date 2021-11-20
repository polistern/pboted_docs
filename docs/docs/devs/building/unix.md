# Building on Unix systems

**Supported systems:**

* GNU/Linux
  - [Debian/Ubuntu](#debian-ubuntu) (with packaging)

Make sure you have all required dependencies for your system successfully installed.
See [this](requirements.md) page for common requirements.

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

## CMake Options

Available CMake options(each option has a form of `-D<key>=<value>`, for more information see `man 1 cmake`):

* `CMAKE_BUILD_TYPE` build profile (Debug/Release, default: no optimization or debug symbols)
* `WITH_STATIC`      build static versions of library and i2pd binary (default: OFF)

Also there is `-L` flag for CMake that could be used to list current cached options:

```
  cmake -L
```

## Debian/Ubuntu:

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
