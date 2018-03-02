# CHEME7770_HomeWork2

## Instructions to Read the code
1. The code for Problem 2 are contained in src folder
2. 4 new functions have been added to the datadictionary

### The first function is : function maximize_cellmass_aerobic_data_dictionary(time_start,time_stop,time_step)
1. This basically checks for cell growth in aerobic conditions with the boolean regulatory constraints.
2. The reaction for ATP maintainance has been enabled by setting : default_flux_bounds_array[20,1:2] = 7.6
3. A new array called aerobic array has been created which contains 142 rows of ones. This means that all the reactions are enabled.
4. The boolean rules have been implemented for the respective required reactions following table 16 and table 17 given in ecosal paper.
5. oxygen,nh4,pi,glc_D,PYK,PFK,GLCpts, ME1,ME2 and Biomass have been set to 1 to allow the aerobic reactions. 
6. The rule for CRPnoGLC that was given in the paper has been modified in the code to account for the formation of pyruvate kinase to enable its role in cell growth.
7. the glucose uptake rate has been set to 10 following the paper by setting lb of glc_D in exchange array as -10.
8. It is seen that pi(phosphate) plays an important role in cell growth. by updating the lb bound of pi to -3.2(pi being used) in the exchange array will give the required objective value/growth rate of 0.86. pi is a major bifurcation parameter.
9. Further the updated aerobic array multiplies element wise with the default_bounds_array to give required results.

### The second function is : function maximize_cellmass_aerobic_unreg_data_dictionary(time_start,time_stop,time_step)
1. This basically checks for cell growth in aerobic conditions without the boolean regulatory constraints.
2. The reaction for ATP maintainance has been enabled by setting : default_flux_bounds_array[20,1:2] = 7.6
3. the glucose uptake rate has been set to 10 following the paper by setting lb of glc_D in exchange array as -10.
4. It is seen that pi(phosphate) plays an important role in cell growth. by updating the lb bound of pi to -3.2(pi being used) in the exchange array will give the required objective value/growth rate of 0.86
9. Solve.jl runs for this function to give the same objective value which verifies that the model is working properly because the reaction shut off by the boolean constraints have no role in the optimal flux and hence will not change the growth rate of ecoli.

### The third function is : function maximize_cellmass_anaerobic_data_dictionary(time_start,time_stop,time_step)
1. This basically checks for cell growth in anaerobic conditions with the boolean regulatory constraints.
2. The reaction for ATP maintainance has been enabled by setting : default_flux_bounds_array[20,1:2] = 7.6
3. A new array called aerobic array has been created which contains 142 rows of ones. This means that all the reactions are enabled.
4. The boolean rules have been implemented for the respective required reactions following table 16 and table 17 given in ecosal paper.
5. Acetate,nh4,pi,lac_D,glc_D,PYK,PFK,GLCpts, ME1,ME2 and Biomass have been set to 1 to allow the aerobic reactions. 
6. The rule for CRPnoGLC that was given in the paper has been modified in the code to account for the formation of pyruvate kinase to enable its role in cell growth.
7. the glucose uptake rate has been set to 10 following the paper by setting lb of glc_D in exchange array as -10.
8. It is seen that etoh(phosphate) plays an important role in cell growth. by updating the ub bound of pi to 0.154(etoh being produced) in the exchange array will give the required objective value/growth rate of 0.21. etoh is a major bifurcation parameter.
9.The following reactions have been shut due to absence of oxygen
   default_flux_bounds_array[56,1:2] = 0
	 default_flux_bounds_array[57,1:2] = 0
	 default_flux_bounds_array[103,1:2] = 0
	 default_flux_bounds_array[104,1:2] = 0
10. Further the updated aerobic array multiplies element wise with the default_bounds_array to give required results.

### The fourth function is : function maximize_cellmass_unreg_anaerobic_data_dictionary(time_start,time_stop,time_step)
1. This basically checks for cell growth in anaerobic conditions without the boolean regulatory constraints.
2. the glucose uptake rate has been set to 10 following the paper by setting lb of glc_D in exchange array as -10.
3. It is seen that etoh(phosphate) plays an important role in cell growth. by updating the ub bound of etoh to 0.154(etoh being produced) in the exchange array will give the required objective value/growth rate of 0.21. etoh is a major bifurcation parameter.
4.The following reactions have been shut due to absence of oxygen
   default_flux_bounds_array[56,1:2] = 0
	 default_flux_bounds_array[57,1:2] = 0
	 default_flux_bounds_array[103,1:2] = 0
	 default_flux_bounds_array[104,1:2] = 0
5. The reaction for ATP maintainance has been enabled by setting : default_flux_bounds_array[20,1:2] = 7.6
6. Solve.jl runs for this function to give the same objective value which verifies that the model is working properly because the reaction shut off by the boolean constraints have no role in the optimal flux and hence will not change the growth rate of ecoli.
## ALL THESE FUNCTIONS ARE CALLED BY Solve.jl . Also 4 csv files containing the fluxes for aerobic and anaerobic growth with and without constraints has been uploaded for comparison. It seems like the fluxes dont vary much with or without constraints for a particular case.

### An excel file called Problem1b is uploaded for the parameter values and their refernces.

### A pdf file called Problem1 has been uploaded for Problem 1 derivation.

