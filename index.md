# Introduction to R
## 1. R as a calculator
### Task 1.1
```r
# Try using R like a calculator
1 + 2
1 * 2
8 / 2
10^4
```
### Task 1.2
```r
# What happens when you type in a letter instead of number?
x
```

Q1. What does the error you get from typing "x" mean?
<details>
Q2. Try adding a # before typing letters, what happens?
  <summary>Answers</summary>
  A1. The error message $\textcolor{red}{\textsf{Error: object 'x' not found}}$ means that R cannot find an object called x. When you see this error and you know that the object should be there, $\textcolor{blue}{\textsf{check that you haven't spelt it wrong}}$ . In this case, the object isn't there.
  A2. R ignores everything that comes after a #. It is considered to be a comment. Comments are extremely useful and your future-self will thank you for making good comments.
</details>

<br/><br/> 

## 2. Making objects


### Task 2.1
```r
# You can make objects in R by using back arrows <-
# "Objects" in R are usually called "variables" in other programming languages
a <- 100
b <- 200
a + b

# You can change the object to something else
a <- 1
a + b

# Your object name can be more descriptive
# This is important when you write longer piece of code, because it will quickly get confusing what short names like a and b refers to.
this_is_a_long_name <- 1000
a + this_is_a_long_name

````
| Good            | Bad           |  Warning         |
|:-------------:|:-------------:|:---------------:|
| sampleMetaData1      | sample Meta Data 1 |          Be careful where the capitalisations are- sampleMetaData1 is not the same as samplemetadata1   |
| sample.meta.data.1      | s@mple.meta.data.1      |  Avoid short common terms - they could be existing functions (e.g. min, max, mean)   |
| sample_meta_data_1 | 1_sample_meta_data      |               |
##### Table 1. Examples of good and bad object names. Notes on things to watch out for when naming your objects
.

### Task 2.2
```r
# Assign the cost for different foods into objects
apple <- 0.5
chocolate_bar <- 0.9
tuna_sandwich <- 5.5

# You can add these objects together
my_lunch <- apple + chocolate_bar + tuna_sandwich
my_lunch

```
### Task 2.3
```r
# You can create strings (a string of letters, numbers or symbols) if you put them in quotation marks
# They can be in double quotations or single quotation marks
item1 <- "apple"
item2 <- 'chocolate bar'
item1 + item2
```
Q1. What went wrong?
<details>
  <summary>Answer</summary>
  A1. "apple" and "chocolate bar" cannot be added together. To combine the two words, you would need to use paste (I will cover this later on).
</details>

<details>
  <summary>Challenge</summary>
  
  ### Challenge 2.1
  ```r
  # Try the code below
  apple <- "0.5"
  chocolate_bar <- "0.9"
  apple + chocolate_bar
  ```
  Q1: Did you get an error. If you did, what went wrong? If you did not, check what is different between the code you have typed and the code just above.
  
  A1. This error $\textcolor{red}{\textsf{Error in apple \+ chocolate\\_bar : non-numeric argument to binary operator}}$ is saying that the values you tried to add together are not numbers. Check that your objects are numeric by using class(chocolate_bar). Sometimes things can look like numbers, but R thinks it is not. This can sometimes be a problem when you import data.
</details>

### Task 2.4
```r
# Stick words together using paste, separating the objects with commas.
item1 <- "apple"
item2 <- "chocolate bar"
paste("lunch:",  item1, item2)
```
<details>
  <summary>Challenge</summary>

  ### Challenge 2.2
  ```r
  # You can change the separator for the words
  paste("lunch:",  item1, item2, sep = "," )

  # You can be more specific about what you want to seperate the words with using paste0
  paste0("lunch:", item1, ",", item2, ",", item3)

  # Notice how there are no spaces so far? Spaces are not "empty" space as far as R is concerned. If you want spaces, you need to let it know.
  paste0("lunch: ", item1, ", ", item2, ", ", item3)
  ```
</details>

<br> </br>
## 3. Data types
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
| list | list(white = "#FFFFFF", black = "#000000", red="#FF0000", odd_one_out = 1.12)  | A collection of objects that can be of different data types |
| function | myfun <- function(x, y){out <- x+y; out <- out + 100; return(out)}  | A block of code that only runs when it is called. There are many pre-set functions in R |
|  | min  |  |
##### Table 2. Main data types in R.


### Task 3.1

```r
# Try checking the data types of the variables you have created. 
# This is a very useful troubleshooting command when you are not sure what you're looking at. 
a
class(a)
item1
class(item1)
```

<details>
  <summary>Challenge</summary>
  
  ### Challenge 3.1
  It might take some time get get everyone set up, so please try out some of the examples in Table 2. Here are some ideas on things you can try:
  - Run the examples and see what they look like.
  - Editting the examples and check what happens. 
  - Remove one of the numbers in the data.matrix example, what happens?
  - What happens when you type class(class)?
  - After creating the function myfun, try myfun(1,2). What do you think the function is doing?
  - Try writing a function that converts celsius to fahrenheit.
  - Try making a function that stick together a defined string and a user input (for example, user can in put "apple", and "0.5", and the function will return "apple costs £0.5". If you can already do this, then try to make it return "An apple costs 50p".)
</details>


<br> </br>
## 4. Read in a file

```r
# We want to first find where our working directory is
# Working directory is the folder you are currently in for R
# You can find your working directory by using getwd() [get working directory]
getwd()

# Notice the data type for what you get back from getwd()
working_dir <- getwd()
class(working_dir)
```
### Task 4.1

```r
# Create a folder where you want to work from for this workshop and make a string that has the folder path
# IMPORTANT: you need to change the line below to the folder on your computer (this example is for my computer)
# IMPORTANT: you can copy and paste the file path from Windows, but you need to change \ to /
working_dir <- "C:/Users/barbara_shih/r_workshop_202306"

# You can change your working directory by using setwd() [set working directory]
setwd(working_dir)

```
### Task 4.2
File 1

Download [gene expression data](https://github.com/barbarashih/r_workshop_202306/raw/main/gene_expression.csv). Go to the linked page then right click to choose "Save as..." when you're on the page.

File 2

Download the [gene descriptions](https://github.com/barbarashih/r_workshop_202306/raw/main/gene_long_name.csv) Go to the linked page then right click to choose "Save as..." when you're on the page.

Copy the downloaded files into your working directory.
```r
# You can use list.files() to list the files in your current working directory 
# (it will come back with nothing if there isn't any files)
list.files()
```
If you have finished this, please go try Challenge 3.1 (just under Task 3.1)


### Task 4.3
Read in a file.
```r
options(stringsAsFactors=FALSE)
gene_expr <- read.csv("gene_expression.csv")
gene_annotation <- read.csv("gene_expression.csv")
```

## 5. Tables
### Task 5.1
Check the table characteristics.
```r
# It's handy to know what datatype you are dealing with
class(gene_expr)
class(gene_annotation)

# This is a very useful way to check what an object looks like
head(gene_expr)
head(gene_annotation)
```
### Task 5.2
Each table is made up of columns and rows. All columns have the same length. All rows have the same length. You can refer to each of them individually.
```r
# First row
gene_expr[1,]
# First column 
gene_expr[,1]
# Refer to columns by name. 
# Once you entered $, it will give you options to auto-complete
gene_expr$Brain1


```









