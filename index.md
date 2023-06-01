# Introduction to R
## 1. R as a calculator
### Task 1.1
Try each of the line below in Rstudio
```r
1 + 2
1 * 2
8 / 2
10^4
```
### Task 1.2
Try the below and consider the following questions
```r
10%%4
9%%4
8%%4
x
```

Q1. What does %% mean?

Q2. What does the error you get from typing "x" mean?

| :exclamation:  Error troubleshooting  |
|:------------|
|<span style="color:red">Error: object 'x' not found</span>|
| Check that you haven't set your variable (or spelt it wrong)|

<br/><br/> 

## 2. Making variables
You can assign values to variables using the back arrow <-

### Task 2.1
Try the following
```r
a <- 100
b <- 200
a + b
a / b
this_is_a_long_name <- 1000
a + this_is_a_long_name
````
| Good            | Bad           |  Warning         |
|:-------------:|:-------------:|:---------------:|
| sampleMetaData1      | sample Meta Data 1 |          Be careful where the capitalisations are- sampleMetaData1 is not the same as samplemetadata1   |
| sample.meta.data.1      | s@mple.meta.data.1      |  Avoid short common terms - they could be existing functions (e.g. min, max, mean)   |
| sample_meta_data_1 | 1_sample_meta_data      |               |
##### Table 1. Examples of good and bad variable names. Notes on things to watch out for when naming your variables.

### Task 2.2
Try adding a few variables together. For example
```r
apple <- 0.5
chocolate_bar <- 0.9
tuna_sandwitch <- 5.5
my_lunch <- apple + chocolate_bar + tuna_sandwitch
my_lunch
```
### Task 2.3
Try creating strings
```r
item1 <- "apple"
item2 <- "chocolate bar"
item1 + item2
```
Q1. What went wrong?
### Challenge 2.1
Try the code below
```r
apple <- "0.5"
chocolate_bar <- "0.9"
apple + chocolate_bar
```
Q1: Did you get an error. If you did, what went wrong? If you did not, check what is different between the code you have typed and the code just above.
| :exclamation:  Error troubleshooting  |
|:------------|
|<span style="color:red">Error in apple + chocolate_bar : non-numeric argument to binary operator</span>|
| Check that your variables are numeric by using class(). Sometimes it can look like numbers, but R thinks it is not.|

### Task 2.4
Stick words together using paste and paste0. Pay attention to the spaces
```r
item1 <- "apple"
item2 <- "chocolate bar"
item3 <- "tuna sandwich"
paste("lunch:",  item1, item2, item3)
```
### Challenge 2.2
```r
paste("lunch:",  item1, item2, item3, sep= ",")

paste0("lunch:",  item1, item2, item3)
paste0("lunch: ", item1, ", ", item2, ", ", item3)

```


<br> </br>
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
| function | myfun <- function(x, y){out <- x+y; out <- out + 100; return(out)}  | A block of code that only runs when it is called. There are many pre-set functions in R |
|  | min  |  |
##### Table 2. Main data types in R.


### Task 3.1
Try checking the data types of the variables you have created. This is a very useful troubleshooting command when you are not sure what you're looking at. 
```r
class(a)
```

<br> </br>
## 4. Read in a file
We want to first find where our working directory is. Working directory is the folder you are currently in for R. You can find your working directory by using getwd() [get working directory]
```r
getwd()
current_working_dir <- getwd()
class(current_working_dir)
```
### Task 4.1
Change your directory to a specified folder on your computer. You will need to change the working_dir below so it is a folder in your computer. You can do this by using setwd() [set working directory]
```r
working_dir <- "C:/Users/barbara_shih/r_workshop_202306"
setwd(working_dir)
```
### Task 4.2
Download the tables here and put them in your working directory.

### Challenge 4.1
It might take some time get get everyone set up, so please try out some of the examples in Table 2. Here are some ideas on things you can try:
- Run the examples and see what they look like.
- Editting the examples and check what happens. 
- Remove one of the numbers in the data.matrix example, what happens?
- What happens when you type class(class)?
- After creating the function myfun, try myfun(1,2). What do you think the function is doing?
- Try writing a function that converts celsius to fahrenheit.
- Try making a function that stick together a defined string and a user input (for example, user can in put "apple", and "0.5", and the function will return "apple costs £0.5". If you can already do this, then try to make it return "An apple costs 50p".)

### Task 4.3
Read in a file.









