# uwsgi deb package

Custom uwsgi package

usage:
```
./build_uwsgi
```

specific version

```
./build_uwsgi --version 2.0.7
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
  - `apt-get install python3` if you want python3 support
  - `apt-get install libpcre3 libpcre3-dev` - for perl regexp support
  - `apt-get install libssl-dev` - required for SSL support
  - `apt-get install libjansson` - JSON support

## TODO

  * allow easier uwsgi customization
