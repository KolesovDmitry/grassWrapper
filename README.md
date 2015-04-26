# grassWrapper

feedgrass: activate or create GRASS GIS database and execute given commands.

The script executes GRASS commands without explicit GRASS starting.


## Example usage:

### Use commands with -e option:

Open HOME/GRASSDATA/mylocation/PERMANENT and execute commands:

```
  $ feedgrass -g /opt/grass70/ -d ~/GRASSDATA/ -l mylocation -e "g.region -p; g.list rast"
```
(There GRASS GIS is installed to `/opt/grass70/` directory).


### Use stdin:

You can pass commands using stdin.

Pipe examples:
```
  $ echo "g.region -p; g.list rast" | feedgrass -g /opt/grass70/ -d ~/GRASSDATA/ -l test -e \-
  $ echo "g.region -p; v.random tmp n=100" | feedgrass -g /opt/grass70/ -d ~/GRASSDATA/ -l test
```

Redirection example:
```
  $ feedgrass -g /usr/lib/grass70 -d /tmp/GRASS -l LOC2  -t Const.tif < myscript
```

### Create GRASS GIS DATABASE:

You can create new location, mapset or database. In this case you need provide a
georefernced file. New location (mapset) will be created to conform the coordinate
system of the file.

```
  $ feedgrass -g /usr/lib/grass70 -d /tmp/GRASS \
    -l mylocation  -t my_raster.tif \
    -e 'r.in.gdal input=my_raster.tif output=raster; r.univar raster'
```
