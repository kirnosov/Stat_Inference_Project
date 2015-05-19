# Statistical Inference: Course Project - Part 1
Nikita Kirnosov  




```r
set.seed(111)
lambda <- 0.2
num_sim <- 1000
sample_size <- 40
sim <- matrix(rexp(num_sim*sample_size, rate=lambda), num_sim, sample_size)
row_means <- rowMeans(sim)
```


```r
hist(row_means, breaks=sample_size, prob=TRUE,
     main=expression(paste("Samples' averages distribution (",lambda,"=0.2)")),
     xlab="")
# experimental center of distribution
abline(v=mean(row_means),lty=2, lwd=2, col="black")
# theoretical center of distribution
abline(v=1/lambda,lty=2, lwd=2, col="red")
# theoretical density of the averages of samples
xfit <- seq(min(row_means), max(row_means), length=num_sim)
yfit <- dnorm(xfit, mean=1/lambda, sd=(1/lambda/sqrt(sample_size)))
lines(xfit, yfit, pch=22, col="red")
# add legend
legend('topright', c("simulation", "theoretical"), lty=c(1,1), col=c("black", "red"))
```

![](Part_1_files/figure-html/unnamed-chunk-2-1.png) 

Simulated 

           Simulated            Theoretical
       
 mean    5.03            5.00 
 
 variance    0.63     `r1/(lambda^2 * sample_size)`


```r
 x <- rbind(c("","Simulated","Theoretical"),c("mean",mean(row_means),1/lambda),
            c("variance",var(row_means),1/(lambda^2 * sample_size))) 
xtable(x)
```

```
## % latex table generated in R 3.2.0 by xtable 1.7-4 package
## % Mon May 18 14:37:51 2015
## \begin{table}[ht]
## \centering
## \begin{tabular}{rlll}
##   \hline
##  & 1 & 2 & 3 \\ 
##   \hline
## 1 &  & Simulated & Theoretical \\ 
##   2 & mean & 5.02561954250747 & 5 \\ 
##   3 & variance & 0.631229641474268 & 0.625 \\ 
##    \hline
## \end{tabular}
## \end{table}
```
