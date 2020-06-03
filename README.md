# iSOSIA
Ice sheet modelling

How to run iSOSIA models?

iSOSIA works with two main folders:

 - mfiles: contains all the Matlab files that enables (i) to create input files for iSOSIA, and (ii) to show results ('show' function).
 - source: contains all the source files (i.e. the core of iSOSIA).

To be able to run an iSOSIA model, the files in the 'source' folder need to be compiled first. This is done by the command file 'gmake' in the source folder.
To run such a command you need the gcc compiler. 
Within a command prompt, go to '.\spm-3.4.7b\source' and write '.\gmake'. The command will be lauched and iSOSIA c files will be compiled.

Once iSOSIA is compiled, you can then create input files for an iSOSIA model.
This is done with Matlab.
For simplicity, add the 'mfiles' folder to the Matlab search path. You can do this by the following set of commands:

	- Within the Matlab interface, go to 'HOME', then click on 'Set Path'. A new interface should pop-up.
	- Click on 'Add Folder...', and go to the location of the 'mfiles' folder in your disk. 
	- Select the folder and click on 'Select a folder'
	- Now, the 'mfiles' folder should appears in the list of folders within the 'Set Path' interface of Matlab.
	- In the bottom-right of this panel, click on 'Save' to save the path.
	- Close the panel.

Now you are able to call the Matlab functions in 'mfiles' to create input files for iSOSIA.

--------------------- Input files for iSOSIA -------------------

The setting of input files is done with the function 'template.m' within the model folder provided (e.g. Tied_Uniform).
Go to the model folder and open the 'template.m' file. You can see inside, all the parameters that can be set to run an iSOSIA model.
Comments are provided to define the parameters.

To be able to write the input files (i.e. in the 'input' folder), corresponding to the set of parameters values, simply call the 'template' function in the Matlab command
prompt: template.
This will generate two figures, the model topography and the defined initial mass balance, and the input files.

Other files are in the model folder:
	- cmap_jet.mat: the colorbar to apply on the figures of results
	- include.mat: the Tiedemann glacier catchment mask
	- Tiedemann.mat: the topography of the Tiedemann glacier area (100 meters resolution)

--------------------- Run iSOSIA models ------------------------

Once the input files are created, you can run iSOSIA for the corresponding model. 
To run iSOSIA:
	- Go to the iSOSIA folder --> spm.3.4.7b\source 
	- Then write '.\spm the\location\of\the\model\folder &'
	- press Enter twice
	- iSOSIA is running in the background
	
Once iSOSIA finished to run, the output files are located in the folder 'output' within the folder of the model. 

---------------- Show results and compute SPDFs ----------------

You can visualize many outcomes from an iSOSIA model by calling the Matlab function 'show' in the Matlab command prompt. All outcomes are listed in the file 'loaddata.m' in the 'mfiles' folder. Here, some examples of calling the 'show' function to visualize the results:

	- See the ice thickness spatial distribution of the last output file: show('file','latest','data','ice').
	- See the total quarrying of the output file 30 within a specified range: show('file',30,'data','quarrying', 'dlim', [0 60]).
	- See the sediment particles density distribution of the last output file: show('file','latest','data','particles')


The computation of detrital age distributions (SPDFs) is done with the function 'dethermo' in the 'mfiles' folder. This function needs, at most, five parameter values to be specified:
	- 'AgeElev': The thermochronological age-elevation to consider (1 for the AFT system, and 2 for the AHe system).
	- 'Ssite': The sampling strategy to consider (1 to sample across the frontal moraine, 2 to sample the local regions in the frontal moraine, 3 and 4 for the models M16 and M17).
	- 'hillslope': to consider only particles originating from hillslopes in the sampling process
	- 'glacial': to consider only particles originating from glaciers in the sampling process.
	- 'pulse': to consider models with only one pulse of particles production.
	- 'showpart': to show the spatial distribution of the particles at the end of the run.

For each iSOSIA model, the value of the parameters to set are described in the head of the file 'dethermo.m'. For example:
 - Compute the detrital age distribution from the model Tied_UniformPart for the AHe data --> dethermo('AgeElev',2,'Ssite',1,'pulse')
 - Compute the detrital age distribution from the model Tied_Uniform by considering only particles originate fron the glacial sources for the AFT data --> dethermo('AgeElev',1,'Ssite',1,'glacial')
 
------ Transient arrival of particles in the frontal moraine ---

To show the transient arrivals of particles within the frontal moraine and the transfer times, simply call the function 'get_particles' in the Matlab command prompt. The particles transfer times shown in Fig. 10 are from the model 'Tied_UniformPart'.
