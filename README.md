<h2>Machine Learning-Support Vector Machines</h2>
<h3>Description:</h3>
<ul style="list-style-type:disc">
<li>A Python script to estimate from scratch Support Vector Machines for linear, polynomial and Gaussian kernels utilising the quadratic programming optimisation algorithm from library CVXOPT.</li>
<li>Support Vector Machines implemented from scratch and compared to scikit-learn's implementation.</li>
<li>All labelled examples are simulated data.</li>
<ul style="list-style-type:disc">
	<li>Linear hard margin fits linearly separable data. Linear soft margin fits linearly separable data with some overlap in class examples. Both Gaussian and polynomial kernels estimate non-linearly separable examples.</li>
</ul>
</ul>



<table style="max-width:100%;white-space:nowrap;">
  <tr>
	  <th><h4><strong>Using this Python Script</strong></h4></th>
	  <th><h4><strong>Using SKLearn Library</strong></h4></th>    
  </tr>
  <tr>	  
    <th>
	    <h5><center>Hard Margin</center></h5><br>
	    <img src="images/SupportVectorMachinesCustomLibraryLinearHardMargin.png" width="425" alt="Linear SVM hard margin. Using custom library."/>
	  </th>
    <th>
	    <h5><center>Hard Margin</center></h5><br>
	    <img src="images/SupportVectorMachinesSklearnLibraryLinearHardMargin.png" width="425"alt="Linear SVM hard margin. Using SKLearn."/>
	  </th>
  </tr>	
  
  
  <tr>	
    <th>
	    <h5><center>Soft Margin</center></h5><br>
	    <img src="images/SupportVectorMachinesCustomLibraryLinearSoftMargin.png" width="400" alt="Linear SVM soft margin."/>
	</th>
    <th>
	    <h5><center>Soft Margin</center></h5><br>
	    <img src="images/SupportVectorMachinesSklearnLibraryLinearSoftMargin.png" width="400"alt="Linear SVM soft margin."/>
	</th>
  </tr>	
  
  
  <tr>
    <th>
	    <h5><center>Polynomial Kernel</center></h5><br>
	    <img src="images/SupportVectorMachinesCustomLibraryPolynomial.png" width="400" alt="Polynomial SVM. Custom library."/>
	</th>
    <th>
	    <h5><center>Polynomial Kernel</center></h5><br>
	    <img src="images/SupportVectorMachinesSklearnLibraryPolynomialMargin.png" width="400"alt="Polynomial SVM. Using SKLearn."/>
	</th>
  </tr>	
  
  <tr>
    <th>
	    <h5><center>Gaussian Kernel</center></h5><br>
	    <img src="images/SupportVectorMachinesCustomLibraryGaussianMargin.png" width="400" alt="Gaussian SVM. Custom library."/>
	</th>
    <th>
	    <h5><center>Gaussian Kernel</center></h5><br>
	    <img src="images/SupportVectorMachinesSklearnLibraryGaussianMargin.png" width="400"alt="Gaussian SVM. Using SKLearn."/>
	</th>
  </tr>	
  
  
</table
 <h3>Given two classes of labelled examples, we are interested in finding a decision boundary resulting from an appropriate choice of support vectors.</h3>
 
<ul style="list-style-type:disc"> 
<h3>Model</h3>
<li><p>Simulate labelled training dataset <img src="svgs/4388ea036963a2791929a7365e301c7a.svg" align=middle width=294.09701144999997pt height=27.91243950000002pt/> where there are N couples of <img src="svgs/81fe5e49971b8fdc94a28f66e9310309.svg" align=middle width=55.44161204999999pt height=24.65753399999998pt/> and k is the number (dimension) of x variables.</p></li>
<li>We are interested in SVM disrimitive analysis by finding the optimum decision boundary resulting from a choice of S support vectors.
This SVM optimization problem is a constrained convex quadratic optimization problem. 
Meaning it can be formulated in terms of Lagrange multipliers.
For the Lagrange multipliers to be applied under constraints, can use the Wolfe Dual Principle which 
is appropriate as long as the Karush Kuhn Tucker (KKT) conditions are satisfied.
Further, as this is a convex problem, Slater’s condition tells us that strong duality holds such that the dual and primal optimums give the solution.</li>
A benefit to this dual formulation is that the objective function only depends on the Lagrange multipliers (weights and intercept drop out).
Further, this formulation will be useful when requiring Kernals for entangled data sets.

