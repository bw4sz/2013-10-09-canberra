Probabilities and Distributions
================================

Generating random samples from a normal distribution

It is often very useful to be able to generate a sample from a specific distribution. To generate a sample of size 100 from a standard normal distribution (with mean 0 and standard deviation 1) we use the rnorm function. We only have to supply the n (sample size) argument since mean 0 and standard deviation 1 are the default values for the mean and stdev arguments.


```r
norm <- rnorm(100)
norm
```

```
##   [1] -0.63456 -0.57886  1.68228  1.33340 -0.86267  0.93719  0.47246
##   [8] -2.43817  0.34920  0.44248  1.01323 -0.92200  0.66717  1.81362
##  [15] -0.22160  0.43769 -1.63710  0.02365  0.96546  1.70067  0.11775
##  [22]  1.38804 -0.07241  0.22388  1.34210 -1.58053 -0.97429 -0.15902
##  [29] -0.69787  2.52081  0.35395  1.01852  0.05577  1.25033 -1.10622
##  [36]  0.10463  0.25839  0.43501 -0.92816  0.97412 -0.24990 -0.47178
##  [43]  0.48782 -0.89487 -0.03540 -1.36953 -0.73619 -0.60991 -0.25363
##  [50]  1.33434 -1.85498 -1.20528 -0.10509 -0.15665 -0.41716 -0.15326
##  [57] -0.54807 -0.29925  1.53662  0.95271  1.06218 -1.11212 -0.82446
##  [64]  1.30715  0.65951  0.94922  1.11404  1.63760 -1.74180  0.71059
##  [71]  0.77183  0.32674 -1.23963  0.76493  0.41274 -0.78568 -0.78058
##  [78]  0.02567  0.16915 -0.29749 -0.89506  1.13275 -0.70355  1.11972
##  [85] -0.84441  0.45923 -2.89235 -0.16611  1.10538  0.52104 -0.39094
##  [92] -0.89882 -1.57878 -0.70863  0.45567  0.49140  1.60069  0.06814
##  [99]  0.60811  0.76755
```


**Try It!**
------------
1. Look up the rnorm function in help screen, what are three arguments?
2. Draw 100 random numbers from a normal distribution with a mean of 3 and an sd of 2, assign it to an object "a"

3. Find the mean number if your draw, how close was it to the true mean
4. Using the ?? tool, lookup the function for standard deviation *Hint* the ?? tool should not include spaces.
5. Drawing on what we learned last time, if norm is a vector of 100 random normal draws, what is the syntax to get the 13th number in the vector?

Generating random samples from other distributions
----------------------------------------------------

R has many distributions in the base package, including all commonly used in biological analysis. Depending on the distribution, each function has its own set of parameter arguments. For example, the rpois function is the random number generator for the Poisson distribution and it has only the parameter argument lambda. The rbinom function is the random number generator for the binomial distribution and it takes two arguments: size and prob. The size argument specifies the number of Bernoulli trials and the prob argument specifies the probability of a success for each trial. 

For now, its sufficient to know that a possion distribution is commonly used for count data, and has only paramater lambda, which is both the expected mean and var

Generating a random sample from a Poisson distribution with lambda=3

**Try It!**
------------
6. Draw 100 values from a poisson with a lambda =3, assign it to an object a
7. Draw 1000 values from a poisson with a lambda, assign it to an object b
8. Find the means of both draws, what is the difference in means?

Other probability and distribution functions
--------------------------------------------
For each of the distributions there are four functions which will generate fundamental quantities of a distribution. Let's consider the normal distribution as an example. We have already given examples of the rnorm function which will generate a random sample from a specific normal distribution. The dnorm function will generate the density (or point) probability for a specific value for a normal distribution. This function is very useful for creating a plot of a density function of a distribution. In the list of the random number generator functions all the functions started with an "r", similarly the density functions for all the distributions all start with a "d".


**Try It!**
------------

9. What is the point probability for a -1.96 for a normal of mean =0, sd=1
10. We want to make a sequence of numbers, based on a given interval, look up, using ??sequence, and find the function that does this. *Hint* it is in the base package
11. Create a sequence beginning at 0 and ending at 4, with .2 intervals, save this as object x.

An introduction to plotting - Univariate
=====================================

```r
dens <- dnorm(x, 2, 0.5)
```

```
## Error: object 'x' not found
```

```r
plot(x, dnorm(des, 2, 0.5), type = "l")
```

```
## Error: object 'x' not found
```



# plotting the density function of a binomial distribution: Binom(30, .25)
y <- 0:30
plot(y, dbinom(y, 30, 0.25), type = "h")

