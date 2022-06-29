# Сборка на UNIX-подобных системах

**Поддерживаемые системы:**

* GNU/Linux
    - [Debian/Ubuntu](#debian-ubuntu) (с созданием пакета)
    - CentOS/RedHat

Убедитесь, что все требуемые зависимости для Вашей системы установлены.
Ознакомтесь с зависимостями в [этом](requirements.md) разделе.

- Клонируйте репозиторий:

```
git clone https://github.com/polistern/pboted.git
cd pboted
git submodule update --init
```

- Скомпилируйте:

```
cd build
cmake <cmake options> . # смотри секцию "CMake Options" ниже
make                    # для отладки можно добавить VERBOSE=1
```

- Поместите исполняемый файл в директорию `/usr/sbin/`

```
sudo cp pboted /usr/sbin/pboted
```

## Опции CMake

Доступные опции CMake (каждая опция имеет вид `-D<key>=<value>`, больше информации в `man 1 cmake`):

* `CMAKE_BUILD_TYPE` тип сборки (Debug/Release, по умолчанию: без оптимизаций и отладки)
* `WITH_STATIC`      статичная сборка pboted (по умолчанию: OFF)

Для CMake доступен флаг `-L` для просмотра текущих опций сборки:

```
  cmake -L
```

## Debian/Ubuntu:

!!! note "Note"

    Проверено на Debian 10 и Ubuntu 20.04.

Вам необходимы компилятор и другие утилиты, которые могут быть установлены с пакетами `build-essential` и `debhelper`:

```
sudo apt-get install git cmake build-essential debhelper
```

Также вам понадобятся библиотеки разработки:

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

Доступна возможность собрать DEB пакет самостоятельно:

```
  sudo apt-get install fakeroot devscripts dh-apparmor
  cd pboted
  debuild --no-tgz-check -us -uc -b
```
