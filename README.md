# GSFLOW-GRASS-Cannon-River-Example

Example of how to send basic inputs (DEM, climate, and settings in the `ini` file) to GSFLOW-GRASS to help new users get up and running

To run GSFLOW-GRASS using this basic example, do this:

1. **Download `GSFLOW-GRASS-Cannon-River-Example`** (this repository) into a directory of your choice. If you use a compressed option, unzip/untar it.
2. Follow the instructions here (https://github.com/UMN-Hydro/GSFLOW-GRASS) to **get GSFLOW-GRASS, GSFLOW, and GRASS GIS**.
3. **Update `Cannon.ini`** by typing appropriate absolute paths in for the following input variables:
```
gsflow_exe=/PATH/TO/GSFLOW/BINARY/EXECUTABLE/GSFLOW_1.2.0/bin/gsflow
gsflow_path_simdir=/PATH/TO/IO/ROOT/DIR
DEM_file_path_to_import=/PATH/TO/GSFLOW-GRASS-Cannon-River-Example/DEM60m.tif
gisdb=/PATH/TO/YOUR/HOME/DIRECTORY/PROBBALY/grassdata
climate_data_file=/PATH/TO/GSFLOW-GRASS-Cannon-River-Example/Precip_Zumbrota.txt
```
(If you want to keep it easy on yourself, you can use the `
GSFLOW-GRASS-Cannon-River-Example` directory for `/PATH/TO/IO/ROOT/DIR` (or create an "outputs" subdirectory to keep it cleaner).

4. Start **GRASS GIS**, create a new "location", and select the appropriate coordinate system from a georeferenced raster. There is no need to import the DEM at the GUI prompt. Start GRASS in this new "location".
5. **Install packages.** Run from the GRASS command prompt `/YOUR/PATH/GSFLOW-GRASS/domain_builder/install_extensions.sh` or `YOUR/PATH/models/GSFLOW-GRASS/domain_builder/install_extensions.bat` (depending on your OS) to install the GSFLOW-GRASS packages and their dependencies.
6. **Build the GSFLOW domain** Type at the GRASS command prompt `/YOUR/PATH/GSFLOW-GRASS/domain_builder/buildDomainGRASS.py FULL/PATH/TO/GSFLOW-GRASS-Cannon-River-Example/Cannon.ini`. For example, I type the following from the `GSFLOW-GRASS-Cannon-River-Example` directory: `$HOME/models/GSFLOW-GRASS/domain_builder/buildDomainGRASS.py $PWD/CannonAW.ini`. If `Done.` appears at the end, regardless of the warning messages (due to Shapefile truncation of fields, etc.), you have successfully set up your domain. There will now be a set of folders that have the outputs of the domain builder, especially the tables of HRUs, segments, etc., which are the inputs to run GSFLOW.
7. **Build final input files and run GSFLOW!** Either inside or outside of GRASS, type at the command prompt (in this example, from the `GSFLOW-GRASS-Cannon-River-Example` directory): `$HOME/models/GSFLOW-GRASS/Run/goGSFLOW.sh $PWD/CannonAW.ini`.

If no errors are thrown, you've succeeded and can now look at your outputs, including by using the visualization scripts explained in the `README.md` for https://github.com/UMN-Hydro/GSFLOW-GRASS.

This example is slightly different from that in the paper (reference below) in order to reduce resolution, speed compute time, and reduce storage on GitHub. The main change is that the flow-routing grid cells are 60 meters on each side (approximately) and the MODFLOW grid cells are approximately 1200 m on each side. In addition, I have changed the location of the pour point slightly and include the updated code that allows the basin to end precisely at the desired pour point.

When you use GSFLOW-GRASS, please cite:

**Ng, G.-H.C., Wickert, A.D., Somers, L.D., Saberi, L., Cronkite-Ratcliff, C., Niswonger, R.G., and McKenzie, J.M., 2018, [GSFLOW-GRASS v1.0.0: GIS-enabled hydrologic modeling of coupled groundwater–surface-water systems](https://www.geosci-model-dev-discuss.net/gmd-2017-321/): *Geoscientific Model Development*, doi:10.5194/gmd-11-4755-2018.**
