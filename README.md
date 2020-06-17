# monetdbe
MonetDBe - the Python embedded MonetDB

https://github.com/monetdBSolutions/MonetDBe-Python/

# requirements

For binary wheel installation you need:

 * Linux or OSX 10.13+
 * pip >= 19.3
 * Python >= 3.6

For non-binary wheel installation (Windows) you also need to have MonetDB installed.


# install

you can install monetdbe from pypi using:
```
# pip install monetdbe
```

On supported platforms, this will download and install the Binary wheel, otherwise a source compile is started.

# compile

You need a recent MonetDB installation with INT128 on and py3integration off: 
```
$ hg clone hg://dev.monetdb.org/hg/MonetDB
$ cd MonetDB
$ mkdir build
$ cd build
$ cmake .. -DCMAKE_INSTALL_PREFIX=<monetdb_prefix> -DINT128=ON -DPY3INTEGRATION=OFF
$ make install
```

You can also compile monetdbe from the source folder:
```
$ git clone https://github.com/MonetDBSolutions/MonetDBe-Python/
$ cd MonetDBe-Python
$ pip install .
```

You need to have MonetDB available on the default search paths, if it is
installed in a different location you need to specify `CFLAGS`:
```
CFLAGS="-I<monetdb_prefix>/include/monetdb -L<monetdb_prefix>/lib/monetdb" pip install .
```
 
# development

![Run test suite and build wheels](https://github.com/MonetDBSolutions/MonetDBe-Python/workflows/Run%20test%20suite%20and%20build%20wheels/badge.svg)


You can use pytest to run the test suite from the source checkout:
```
$ python3 -m venv venv
$ source venv/bin/activate
$ pip install -e ".[test,doc]"
$ pytest
```

If MonetDB is installed in a different location, set the LD\_LIBRARY\_PATH environment variable first:
```
$ export LD_LIBRARY_PATH=<monetdb_prefix>/lib:<monetdb_prefix>/lib/monetdb5
```
