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

## plugins

The main uwsgi building logic is around line 72:

```bash
 $python uwsgiconfig.py --build core
 $python uwsgiconfig.py --build package
 $python uwsgiconfig.py --plugin plugins/python core python32
 $python uwsgiconfig.py --plugin plugins/carbon core

```

## TODO

  * allow easier uwsgi customization
