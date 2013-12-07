
Subsetting Data
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



