Instructions for running computational experiments used in the paper:
"Production and transport of supraglacial debris: Insights from cosmogenic 10Be and numerical modeling, Chhota Shigri Glacier, Indian Himalaya" by D. Scherler & D. L. Egholm

This github release contains 1) iSOSIA (version spm-3.4.3) for running the experiments, 2) four model folders (Uniform, Slope, Frost_AT, and Frost_LST), and 3) grids with DEMs and other geo-referenced information.

To compile iSOSIA: go to folder spm-3.4.3/source and use a C-compiler to compile spm.c. If you have gcc installed you can use the compile script gmake. The Makefile may also be useful, but you may need to make adjustments to fit your compiler.

To build input files: Open MATLAB and go to a model folder (Uniform, Slope, Frost_AT, or Frost_LST). Add folder spm-3.4.3/mfiles to your MATLAB path. Similarly you need a path to TopoToolbox. Run MATLAB script template.m

To start iSOSIA: call the compiled version of spm with the path to a model folder as input: For example: ./spm ~/models/Uniform

To study model output: Open MATLAB and go to model folder. Use spm-3.4.3/show.m to visualize output.

