# Introduction to R (Day 1)
## 1. R as a calculator
### Task 1.1. Try out some mathematical operators
```r
# Try using R like a calculator
1 + 2
1 * 2
8 / 2
10^4
8%%4
7%%4
6%%4
8%/%4
7%/%4

```
### Task 1.2. What happens when you type letters?
```r
# What happens when you type in letters instead of numbers?
x
```

Q1. What does the error you get from typing "x" mean?
<details>
  <summary>Answer</summary>
  The error message $\textcolor{red}{\textsf{Error: object 'x' not found}}$ means that R cannot find an object called x. When you see this error and you know that the object should be there, $\textcolor{blue}{\textsf{check that you haven't spelt it wrong}}$ . In this case, the object isn't there.
</details>
Q2. Try adding a # before typing letters, what happens?
<details>
  <summary>Answer</summary>
  R ignores everything that comes after a #. It is considered to be a comment. Comments are extremely useful and your future-self will thank you for making good comments.
</details>
Q2. What do %% and %/% mean?
<details>
  <summary>Answer</summary>
  X%%y gives the remainder when you divide X by y. X%/%y gives you the quotient you get. These have many useful applications, for example, counting codons or splitting sequences into equal-length lines.
</details>

<br/><br/> 

## 2. Making objects (variables)
### Task 2.1. Using mathematical with objects 
```r
# You can make objects in R by using back arrows <-
# "Objects" in R are usually called "variables" in other programming languages
a <- 100
b <- 200
a + b

# You can overwrite existing objects
a <- 1
a + b

# You can use the object in the process of overwriting it
a <- a + 1
a
a <- a + 1
a

# Your object name can be more descriptive
# This is important when you write longer pieces of code, 
# because short object names like a and b will quickly get confusing.
very_long_name <- 1000
a + very_long_name
```

<br></br>
| Good            | Bad           |  Warning         |
|:-------------:|:-------------:|:---------------:|
| sampleMetaData1      | sample Meta Data 1 (can't use spaces) |          Be careful of capitalisations - sampleMetaData1 is not the same as samplemetadata1   |
| sample.meta.data.1      | s@mple.meta.data.1  (can't use special symbols)    |  Avoid short common terms - they could be existing functions (e.g. min, max, mean)   |
| sample_meta_data_1 | 1_sample_meta_data (can't start with numbers)   |               |
##### Table 1. Examples of good and bad object names. Notes on things to watch out for when naming your objects

<br></br>
### Task 2.2. More on numeric objects
```r
# Assign the cost for different foods into objects
apple <- 0.5
chocolate_bar <- 0.9
tuna_sandwich <- 5.5

# You can add these objects together
my_lunch <- apple + chocolate_bar + tuna_sandwich
my_lunch

```
### Task 2.3. Character objects
```r
# You can create character objects (a string of letters, numbers or symbols) if you put them in quotation marks
# They can be in double quotations or single quotation marks
item1 <- "apple"
item2 <- 'chocolate bar'
item1 + item2
```
Q. What went wrong?
<details>
  <summary>Answer</summary>
  "apple" and "chocolate bar" cannot be added together. To combine the two words, you would need to use paste (I will cover this later on).
</details>

### Task 2.4
```r
# Try the code below
apple <- "0.5"
chocolate_bar <- "0.9"
apple + chocolate_bar
```
Q: Did you get an error. If you did, what went wrong? If you did not, check what is different between the code you have typed and the code above.

<details>  
  <summary>Answer</summary>
  This error $\textcolor{red}{\textsf{Error in apple \+ chocolate\\_bar : non-numeric argument to binary operator}}$ is saying that the values you tried to add together are not numbers. Check that your objects are numeric by using class(chocolate_bar). Sometimes things can look like numbers, but R thinks it is not. This can be a problem when you import data where part of the column has characters like "NaN" instead of numbers.
</details>

### Task 2.5
```r
# Stick words together using paste
item1 <- "apple"
item2 <- "chocolate bar"
paste("lunch:",  item1, item2)
```

### Task 2.6
```r
# You can change the separator 
paste("lunch:",  item1, item2, sep = "," )

# You can be more specific about what you want to seperate the words with using paste0
paste0("lunch:", item1, ",", item2, ",", item3)

# Notice how there are no spaces between words. 
# If you want spaces, you need to let R know.
paste0("lunch: ", item1, ", ", item2, ", ", item3)

```


<br></br>

## 3. Vectors
### Task 3.1
```r
# You can put multiple strings or numerics together as a vector (they have to be the same type)
x <- c(1, 2, 3)
x

# For continuous integers (i.e. 1, 2, 3, 4, 5) you can use :
x <- 1:3
x

# You can refer to each position of the vectors
x[3]

```
### Task 3.2
```r
# You can add multiple vectors of the same length
y <- c(3, 2, 1)
x + y

# Or add the same number to each element of a vector
y + 1

# Similarly, you can paste two vectors
letters <- c("a", "b", "c")
paste(letters, x, sep="")

# Or paste the same value to each element of a vector
paste("letter", letters, sep=" ")

# You can collapse values in a vector
paste(letters, collapse = "")
sum(x)
sd(x)

# You can combine multiple vectors (of the same type)
c(x, y)
c(100, y, 150)


```

### Task 3.3. Consistant data type within a vector

```r
# Try putting both numbers and characters in a vector
c(1, 2, 3, "apple")
```
Q. What happens when you put a mixture of numbers and characters in a vector?
<details>  
  <summary>Answer</summary>
  It turns all the numbers into strings (notice the quotation marks added around the numbers in the output even when you didn't add them when you created the object)
</details>



<details>
  <summary>Challenge 3.1</summary>

  ### Challenge 3.1
  ```r
  # Q. Try the below. What does the error mean?
  x <- c(1, 2, 3)
  y <- 1:5
  x + y
  ```
  <details>
    <summary>Answer</summary>
    It will give you an error message $\textcolor{red}{\textsf{Warning message: In x + y : longer object length is not a multiple of shorter object length}}$ . This is the mathmatical functions will only work if the longer object legnth is multiples of the shorter one. Try changing y <- 1:6
  </details>

  ```r
  # Q. Try the below. Why does it not return an error?
  x <- 1:5
  y <- c("a", "b")
  x + y
  ```
  <details>
    <summary>Answer</summary>
    Because this is not a mathmetical function, it just repeats the shorter length vector.
  </details>
  
  ```r
  # Make an empty vector
  x <- vector()
  # Set the 5th element of this vector to 100
  x[5] <- 100
  ```
  Q1. What happens to the first 4 elements
  <details><summary>Answer</summary>
  They are automatically filled with NA
  </details>

  ```r
  # Make an empty vector, declar the data type and length
  x <- vector("character", 5)
  # Set the 5th element of this vector to "100"
  x[5] <- 100
  ```
  Q1. What happens to the first 4 elements
  <details><summary>Answer</summary>
  They are automatically filled with ""
  </details>
  Q2. What data type is the 5th element?
  <details><summary>Answer</summary>
  Character. This is because the vector is delcared as a character vector.
  </details>
  ```
</details>



<br> </br>
## 4. Data types
Data type            | Examples           |  Long explaination         |
|------------- |-------------|---------------|
| integer | 1L | Integers (whole numbers) |
|  | 1:10 | |
| numeric (double) | 1 | Numbers |
|  | 3.20 | |
|  | c(1, 2.3, 5) | |
| character (string) | "apple" | A mixture of characters, numbers or symbols |
|  | "3 three 2 two 1 one!" |  |
|  | c(white = "#FFFFFF", black = "#000000", red="#FF0000")  | |
|  | c("a", "b", "c") |  |
| logical (boolean) | TRUE  | True or false |
|  | FALSE  | |
|  | c(TRUE, TRUE, FALSE)  | |
| factor | factor(c("r", "b", "g", "b", "r"), levels=c("r", "g", "b"))  | Like vectors, but with pre-defined and ordered values (catogerial data) |
| data.frame | data.frame (food = c("apple", "chocolate bar", "tuna sandwitch"), cost = c(0.5, 0.9, 5.5))  | Table made of collections of vectors |
| data.matrix | matrix(c(1, 2, 3, 4, 5, 6), nrow = 2)  | Numeric table with fixed number of rows/columns. Need to make sure the number of elements is divisible by the stated nrow or ncol (number of row/columns) |
| list | list(white = "#FFFFFF", black = "#000000", red="#FF0000", odd_one_out = 1.12)  | A collection of objects that can be of different data types |
| function | myfun <- function(x, y){out <- x+y; out <- out + 100; return(out)}  | A block of code that only runs when it is called. There are many pre-set functions in R |
|  | min  |  |
##### Table 2. Main data types in R.


### Task 4.1

```r
# List all the objects in the current R session
ls()

# Try checking the data types of the objects you have created. 
# This is especially for following online tutorials. 
a
str(a)
class(a)

```

<details>
  <summary>Challenge 4.1</summary>
  
  ### Challenge 4.1
  It might take some time get get everyone set up, so please try out some of the examples in Table 2. Here are some ideas on things you can try:
  - Run the examples and see what they look like.
  - Edit the examples. 
  - Remove one of the numbers in the data.matrix example.
  - What happens when you type class(class)?
  - After creating the function myfun, try myfun(1,2). What do you think the function is doing?
  - Try writing a function that converts celsius to fahrenheit.
  - Try making a function that stick together a defined string and a user input (for example, user can in put "apple", and "0.5", and the function will return "apple costs £0.5". If you can already do this, then try to make it return "apple costs £0.50".)
</details>

### Task 4.2
```r
# Change data types
mixed_num <- c(0, 1, 5, "missing")
class(mixed_num)
mixed_num_forced <- as.numeric(mixed_num)

# NA means Not Available. It is used to represent missing values
mixed_num_forced <- as.logical(mixed_num_forced)
class(mixed_num)
mixed_num_forced <- as.character(mixed_num_forced)
class(mixed_num)

```

  
## 5. Read in files

### Task 5.1
```r
# We want to first find where our working directory is
# Working directory is the folder you are currently in for R
# You can find your working directory by using getwd() [get working directory]
getwd()

# Notice the data type for what you get back from getwd()
working_dir <- getwd()
class(working_dir)
```
  
### Task 5.2

```r
# Create a folder where you want to work from for this workshop and make a string that has the folder path
# IMPORTANT: you need to change the line below to the folder on your computer (this example is for my computer)
# IMPORTANT: you can copy and paste the file path from Windows, but you need to change \ to /
working_dir <- "C:/Users/shihb/OneDrive - Lancaster University/work/teaching/workshop/r_workshop_202306"

# You can change your working directory by using setwd() [set working directory]
setwd(working_dir)

```
### Task 5.3
File 1

Download [gene expression data](https://github.com/barbarashih/r_workshop_202306/raw/main/gene_expression.csv). 
Go to the link above, and then right click to choose "Save as..." when you're on the page.

File 2

Download the [long gene name](https://github.com/barbarashih/r_workshop_202306/raw/main/gene_long_name.csv). 
Go to the link above, and then right click to choose "Save as..." when you're on the page.

Copy the downloaded files into your working directory.
```r
# You can use list.files() to list the files in your current working directory 
# (it will come back with nothing if there isn't any files)
list.files()
```
If you have finished this, please go try Challenge 4.1 (just under Task 4.1)


### Task 5.4
Read in a file.
```r
# Read in the files you have downloaded
gene_exprs <- read.delim("gene_expression.csv", sep=",")
gene_annotation <- read.delim("gene_long_name.csv", sep=",")
```

<br/><br/> 

## 6. Data frames (tables)
### Task 6.1
Check the data frame characteristics.

```r
# Check that you have read in the files.
# Do you see "gene_exprs" and "gene_annotation" when using ls()? (if not, let me know)
ls()
  
# It's handy to know what data type you are dealing with
class(gene_exprs)
class(gene_annotation)

str(gene_exprs)
str(gene_annotation)

# This is a useful way to check what an object looks like
head(gene_exprs)
head(gene_annotation)
               
# It is useful to check the number of rows and columns in a data frame
dim(gene_exprs)
nrow(gene_exprs)
ncol(gene_exprs)

```

### Task 6.2
Each table is made up of columns and rows. All columns have the same length. All rows have the same length. You can refer to each of them individually.
```r
# First row
gene_exprs[1,]
# Refer to multiple rows
gene_exprs[1:5,]
gene_exprs[c(1,4,5),]

# First column
gene_exprs[,1][1:10] # the first 10 values
gene_exprs$Brain1[1:10] # the first 10 values
gene_exprs[,c("Brain1", "Blood1")][1:10,] # the first 10 rows
               
# Check the data type
class(gene_exprs$Brain1)
class(gene_exprs$Name)
length(gene_exprs$Name)
```
  
### Task 6.3
```r
# You can get the column and rownames, these are vectors
colnames(gene_exprs)
rownames(gene_exprs)[1:10] # I only printed the first 10 

# You can set the row names to a vector of unique values
# Think of it like names - if you have 2 identical names, R wouldn't be able to tell which is which
row.names(gene_exprs) <- gene_exprs$Name
head(gene_exprs)                    
```
                         
### Task 6.4
```r
# You can make a new column by using existing columns
gene_exprs_edited <- gene_exprs
gene_exprs_edited$Mixed1 <-  gene_exprs_edited$Brain1 + gene_exprs_edited$Blood1
head(gene_exprs)
head(gene_exprs_edited)

# You can make a new column based on conditions you want 
# If condition
cond1 <- gene_exprs_edited$Brain1 > 0
cond2 <- gene_exprs_edited$Brain2 > 0
cond3 <- gene_exprs_edited$Brain3 > 0

# Chain your if conditions (using & and)
gene_exprs_edited$threshold <- cond1 & cond2 & cond3
head(gene_exprs_edited)
# Chain your if conditions (using | or)
gene_exprs_edited$threshold2 <- cond1 | cond2 | cond3
head(gene_exprs_edited)  
                          
```

### Task 6.5
```r
# Let's filter this data frame so we only keep rows where all brain samples have an expression
# You don't have to add the column to the data frame (you can create the TRUE/FALSE vector outside the dataframe)
keep <- (gene_exprs$Brain1 > 0) & (gene_exprs$Brain2 > 0) & (gene_exprs$Brain3 > 0)  
gene_exprs_edited <- gene_exprs[keep,]
nrow(gene_exprs)
nrow(gene_exprs_edited)                    
```
                    
### Task 6.6
```r
# Annotate the genes with a different data frame
head(gene_annotation)
head(gene_exprs_edited)
gene_exprs_annotated1 <- merge(gene_exprs_edited, gene_annotation, by.x = "Name", by.y="Name")
gene_exprs_annotated2 <- merge(gene_exprs_edited, gene_annotation, by.x = "Name", by.y="Name", all.x=TRUE)

# What is the difference between whether if you use all.x?
nrow(gene_exprs_annotated1)
nrow(gene_exprs_annotated2)
                         
```

### Task 6.7
```r
# Keeping only columns that you want
# Get columns with names starting with Blood or Brain
pattern_match <- grepl("^(Blood|Brain)", colnames(gene_exprs))
gene_exprs_nums <- gene_exprs[,pattern_match]

# ^ indicates the start of the word
# Try 
grepl("^(Blood|Brain)", colnames(gene_exprs))
grepl("^(lood|rain)", colnames(gene_exprs))
grepl("(lood|rain)", colnames(gene_exprs))

# refer to the index instead
grep("^(Blood|Brain)", colnames(gene_exprs))

```

<details>
  <summary>Challenge 6.1</summary>
  
  ### Challenge 6.1  
  ```r
  # You can refer to specific columns in a dataframe by their name
  gene_exprs_annotated1[,c("Brain1", "Blood1")]
  ```
  Q. Try to organise your dataframe so the columns starts with "Name", "Description", "Gene.Name", and then the sample columns
  [Hint: you can use colnames(gene_exprs) to get a vector of the column names]
<details>
  <summary>Answer</summary>

  ```r
  # Method1
  gene_exprs_annotated1_reordered <- gene_exprs_annotated1[,c("Name", "Description", "Gene.Name", "Brain1", "Brain2", "Brain3", "Blood1", "Blood2", "Blood3")]
  head(gene_exprs_annotated1_reordered)
  # Method2
  gene_exprs_annotated1_reordered <- gene_exprs_annotated1[,c(1:2, 9, 3:8)]
  # Method3
  gene_exprs_annotated1_reordered <- gene_exprs_annotated1[,c(1:2, 9, grep("^(Blood|Brain)", colnames(gene_exprs)))]
  ```

  </details>
</details>
 

