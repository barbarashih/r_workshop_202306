# Introduction to R
## 1. R as a calculator
### Task 1.1: Try each of the line below in Rstudio
```r
1 + 2
1 * 2
8 / 2
10^4
10%%4
9%%4
8%%4
a
```
Questions to consider:
1. What does %% mean?
2. What does the error you get from typing "a" mean?

<br/><br/> 

## 2. Making variables
You can assign values to variables using the back arrow <-

### Task 2.1: Try the following
```
a <- 100
b <- 200
a + b
a / b
````
Variable naming tips
Good            | Bad           |  Warning         |
| ------------- |:-------------:|:---------------:|
| sampleMetaData1      | sample Meta Data 1 |          sampleMetaData1 is not the same as samplemetadata1   |
| sample.meta.data.1      | s@mple.meta.data.1      |  short common terms could be existing functions (e.g. min, max, mean)   |
| sample_meta_data_1 | 1_sample_meta_data      |               |


### Task 2.2: Try adding a few variables together. For example
```
apple <- 0.5
chocolate_bar <- 0.9
tuna_sandwitch <- 5.5
my_lunch <- apple + chocolate_bar + tuna_sandwitch
my_lunch
```

