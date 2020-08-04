
# Portland Metro Area

This project is configured to download/prepare/build a complete Pelias installation for Portland, Oregon.

It is intended as an example for other projects, feel free to copy->paste these files to a new project directory to kick-start your own project.

# Setup

Please refer to the instructions at https://github.com/pelias/docker in order to install and configure your docker environment.

The minimum configuration required in order to run this project are [installing prerequisites](https://github.com/pelias/docker#prerequisites), [install the pelias command](https://github.com/pelias/docker#installing-the-pelias-command) and [configure the environment](https://github.com/pelias/docker#configure-environment).

Please ensure that's all working fine before continuing.

# Run a Build

To run a complete build, execute the following commands:

```bash
pelias compose pull
pelias elastic start
pelias elastic wait
read -r -p "Please run create_index.http to create index" key
read -r -p "Press any key to continue..." key
pelias download all
pelias prepare all
pelias import all
pelias download geonames
pelias import geonames
pelias compose up
pelias test run
```

# Make an Example Query

You can now make queries against your new Pelias build:

http://localhost:4000/v1/search?text=pdx
