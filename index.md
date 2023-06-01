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
| Good            | Bad           |  Warning         |
|:-------------:|:-------------:|:---------------:|
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
## 3. Data types
Main data types in R:
Data type            | Examples           |  Long explaination         |
|------------- |-------------|---------------|
| numeric | 1 | Numbers, can be integers (whole numbers) or float (numbers with digits) |
|  | 3.20 | |
| string | "apple" | A mixture of characters, numbers or symbols |
|  | "3 three 2 two 1 one!" |  |
| boolean | TRUE  | True of false |
|  | FALSE  | |
| vector | c(1, 2, 3)  | An ordered collection of the same data type; you can give names |
|  | c("apple", "banana", "oranges")  | |
|  | c(white = "#FFFFFF", black = "#000000", red="#FF0000")  | |
| factor | factor(c("r", "b", "g", "b", "r"), levels=c("r", "g", "b"))  | Like vectors, but with pre-defined and ordered values (catogerial data) |
| data.frame | data.frame (food = c("apple", "chocolate bar", "tuna sandwitch"), cost = c(0.5, 0.9, 5.5))  | Table made of collections of vectors |
| data.matrix | matrix(c(1, 2, 3, 4, 5, 6), nrow = 2)  | Numeric table with fixed number of rows/columns. Need to make sure the number of elements is divisible by the stated nrow or ncol (number of row/columns) |
| list | list(white = "#FFFFFF", black = "#000000", red="#FF0000", odd_one_out = 1.12)  | A collection of variables that can be of different data types |