<li>The Wolfe dual soft margin formula with kernel is given by

<p align="center"><img src="svgs/0acbd9783d20c53d1e9f750f2665520d.svg" align=middle width=333.89845664999996pt height=131.37932775pt/></p>

Where
<p><img src="svgs/c745b9b57c145ec5577b82542b2df546.svg" align=middle width=10.57650494999999pt height=14.15524440000002pt/> are the Lagrange multipliers, <img src="svgs/39ae080f4ae6ef7bda6a0ca0c44efc78.svg" align=middle width=32.48865674999999pt height=24.65753399999998pt/> is the kernel function, N are the number of training 
samples in the dataset, x is the matrix of training samples, y is the vector of target values, C is a supplied hyperparameter.</p>
</li>
<li>The non-zero Lagrange multipliers are the data points which contribute to the formation of the decision boundary.
<p>The hypothesis function <img src="svgs/4dd763dd7876885c2e5131a0b6d62d57.svg" align=middle width=133.02135495pt height=24.65753399999998pt/> is the decision boundary. The hypothesis formula in terms of the Kernel function is given by:</p></li>

<p align="center"><img src="svgs/554a33df7742aebf76ec7b81f6f3c17a.svg" align=middle width=283.76643075pt height=49.315569599999996pt/></p>
<p>Where S is the set of support vectors, <img src="svgs/c745b9b57c145ec5577b82542b2df546.svg" align=middle width=10.57650494999999pt height=14.15524440000002pt/> is the Lagrange multiplier, b is the bias term, y is the target from the examples, <img src="svgs/39ae080f4ae6ef7bda6a0ca0c44efc78.svg" align=middle width=32.48865674999999pt height=24.65753399999998pt/> is the Kernel and</p>

<p align="center"><img src="svgs/cb555672d4c84c369da09fd80f6811d8.svg" align=middle width=184.7945286pt height=69.0417981pt/></p>


<h4>Linear Kernel</h4>
<li><p>Applies to linearly separable data in the <img src="svgs/433badc501d4f8a183b14684b47f305e.svg" align=middle width=18.424726649999986pt height=26.76175259999998pt/> space.</p></p>
<li>When the constraint C is zero. The data must be completely linearly separable and the decision boundary is referred to as <em>'hard margin'</em>.</li>
<li>When the parameter C is non-zero, the approach allows for some overlap in the data and the decision boundary is referred to as <em>'soft-margin'</em>.</li>


<p align="center"><img src="svgs/3229be5d1587352e6b4dddbb725a2468.svg" align=middle width=114.9997167pt height=17.2895712pt/></p>
Where x and x' are two vectors.

<h4>Polynomial Kernel</h4>
<p>Applies to non-linearly separable data in <img src="svgs/d03c1e146df015e061405cc425738d83.svg" align=middle width=18.424726649999986pt height=26.76175259999998pt/> space.</p>
<p align="center"><img src="svgs/130c930cf5becce140bc3628f8d6d787.svg" align=middle width=168.4659702pt height=18.88772655pt/></p>
Where C is a constant and d is the degree of the kernel.

<h4>Gaussian Kernel (aka Radial Basis Function (RBF)) </h4>
<p>Applies to non-linearly separable data in <img src="svgs/7d8f6ef7574d1ebbafb8c1f734d24b6e.svg" align=middle width=24.97726109999999pt height=22.648391699999998pt/>. space.</p>
<p align="center"><img src="svgs/427b753bc670d106e67a2c8c5e77febf.svg" align=middle width=213.56621055pt height=21.1544223pt/></p>
<p>Where <img src="svgs/243cf87857232b4de4bc600c26d9d7cb.svg" align=middle width=22.20931349999999pt height=19.1781018pt/> is a free scalar parameter chosen based on the data and defines the influence of each training example.</p>


<h3>CVXOPT Library</h3>
The CVXOPT library solves the Wolfe dual soft margin constrained optimisation with the following API:
 
<p align="center"><img src="svgs/d815dd2e1e10d79a7162f6fe778314f4.svg" align=middle width=137.42467695pt height=78.26216475pt/></p>
<p>Note: <img src="svgs/ceddacf03a28d83100c38150c1076c1f.svg" align=middle width=12.785434199999989pt height=20.931464400000007pt/> indicates component-wise vector inequalities. It means that each row of the matrix <img src="svgs/b5087617bd5bed26b1da99fefb5353f1.svg" align=middle width=23.50114799999999pt height=22.465723500000017pt/> represents an inequality that must be satisfied.</p>
 
