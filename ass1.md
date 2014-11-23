Analysis of 40 exponential(0.2)s
========================================================

## Synopsis
This aims to explain and simulate the properties of the of 40 exponential(0.2)s.

## Simulation
Let us create a simulation of means of 1000 exponential distributions of size 40 each, with lambda 0.2

```r
means <- NULL
for(i in 1:1000) {
  means <- c(means, mean(rexp(40,0.2)))
}
```



The standard deviation of the distribution is:

```r
SD <- sd(means)
SD
```

```
## [1] 0.7728
```
The expected standard deviation of the individual exponential distributions is:

```r
expSD <- sd(rexp(40,0.2))
expSD
```

```
## [1] 4.65
```

Standard deviation of the sample distribution is effectively equal to standard deviation of the mean times the square root of the number of exponentials in the distribution:

```r
SD*sqrt(40)
```

```
## [1] 4.888
```

The mean and the theoretical center should be equal. Clearly reflected in the following:


```r
#Distribution mean:
mean(means)
```

```
## [1] 4.945
```

```r
#Theoretical center:
1/0.2
```

```
## [1] 5
```


The histogram for the graph is as follows: 
The histogram generated is as follows:

```r
hist(means)
```

![plot of chunk unnamed-chunk-6](figure/unnamed-chunk-6.png) 

Clearly, it simulates a bell curve, justifying normality.

The Shapiro-Wilk normality test confirms it too:


```r
shapiro.test(means)
```

```
## 
## 	Shapiro-Wilk normality test
## 
## data:  means
## W = 0.9915, p-value = 1.701e-05
```

The p value is highly negligible. Hence proving the normality of the distribution.
