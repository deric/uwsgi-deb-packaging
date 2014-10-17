# uwsgi deb package

Custom uwsgi package

usage:
```
./build_uwsgi
```

  * specific version
  ```
  ./build_uwsgi --version 2.0.7
  ```
  * with Python 3.4:
  ```
  ./build_uwsgi --version 2.0.7 --python "python3.4"
  ```

## flags

  * `version` - uwsgi version
  * `patch` - fix version which is appended to real package version, e.g.: `--patch -1` will produce package version `2.0.7-1`
  * `python` - specify Python version which is used for building

## plugins

The main uwsgi building logic is around line 72:

```bash
 $python uwsgiconfig.py --build core
 $python uwsgiconfig.py --build package
 $python uwsgiconfig.py --plugin plugins/python core python32
 $python uwsgiconfig.py --plugin plugins/carbon core

```

## requirements

Package is build using FPM

  - `apt-get install build-essential`
  - some ruby version, e.g. `apt-get install ruby1.9.3`
  - `gem install fpm`
  - `apt-get install python3 python3-dev` if you want python3 support
  - `apt-get install libpcre3 libpcre3-dev` - for perl regexp support
  - `apt-get install libssl-dev` - required for SSL support
  - `apt-get install libjansson-dev` - JSON support

## TODO

  * allow easier uwsgi customization


## uwsgi configuration

uswgi configuration is detected based on libraries installed on your system, make sure that the config matches your expectations:

```
################# uWSGI configuration #################

pcre = True
kernel = Linux
malloc = libc
execinfo = False
ifaddrs = True
ssl = True
zlib = True
locking = pthread_mutex
plugin_dir = /usr/lib/uwsgi
timer = timerfd
yaml = embedded
json = jansson
filemonitor = inotify
routing = True
debug = False
capabilities = False
xml = expat
event = epoll

```
