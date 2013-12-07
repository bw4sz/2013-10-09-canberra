Beyond Vectors - Beginning with Data frames
===========================================

A data frame is a very important data type in R. It's pretty much the de facto data structure for most tabular data and what we use for statistics. Data frames can have additional attributes such as rownames() and colnames(). This can be useful for annotating data.

**Useful functions**  

head() - see first 5 rows

tail() - see last 5 rows

dim() - see dimensions

nrow() - number of rows

ncol() - number of columns

str() - structure of each column

names() - will list column names for a data.frame (or any object really).

Data frames are usually read in from file, but R comes with many practice datasets. We will use the iris dataset, famously used by Fisher in 1936 (http://en.wikipedia.org/wiki/Iris_flower_data_set)

Exploring Data
------------------

**Try It!**
------------
1. 
Subsetting
=================

R has many powerful subset operators and mastering them will allow you to easily perform complex operation on any kind of dataset. Allows you to manipulate data very succinctly.

Subsetting atomic vectors

```r
x <- seq(0, 10, 1)
```


1. Using positive integers


```r
x[1]
```

```
## [1] 0
```

```r
x[c(3, 1)]
```

```
## [1] 2 0
```


2. Using negative integers


```r
# skip the first element
x[-1]
```

```
##  [1]  1  2  3  4  5  6  7  8  9 10
```

```r
# skip the first and the fifth
x[-c(1, 5)]
```

```
## [1]  1  2  3  5  6  7  8  9 10
```


3. Using logical operators


```r
x[c(TRUE, TRUE, FALSE, FALSE)]
```

```
## [1] 0 1 4 5 8 9
```

```r
# or based on a condition
x[x > 3]
```

```
## [1]  4  5  6  7  8  9 10
```

```r
x[which(x > 3)]
```

```
## [1]  4  5  6  7  8  9 10
```

```r
# Also see `which.max()` and `which.min()`
```


```coffee
df <- data.frame(x = 1:3, y = 3:1, z = letters[1:3])

df[df$x == 2, ]
#   x y z
# 2 2 2 b
df[c(1, 3), ]
#   x y z
# 1 1 3 a
# 3 3 1 c

# There are two ways to select columns from a data frame
# Like a list:
df[c("x", "z")]
#   x z
# 1 1 a
# 2 2 b
# 3 3 c
# Like a matrix
df[, c("x", "z")]
#   x z
# 1 1 a
# 2 2 b
# 3 3 c

# There's an important difference if you select a simple column:
  # matrix subsetting simplifies by default, list subsetting does not.
  df["x"]
#   x
# 1 1
# 2 2
# 3 3
df[, "x"]
# [1] 1 2 3
```