# EDA plots for microarray


```r
shistogram <- function(z, unit) {
    n <- length(z)
    h <- hist(z, breaks = seq(from = min(z) - unit, to = max(z) + unit, by = unit), 
        col = "grey")
    d <- density(z)
    lines(d$x, d$y * n * unit, lwd = 3, col = "dodgerblue")
    arrows(h$breaks[1], max(h$counts), h$breaks[1] + unit, max(h$counts), angle = 90, 
        code = 3, length = 0.1)
    text(h$breaks[1] + unit, max(h$counts), paste("unit =", unit), pos = 4)
}
```



```r
set.seed(1)
n <- 1000
z <- rnorm(n)
par(mfrow = c(2, 2))
shistogram(z, unit = 1)
shistogram(z, unit = 2)
shistogram(z, unit = 0.5)
shistogram(z, unit = 0.1)
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 
