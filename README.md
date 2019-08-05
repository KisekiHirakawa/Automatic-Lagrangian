# Automatic-Lagrangian-
Python implementation of the  "Hills et al. (2015), An algorithm for discovering Lagrangians automatically from data. PeerJ Comput. Sci. 1:e31; DOI 10.7717/peerj-cs.31"

Summary Report 
Implementation of the Hills paper
Kiseki Hirakawa

Introduction & Environment specification
The paper was implemented using Python 3.7.3 on a macOS Mojave
Libraries used were 
Pandas
Sympy
Matplotlib
Itertools
Math
Functools
Numpy
Scipy
I have tested this implementation using the data (generated artificially) for a simple pendulum. 
Click here to my GitHub repository containing the jupyter notebook.

In my opinion, the paper was very well written and easy to understand. The author gave a detailed description of what was done which was extremely helpful during the implementation. On the other hand, the code provided was not really helpful(written in Mathematica). The implementation managed to find the equation of motion with reasonable accuracy. The reader must note that the data was generated using an ideal simulation. 

Benefits 
Easy to implement 
Accurate results 
Data was created based on the equation Double_dot(theta)=-5*theta and the result obtained was Double_dot(theta)=-4.938341*theta
Very fast 
“Note that, for a given polynomial model, it is possible to partially pre-calculate the score function ELD for a given dataset, yielding a function quadratic in the coefficients ci. This is possible because the form of the model is fixed and it is possible to calculate its derivatives in advance. As a result, after the initial simplification of the score function, optimisation iterations are fast, and have a run-time independent of the number of data points.” Hence, the optimization process does not depend on the number of data points.



Drawbacks and limitations
Accuracy limited due to restricted polynomial search
The accuracy was limited as I opted for the restricted polynomial search method(instead of the symbolic regression). This method has a much lesser computation time but comes at a cost of only being able to predict polynomial equations of motion(No trigonometric functions, etc). For the pendulum case, this method works well for small angles but starts to break down when the angle gets larger(Training data was created using an initial angle of 10 degrees).
This implies that we must check the order of magnitude for our problem. In the gas pressure sensor case this should not be an issue(after normalization) as the values are small. 

 Convergence not achieved always
The optimization was not achieved initially when tested using Nelder-mead algorithm. 
Some trial and error were required to find a suitable optimization algorithm(I've used the truncated newton method).

Further improvements
While the restricted polynomial search gives accurate results for a few cases, for this method to be applied broadly, the symbolic regression method will be much more useful in the long run. There could be ways to integrate the DSS and symbolic regression to further optimize the method. 







