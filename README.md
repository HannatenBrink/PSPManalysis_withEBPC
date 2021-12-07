This is an adapted version of the original PSPManalysis (https://github.com/cran/PSPManalysis/tree/master/build). 

In this version, it is possible to calculate the second-order partial derivates of the R_0 value wrt the resident and mutant value of evolutionary traits for multiple populations during an ESS-continuation. In addition, it is possible to continue the point where R0_yy = 0 over two bifurcation parameters and ESS traits of multiple populations. 
Note that the package does not locate where the sign of R0_yy changes during an ESS-continuation.

To continue the ESS traits of multiple populations, the syntax is almost the same as in the original package:

output <- PSPMequi(modelname = NULL, 
                                 biftype = NULL, startpoint = NULL,
                      stepsize = NULL, parbnds = NULL, parameters = NULL,
                      options = NULL, minvals = NULL, maxvals = NULL,
                      clean = FALSE, force  = FALSE, debug  = FALSE,
                      silent = FALSE)
                      
where biftype equals 'ESS'. However, it is no longer necessary to specify for which population the R0_xx & R0_yy will be calculated. By default, these values will be calculated for each population. 



 To continue the point where R0_yy = 0,  the biftype argument should be set to 'EBPC'.
 
 The startpoint argument is the initial point of the computation. This initial point should be close to a the point where R0_yy equals zero. The initial point should be set as follows: 
 
 c(value bifpar1, environmental variables, population birth rates, value bifpar2, value ESStraits)
 
 The fifth argument 'parbnds'  should be a (row) vector with dimensions 6 + 4*N, where N is the number of traits in the ESS: 

 c(index bifpar1, minval bifpar1, maxval bifpar1, index bifpar2, minval bifpar2, maxval bifpar2,
 population N, index essparN, minval essparN, maxval essparN)
 
In the options argument, it is now necessary to specify for which population the PSPManalysis should continue the point R0_yy  = 0. This can be done by adding an option pair c("popEBP", "i"), where 'i' is the index of the population.


