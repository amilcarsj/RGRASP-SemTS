# RGRASP-SemTS

The Reactive Greedy Randomized Adaptive Search Procedure for semantic Semi-supervised Trajectory 
Segmentation (RGRASP-SemTS) is an algorithm that segments trajectories combining a limited user 
labeled dataset with a low number of input parameters and no predefined segmenting criteria.
    
When using this code, please refer to: 

Amilcar Soares Junior, Valeria Cesario Times, Chiara Renso, Stan Matwin, and Lucídio AF Cabral. 
"A semi-supervised approach for the semantic segmentation of trajectories." 
In 2018 19th IEEE International Conference on Mobile Data Management (MDM), pp. 145-154. IEEE, 2018.

[Original published version](https://ieeexplore.ieee.org/abstract/document/8411271/) 

DOI: [https://doi.org/10.1109/MDM.2018.00031](https://doi.org/10.1109/MDM.2018.00031)

[Author version](https://www.researchgate.net/publication/324841537_A_Semi-Supervised_Approach_for_the_Semantic_Segmentation_of_Trajectories)


## Preparing the data

RGRASP-SemTS requires the trajectory data as a numpy multidimensional matrix with the following: 

1. A trajectory dataset to segmented and labeled. 

\[trajectory_id, longitude, latitude, time_collected, point_feature_1, ..., point_feature_n\] 

where, 
	*_trajectory_id_ (float) is an identifier for the trajectory*
	*_longitude_ (float) is the longitude for a given trajectory point*
	*_latitude_ (float) is the latitude for a given trajectory point*
	*_time_collected_ (string) is a string with the timestamp in the 
		following format 'YYYY-MM-DD hh:mm:ss'*
	*_point_feature(_n) (float) a vector with all point features of the trajectory*

1.  A small labeled trajectory dataset, with an extra column for the class for each trajectory point.
\[trajectory_id, longitude, latitude, time_collected, point_feature_1, ..., point_feature_n, semantic_class\]

where, 
	*_semantic_class (string) is the last column containing a semantic class as a float value.*

## Running the algorithm 

RGRASP-SemTS uses the following input parameters: 

1. A _seed_ (int), for reproducing experiments results.
1. A _reactive_proportion_ (float), from 0. -- 1., for updating gradually the probabilities
   of selecting parameters min_time and alpha values. 
1. A lists_size (int), for defining the size of the lists for parameters alpha and min_time values
1. A value for _max_iterations_ (int) with the number of max iterations for building and optimizing solutions
1. A _max_value_ (float), with the maximal similarity value possible between two trajectory points. 
	Use the square root of the number of trajectory features as a default
1. A segments_feats_list \[(string),...\] *(optional)* with a list with all segment features attributes 
   to be computed. At this version only the percentiles \'p5\',\'p25\',\'p50\',\'p75\' and \'p95\' 

## Jupyter notebooks examples with two datasets are included in this package, please check  the files RunRGRASP-SemTS(Fishing).ipynb and RunRGRASP-SemTS(Hurricanes).ipynb ##
