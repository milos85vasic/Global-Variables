# Global Variables

Simple native application for reading global variables from global JSON configuration file.

## Ho wto use it

Application can be used like this:

`$ vars --source=/path/to/json/file.json CATEGORY.CATEGOY.CATEGORY.KEY`

Where we have passed the source JSON file and variable path. 

Or:

`$ vars CATEGORY.CATEGOY.CATEGORY.KEY`

Where default JSON path is: 

`/root/Server/Variables/Configuration.json`

## Building the application

To build application perform the following steps:

-  cd into project directory
- mkdir build
- cd build
- cmake ..
- make
- make install

### Building requirements

The following dependencies needed in order to be able to build the application:

- C++ installed for the platform
- Cmake, Make and proper C++ compiler
- Boost library version >= 1.71.0.