To use the CVXOPT convex solver API. The Wolfe dual soft margin formula is re-written as follows

<p align="center"><img src="svgs/a364906d0854671fe9b9718ce4ce1ec3.svg" align=middle width=212.12443724999997pt height=81.45851505pt/></p>

Where 
<br>
<p>G is a Gram matrix of all possible dot products of vectors <img src="svgs/d7084ce258ffe96f77e4f3647b250bbf.svg" align=middle width=17.521011749999992pt height=14.15524440000002pt/>.</p>

<p align="center"><img src="svgs/5ceca286e4d3c1cb407465d5db863df5.svg" align=middle width=357.85148685pt height=88.76800184999999pt/></p>

<p align="center"><img src="svgs/ceeaf43e7d8f6cde00a8a21441244b9f.svg" align=middle width=386.18483804999994pt height=144.88403325pt/></p>

 
<h3>How to use</h3>
<pre>
python supportVectorMachines.py
</pre>
		
		
<h3>Expected Output</h3>
<pre>
Estimating kernel: linear
     pcost       dcost       gap    pres   dres
 0: -1.4469e+01 -2.6709e+01  5e+02  2e+01  2e+00
 1: -1.6173e+01 -1.1054e+01  1e+02  6e+00  6e-01
 2: -2.1081e+01 -1.0259e+01  1e+02  4e+00  3e-01
 3: -6.7928e+00 -4.0658e+00  1e+01  4e-01  3e-02
 4: -3.1094e+00 -3.4085e+00  9e-01  2e-02  2e-03
 5: -3.2416e+00 -3.2970e+00  7e-02  4e-04  4e-05
 6: -3.2908e+00 -3.2914e+00  7e-04  4e-06  4e-07
 7: -3.2913e+00 -3.2913e+00  7e-06  4e-08  4e-09
 8: -3.2913e+00 -3.2913e+00  7e-08  4e-10  4e-11
 9: -3.2913e+00 -3.2913e+00  7e-10  4e-12  4e-13
10: -3.2913e+00 -3.2913e+00  7e-12  4e-14  7e-15
Optimal solution found.
============================================================
        SUPPORT VECTOR MACHINE TERMINATION RESULTS
============================================================
               **** In-Sample: ****
3 support vectors found from 160 examples.
               **** Predictions: ****
40 out of 40 predictions correct.
============================================================
Finished
</pre>

<h3>Highlights</h3>
<ul style="list-style-type:disc">
<li>SVMs are particularly well-suited for classification of complex but small- or medium-sized linear and non-linearably separable datasets.</li>
<li>The SKLearn SVC class is based on the libsvm library, which implements an algorithm that supports the kernel trick. The training time complexity is usually between <img src="svgs/a7aa3d3f0a66b0ab8343cb0cdc65e815.svg" align=middle width=77.54648549999999pt height=26.76175259999998pt/> and <img src="svgs/5fb0b1e8a4351c46b2c6c4f85da74bf4.svg" align=middle width=77.54648549999999pt height=26.76175259999998pt/>. This means that training becomes slow when the number of training instances are large.</li>
<li>Support Vector Machines in Machine Learning generally follow <p><a href="https://github.com/DrIanGregory/MachineLearning-LogisticRegressionWithGradientDescentOrNewton">Logistic regression</a> in studies. This work is a natural stepping stone and advances the candidates Machine Learning knowledge from this step as follows:</li>
	<ul style="list-style-type:disc">
		<li>Strong introduction to vectors and vector operations.</li>
		<li>Appreciation and usage of advanced optimisation routines such as convex optimisation and Sequential Minimal Optimization (SMO).</li>
		<li>SKLearn implements SVM optimisation using LIBSVM which utilises an SMO routine.</li>
	</ul>
</ul>

<h3>Requirements</h3>
<p><a href="https://www.python.org/">Python (>2.7)</a>, <a href="http://www.numpy.org/">Numpy</a>, <a href="https://cvxopt.org/">CVXOPT</a>, <a href="https://scikit-learn.org">sklearn</a> and <a href="https://matplotlib.org/">matplotlib</a>.</p>
</ul>
