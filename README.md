# grassWrapper

feedgrass: activate or create GRASS GIS database and execute given commands.

The script executes GRASS commands without explicit GRASS starting. 


## Example usage:

### Use commands with -e option:
  $ feedgrass -g /opt/grass70/ -d ~/GRASSDATA/ -l mylocation -e "g.region -p; g.list rast"

### Use stdin:
  $ echo "g.region -p; g.list rast" | feedgrass -g /opt/grass70/ -d ~/GRASSDATA/ -l test -e \-
  $ echo "g.region -p; v.random tmp n=100" | feedgrass -g /opt/grass70/ -d ~/GRASSDATA/ -l test
