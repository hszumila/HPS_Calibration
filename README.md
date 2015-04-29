# HPS_Calibration
Author: Holly Szumila-Vance
Email: hvanc001@odu.edu

This contains the scripts for running the cosmic calibration for the HPS
Ecal. 

In order to run the cosmic calibration, one must first have the evio files
converted to ROOT files containing the raw adc spectra for each crystal. This
still needs to be added here.

The raw data needs to be analyzed using a strict geometric cut, loose
geometric cut, or counting cut. The first is recommended, but the latter two
are useful when there are bad crystals. A strict geometric cut requires that
there is no hit above threshold to the left and right crystals but there must
be a hit above and below. A loose geometric cut requires that there can be no
hit in the left and crystals but there must be a hit in a crystal above or
below. A counting cut requires that any two crystals in the same column have a
hit above threshold and not the ones to the left and right. 

Make a folder called cosmicFiles with the raw root input files. Make a folder
called convolFit to contain the fits to each crystal in getGain(). getGain()
will also output two color plots showing the gain values and the total hits in
that crystal above threshold for the run files used. 

To use the geometric cut, one can run cosmicAnalysis in root by typing:
.L cosmicAnalysis.C++
rawGeoCut(0) //Option 0 is strict, option 1 is loose
getGain()

To use the counting cut, one can run cosmicAnalysis in root by typing:
.L cosmicAnalysis.C++
rawCountingCut()
getGain()

The output file with the crystals and gains must then be converted for use in
the database or daq. (Still needs to be added here as a howto)

The files in the folder "dependency" must be added to the root path compiler
to access.
