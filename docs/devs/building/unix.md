# Building on Unix systems

**Supported systems:**

* GNU/Linux
  - Debian / Ubuntu (with packaging)

## CMake Options


## Debian/Ubuntu:

_Tested with Debian 10 and Ubuntu 20.04._

- Install development libraries and tools:

```
sudo apt install git cmake build-essential zlib1g-dev libssl-dev \
libboost-filesystem-dev libboost-system-dev libboost-program-options-dev \
libboost-date-time-dev libboost-thread-dev libmimetic-dev
```

- Clone repository:

```
git clone https://github.com/polistern/pboted.git
cd pboted
git submodule update --init
```

- Build:

```
cd build
cmake -DCMAKE_BUILD_TYPE=Release
make
```

- Put binary to `/usr/sbin/`

```
sudo mv pboted /usr/sbin/pboted
```