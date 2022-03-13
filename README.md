# Gait_Analysis_RPA

Robotics Perception and Action/n
Project on Gait Analysis and Gait Phases Detection with Laser Rangefinder/n
Students: Giacomo Mutti, Mattia Sartori
Supervisors: prof. Mariolino De Cecco, Luca Maule, Valentina Nardon

The project aims at detecting the phases of the gait cycle of a person walking with the 
support of an autonomous walker. The detection is possible by analyzing the measures taken 
with a laser rangefinder RPLidar A1 M8 positioned in front of the person at a height
just under the knees.

First, the measurements are taken with the revised "ultra_simple" code provided in the 
rplidar sdk.
Then we adjust the .txt files deriving from the dump of the measurements by adding the 
number of the acquisiton rounds.
We analyse data and extract features that are meaningful of the gait phases that we want 
to detect:
Phases (classes):
   1 - double support left forward
   2 - right swing phase
   3 - double support right forward
   4 - left swing phase
   5 - standing
The computed features can be used, after manual labelling, for model training. 
For manual labelling we comapred the plots of the extracted features and the videos
taken during the experiments.
In the project we used the Matlab toolbox Classification Learner since it is easy and 
simple to use and it allows to export the C/C++ code underlying some models.
At the end we used the model to make automatic detection.

Brief description of files in the repository:

- adjust_data.m : read the .txt files generated by the dump of the measurements and 
  	 	  adjust the format by adding the number of round (revolutions of the lidar)

- circ_fit.m : function that performs the best circumference fitting for the points of 
	       each leg

- gait_analysis.m : code for extracting the features from the data. Simulates realtime
	 	    acquisition and features extraction.

- gait_phase_detection.m : code that simulates the realtime features extraction and the 
			   detection of the gait phase at each acquisition round.

Note: the last two code files can be merged in a single file to be used in the realtime
      application. The structure that we gave to the files is useful for an offline
      analysis and for the model training. However, the core parts of the code can be 
      directly applied in the C++ code for a realtime gait phases detection.


Brief description of folders in the repository: 

- data_lab : folder containing the original .txt dump of the measurements

- data_lab_adj : folder containing the adjusted .txt files. Only some of the files
		 in data_lab have been adjusted and used for feature extraction and 
		 manual labelling because we had a video reference.

- feat_labelled : folder containing the .txt files of the labelled data of the single
		  acquisition experiments and the .txt file with all the labelled data
		  put together to form the complete "supervised" dataset.

- phase_img : images of the five detected gait phases to show on the plot.
