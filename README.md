# modelling-des-nns
This repository contains the code to model differential equations and solve the inverse learning problem using neural networks. The 2 examples shown include the mixing tank model and the predator prey model (coupled differential equations) 

# Data generator function recommended usage
The data files are generated using code using parameters that can be modified in the function call. But the default arguments are the recommended parameter settings in order to avoid overflow errors and such. It is also recommended to sample test data from the same range or a subset of the same range. This is in order to ensure that the test data is from a similar distribution as the training data, without which the probability distribution the model learnt will not be very meaningful. For the mixing tank, the data gen function is called every time we run because it doesn't take too long to run and gives us flexibility to customize the parameters. 

# Data generator function limitations (predator prey model only) 
The data files take a really long time to generate. Models like the predator prey system don't have separable equations (with respect to time) and as a result, we resort to using ODE solvers. The ODE solvers take in a set of initial conditions and give us an output for the desired time period. These ODE solvers take up a lot of memory and time, often exceeding usage limits on platforms such as colab. Additionally, the solutions they generate are limited by other factors such as precision. We often see exponential growth or decay when using these solvers which completely skew the cost function value. In such cases, we regenerate a different random set of initial conditions. A few runs saw that in order to generate 10000 predator prey systems which were not running into errors, the solver actually had to be run 50000 times ie. 40000 predator prey systems resulted in some error or the other. For this purporse, the data is generated and stored before hand in a csv file and is simply loaded in. 

# Data files links: 
The following link contains 6 files. input1.csv, predator1.csv, prey1.csv and 3 others. The other 3 are from a different data distribution which did not work well but are stored for the purpose of completeness should this be expanded further later. Only the above 3 data files were used in the code.
Link: https://drive.google.com/drive/folders/1XffLNkG9YmcywQtKo0ElsQRpvWu8hky9?usp=sharing

