# dropGrowth

Simulates (water)drop growing by condesation and accretion effect and the downwards movement through gravitation. This movement is not generated by gravitation, but simply follows a function depending on the drop size.
Start state is a randomly uniform distributed area of very small droplets (around 2E-6 meters in diameter), where as their size is normal distributed. Parameters of this small program can be set in the src/global.h definition. The OpenCV functionality can also be turned off there, which is needed to visualize the simulation environment and create a small video snip. No logs are produced, some state informations are printed to stdout. Starting parameters are not built in yet.

## Build Instructions

## Dependencies
OpenCV v4 (can be disabled in src/global.h; for older versions the source code may be adopted)

### Configure
Use a out-of-tree build to not pollute your checkout:
```
mkdir build
cd build
```

Depending if you want to use a debug or release build, either run

```
# debugging
cmake -GNinja -DCMAKE_BUILD_TYPE=Debug -DSANITIZE_ADDRESS=On ..
```

or

```
# profiling
cmake -GNinja -DCMAKE_BUILD_TYPE=RelWithDebInfo ..
```

or

```
# public release
cmake -GNinja -DCMAKE_BUILD_TYPE=Release ..
```

### Actual Build
```
ninja
```
Usually, you do NOT need to re-run cmake.

### Run
```
./dropgrowth
```

## Developer Notes
"Height" in the simulaiton is inverted! If the height has a value as defined in ENVIRONMENT_HEIGHT, it means the drop is at the ground (real world). Height = 0 in the program means the drop is at height = ENVIRONMENT_HEIGHT in the real world.

## Auto-Format
```
cd build
ninja format
```

## TODO
- performance improvements (i.e. QuadTree instead of bruteforce)
