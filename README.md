# GSFLOW-GRASS-Cannon-River-Example

Example of how to send basic inputs (DEM, climate, and settings in the `ini` file) to GSFLOW-GRASS to help new users get up and running

To run GSFLOW-GRASS using this basic example, do this:

1. Follow the instructions here (https://github.com/UMN-Hydro/GSFLOW-GRASS) to get GSFLOW-GRASS, GSFLOW, and GRASS GIS.
2. Update `Cannon.ini` by typing appropriate absolute paths in for the following input variables:
```
gsflow_exe=/PATH/TO/GSFLOW/BINARY/EXECUTABLE/GSFLOW_1.2.0/bin/gsflow
gsflow_path_simdir=/PATH/TO/IO/ROOT/DIR
DEM_file_path_to_import=/PATH/TO/GSFLOW-GRASS-Cannon-River-Example/DEM60m.tif
gisdb=/PATH/TO/YOUR/HOME/DIRECTORY/PROBBALY/grassdata
climate_data_file=/PATH/TO/GSFLOW-GRASS-Cannon-River-Example/Precip_Zumbrota.txt
```
(If you want to keep it easy on yourself, you can use the `
GSFLOW-GRASS-Cannon-River-Example` directory for `/PATH/TO/IO/ROOT/DIR` (or create an "outputs" subdirectory to keep it cleaner).

3. Start GRASS GIS, create a new "location", and select the appropriate coordinate system from a georeferenced raster. There is no need to import the DEM at the GUI prompt. Start GRASS in this new "location".
4. Run from the GRASS command prompt `/YOUR/PATH/GSFLOW-GRASS/domain_builder/install_extensions.sh` or `YOUR/PATH/models/GSFLOW-GRASS/domain_builder/install_extensions.bat` (depending on your OS) to install the GSFLOW-GRASS packages and their dependencies.
5. Type at the GRASS command prompt `/YOUR/PATH/GSFLOW-GRASS/domain_builder/buildDomainGRASS.py FULL/PATH/TO/GSFLOW-GRASS-Cannon-River-Example/Cannon.ini`. For example, I type the following from the `GSFLOW-GRASS-Cannon-River-Example` directory: `$HOME/models/GSFLOW-GRASS/domain_builder/buildDomainGRASS.py $PWD/CannonAW.ini`.
