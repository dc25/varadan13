---
title: "collage notes on machine learning"
tags: ""
layout: post
theme:  
categories: Technical_Notes

---

---

![logistic regression graph 1](https://1.bp.blogspot.com/-7UMiV8_5jYE/X2jFXdOjB2I/AAAAAAAAAfA/GaE7bRCHg7Mg7lgNmFRZWFYbp0AzFFYlQCLcBGAsYHQ/s16000/1.PNG)

> Note - &lt; y={0:'stroke' , 1:'drug overdose'}, x=... > when linear regression is used on this dataset show that the obtained b's are same even if we encode y={1:'stroke' , 0 :'drug overdose'}  
> This is however not the case when y has more than two encodings. This is the major reason why we don't use regression.

![logistic 2](https://1.bp.blogspot.com/-6aixVw_UZnY/X2jKO6OsRCI/AAAAAAAAAfM/XoJyGZ6fwgw-CcG4YHZk6yg-1gZ5HBcVwCLcBGAsYHQ/s16000/1.PNG)

Rather than modeling response Y directly, logistic regression models the probability that Y belongs to a particular category.
For the Default data, Pr(default = Yes|balance) is predicted/modeled in logistic.  
The values of Pr(default = Yes|balance), which we abbreviate p(balance),
will range between 0 and 1. Then for any given value of balance, a prediction
can be made for default. For example, one might predict default = Yes
for any individual for whom p(balance) > 0.5. Alternatively, if a company
wishes to be conservative in predicting individuals who are at risk for default,
then they may choose to use a lower threshold, such as p(balance) >
0.1.

> What does it mean that Pr(default = Yes|balance)  is modeled? How do we do that?  
> We estimate the parameters  
> ...  
> What are the parameters? 
> 'betas'  

![l3](https://1.bp.blogspot.com/-EQINsTUa920/X2jODnOGU-I/AAAAAAAAAfY/fM-vLaN0WDY0dReTNXosqwdxxwN2eAqngCLcBGAsYHQ/s320/1.PNG)

This is the function that is used to model the probability. The main property of this function is that it ranges from 0 to 1, no matter what beta is.

> Try to visualise this function.  
> also visualise log odds form. 

![df](https://1.bp.blogspot.com/-DqsPLzPFDx0/X2jPcTNEdRI/AAAAAAAAAfk/ZtsNGLjHDNgrJnnwFDWsLLFRMMKFPGReQCLcBGAsYHQ/s320/1.PNG)   The LHS represents odds ratio and this ranges from 0 to infinity.

![fa](https://1.bp.blogspot.com/-4Vm1trKHV-U/X2jPlNZ-nGI/AAAAAAAAAfo/wAY0AWjYb74voBSmg7M46Oatax0Ic1wxwCLcBGAsYHQ/s320/1.PNG)

> statistically speaking.  
> betas follow normal distribution and we can test whether they are significant or not.  
> ....  
> betas have standard error which can be calculated.  
> ....  
> the model accuracy can also be calculated.  
> ....  
> Try to do it while coding!!!

![faf](https://1.bp.blogspot.com/-qTisgNLNzLA/X2jQyDHzDWI/AAAAAAAAAf4/QJYS_ZGPnTIaHg8vwPL570i8LP_jjqaPwCLcBGAsYHQ/s16000/1.PNG)  

in the default data set, HOW DO YOU INTREPRET THE VALUE OF SLOPE i.e., the value of parameter  
associated with balance. LOOK ABOVE!!! 

the only thing that remains is to predict. which is easy!!! 

### CONFOUNDING IS A PROBLEM. CORRELATION BETWEEN PREDICTORS AND BETWEEN PREDCITORS AND RESPONSE IS A PROBLEM.

### SO CONDUCT TEST AND MAKE SURE NO CONFOUNDING AND CORRELATION BETWEEN RLEVEANT ENTITIES

![GD](https://1.bp.blogspot.com/-kiwfROwBj9g/X2jYSTC9k0I/AAAAAAAAAgE/g7Y-7JhYR9oz6iJ7gO5TXAYNnBCuKwqmgCLcBGAsYHQ/s16000/1.PNG)

> Check if each predictors is distributed normally using various statistical tests.

## 

Pr(Y = k|X = x) = ( 	(πk) Pr(X = x|Y = k)	)  /  (	 sum(πi Pr(X = x|Y = i)	)	)   

πk - the probability of an observation belonging to kth class can be easily available if the data is large and randomly generated by averaging the no of observation for a given class.

if we can estimate Pr(X = x|Y = i) for all i then the LHS can be easily estimated.  

This is the methodology of **linear discriminant analysis**  

# 

### Leave One Out Cross Validation

LeaveOneOut (or LOO) is a simple cross-validation. Each learning set is created by taking all the samples except one, the test set being the sample left out 

As a general rule, most authors, and empirical evidence, suggest that 5- or 10- fold cross validation should be preferred to LOO.

### 

    	from sklearn.model_selection import LeaveOneOut
        X = [1, 2, 3, 4]
        
        loo = LeaveOneOut() #LeaveOneOut() is equivalent to KFold(n_splits=n) and LeavePOut(p=1)
        
        for train, test in loo.split(X): #TO SPLIT X INTO TRAIN AND TEST USING LEAVE ONE OUT PROCEDURE 
        									USE loo.split() this spits out train and test arrays
    			 print("%s %s" % (train, test))

### Leave P out.

        from sklearn.model_selection import LeavePOut

    	X = np.ones(4)
    	lpo = LeavePOut(p=2)
    	for train, test in lpo.split(X):
    			print("%s %s" % (train, test))
                
                
                
                
                
        X_train, X_test, y_train, y_test = train_test_split(
        X, y, test_size=0.4, random_state=0) ## THIS IS A SIMPLE RANDOM TEST AND TRAIN DATASET FROM THE GIVEN DATASET
        
        
        

# 

### Decisison tree

            import numpy as np
    		from sklearn.tree import DecisionTreeRegressor
    		import matplotlib.pyplot as plt

    		# Create a random dataset
    		
            rng = np.random.RandomState(1)
            

""" what is [seed](https://en.wikipedia.org/wiki/Random_seed) in random number generation?  

it is the starting point of the sequence from which point onwards the random no is generated by the computer. for same seed we get same random numbers.  
this is particularly useful if we want to replicate a random experiment during testing. """

            X = np.sort(5 * rng.rand(80, 1), axis=0)
            

""" rng.rand(80,1) produces 80 rows of random numbers in one column. basically rand produces random numbers in the given shape.

np.sort(...) Return a sorted copy of an array.

what is axis of a numpy array?

axis 0 represents rows in a 2d matrix/array
axis 1 represents columns in an array.  

in summary this code creates x a sorted array of size '80 r \* 1 c' with entries random and this array is sorted along row 
"""

    		y = np.sin(X).ravel() # why do you need it here ???
    		y[::5] += 3 * (0.5 - rng.rand(16))
            

""" .ravel() -- Return a contiguous flattened array.  

"""

    		# Fit regression model
    		regr_1 = DecisionTreeRegressor(max_depth=2)
    		regr_2 = DecisionTreeRegressor(max_depth=5) # I DON'T UNDERSTAND WHAT IS max_depth=2/5
    		regr_1.fit(X, y)
    		regr_2.fit(X, y)

    		# Predict
    		X_test = np.arange(0.0, 5.0, 0.01)[:, np.newaxis] # I DON'T UNDERSTAND THIS STEP. 
    		
            y_1 = regr_1.predict(X_test)
    		y_2 = regr_2.predict(X_test)

    		# Plot the results
    		plt.figure()
    		plt.scatter(X, y, s=20, edgecolor="black",
            c="darkorange", label="data")
    		plt.plot(X_test, y_1, color="cornflowerblue",
         label="max_depth=2", linewidth=2)
    		plt.plot(X_test, y_2, color="yellowgreen", label="max_depth=5", linewidth=2)
    		plt.xlabel("data")
    		plt.ylabel("target")
    		plt.title("Decision Tree Regression")
    		plt.legend()
    		plt.show()
            

## logistic regression

The general workflow is:  

-   get a dataset  
-   train a classifier  
-   make a prediction using such classifier  

### Hypothesis of logistic regression is

![xyz](https://miro.medium.com/max/1050/1*o4Dy1w4n2kDOLA8UEwGC9g.png)

# 

### Calculate Singular-Value Decomposition

The SVD can be calculated by calling the **svd()** function.

The function takes a matrix and returns the U, Sigma and V^T elements. The Sigma diagonal matrix is returned as a vector of singular values. The V matrix is returned in a transposed form, e.g. V.T.

The example below defines a 3×2 matrix and calculates the Singular-value decomposition.

            # Singular-value decomposition
            from numpy import array
            from scipy.linalg import svd
            # define a matrix
            A = array([[1, 2], [3, 4], [5, 6]])
            print(A)
            # SVD
            U, s, VT = svd(A)
            print(U)
            print(s)
            print(VT)
            

### Reconstruct Matrix from SVD

            # Reconstruct SVD
            from numpy import array
            from numpy import diag
            from numpy import dot
            from numpy import zeros
            from scipy.linalg import svd
            # define a matrix
            A = array([[1, 2], [3, 4], [5, 6]])
            print(A)
            # Singular-value decomposition
            U, s, VT = svd(A)
            # create m x n Sigma matrix this done because svd returns sigma as a vector 
            Sigma = zeros((A.shape[0], A.shape[1])) 
            # populate Sigma with n x n diagonal matrix
            Sigma[:A.shape[1], :A.shape[1]] = diag(s)
            # reconstruct matrix
            B = U.dot(Sigma.dot(VT))
            print(B)
            
            

### SVD for Pseudoinverse

A^+ = V . D^+ . U^T

A^+ represents pseudo inverse of A
D^+ represents pseudo inverse of Sigma matrix 

How to calculate D^+?  

The D^+ can be calculated by creating a diagonal matrix from Sigma, calculating the reciprocal of each non-zero element in Sigma, and taking the transpose if the original matrix was rectangular.

Sigma = \[[S11, 0, 0], [0, S22, 0], [0, 0, S33]]

D^+ =\[[1/S11,0, 0],[0,1/S22,0],[0,0,1/S33]]

NumPy provides the function pinv() for calculating the pseudoinverse of a rectangular matrix.

                # Pseudoinverse
                from numpy import array
                from numpy.linalg import pinv
                # define matrix
                A = array([
                    [0.1, 0.2],
                    [0.3, 0.4],
                    [0.5, 0.6],
                    [0.7, 0.8]])
                print(A)
                # calculate pseudoinverse
                B = pinv(A)
                print(B)
                

DIRECT IMPLEMENTATION OF PSEUDOINVERSE IS 

                # Pseudoinverse via SVD
                from numpy import array
                from numpy.linalg import svd
                from numpy import zeros
                from numpy import diag
                # define matrix
                A = array([
                    [0.1, 0.2],
                    [0.3, 0.4],
                    [0.5, 0.6],
                    [0.7, 0.8]])
                print(A)
                # calculate svd
                U, s, VT = svd(A)
                # reciprocals of s
                d = 1.0 / s
                # create m x n D matrix
                D = zeros(A.shape)
                # populate D with n x n diagonal matrix
                D[:A.shape[1], :A.shape[1]] = diag(d)
                # calculate pseudoinverse
                B = VT.T.dot(D.T).dot(U.T)
                print(B)
                

Dimensionality reduction 

                from numpy import array
                from numpy import diag
                from numpy import zeros
                from scipy.linalg import svd
                # define a matrix
                A = array([
                    [1,2,3,4,5,6,7,8,9,10],
                    [11,12,13,14,15,16,17,18,19,20],
                    [21,22,23,24,25,26,27,28,29,30]])
                print(A)
                # Singular-value decomposition
                U, s, VT = svd(A)
                # create m x n Sigma matrix
                Sigma = zeros((A.shape[0], A.shape[1]))
                # populate Sigma with n x n diagonal matrix
                Sigma[:A.shape[0], :A.shape[0]] = diag(s)
                # select
                n_elements = 2
                Sigma = Sigma[:, :n_elements]
                VT = VT[:n_elements, :]
                # reconstruct
                B = U.dot(Sigma.dot(VT))
                print(B)
                # transform
                T = U.dot(Sigma)
                print(T)
                T = A.dot(VT.T)
                print(T)

        

dimensional reduction using sklearn

                from numpy import array
                from sklearn.decomposition import TruncatedSVD
                # define array
                A = array([
                    [1,2,3,4,5,6,7,8,9,10],
                    [11,12,13,14,15,16,17,18,19,20],
                    [21,22,23,24,25,26,27,28,29,30]])
                print(A)
                # svd
                svd = TruncatedSVD(n_components=2)
                svd.fit(A)
                result = svd.transform(A)
                print(result)