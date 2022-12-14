# Basic R Syntax, Data Types, and Structures {#ch5}

In this chapter: 

- Basic R syntax and conventions 

- Base R arithmetic, logical, and Boolean operators 

- Assigning values to objects 

- Data types, structures, and aggregation 


## Writing things in R 

Given that the last chapter gave you the tools to open an R script, you are now ready to get started with writing some basic code. Let's get started first with some basics on how R operates. R is a mixed programming code that relies on *objects and functions* to perform user-designated operations. These operations provide an output for our interpretation. We can think of objects like nouns-- the 'things' we care to analyze; functions are like verbs-- the 'actions' we want to do with our objects. 

Bringing it back to the potato example from the [first chapter](#intro), the variable `potatoes` is an object. Anything you ask R to do with the variable `potatoes` is a function. For example, you might want to know what type of variable `potatoes` is. You would then use the appropriate function `class` to get this answer. To get objects and functions to interact, you must nest the object into the function call, as shown in the code chunk below. R then responds back with the appropriate answer-- which, in this case, you will find that the `potatoes` variable is of class character. 




```r
class(potatoes)
```

```
## [1] "character"
```
### Some additional conventions


## Operators 

### Arithmetic Operators 

Thankfully, R makes use of some already common operators to perform basic mathematical tasks before having to rely on more complex function calls. 

Arithmetic operators will form the basis of most math functions; logical operators will be useful to separate out objects while using functions or operators. You are probably familiar with most of the base arithmetic operators: 


|Operator |Use                           |
|:--------|:-----------------------------|
|+        |Addition                      |
|-        |Subtraction                   |
|*        |Multiplication                |
|/        |Division                      |
|^        |Expontentiation               |
|x %% y   |Modulus (Finding a remainder) |
|x %/% y  |Integral Division (uncommon)  |
|X %*% Y  |Matrix Multiplication         |

Using the operators standalone means that we can use R as a glorified calculator. The system will perform whatever mathematical operation that you run, following algebraic order of operations, or PEMDAS. For example, you can input the following arithmetic into either the R console or run in a script to obtain the following answers: 


```r
4*3^2 
```

```
## [1] 36
```

```r
(4*3)^2
```

```
## [1] 144
```

```r
100-45+24/2
```

```
## [1] 67
```

```r
(100-45+24)/2
```

```
## [1] 39.5
```

```r
24%%2
```

```
## [1] 0
```

If any of the answers returned by R are puzzling or you are unsure why certain answered were obtained based on slight differences, it may be time to check up on your arithmetic skills based on (Chapter X)[other book] in the accompanying textbook. 

### Boolean and Logical Operators 

Logical and Boolean operators are also important to coding in R. Sometimes you will need to separate or join data in logical ways. Or, you might want to index through data to find if certain conditions about the data are true. Below is a list of the most common Logical and Boolean operators and what they indicate. 


|Operator |Use                      |
|:--------|:------------------------|
|&#124;   |Or                       |
|&        |And                      |
|!        |Not                      |
|==       |Equals                   |
|!=       |Does not equal           |
|<        |Less than                |
|>        |Greater than             |
|>=       |Less than or equal to    |
|<=       |Greater than or equal to |
|%in%     |Is in the set            |

As mentioned, these operators are good tools to partition or join data, as well as setting conditions on operations. We will get more into what that means later, but for now here are some examples of how these operators work to render logical results. 


```r
10^10 == 100^5
```

```
## [1] TRUE
```

```r
(10^10 == 100^5) | (10^10 != 100^5)
```

```
## [1] TRUE
```

```r
150 >= 157
```

```
## [1] FALSE
```

Notice how the output is simply a logical analysis as to whether the statement evaluated is `TRUE` or `FALSE`. Furthermore, these operations will similarly follow an order of operations as with the arithmetic operators. 

## Objects and Data Types 

In the previous sections, we went over how to perform simple operations using R. However, none of the output rendered was saved for later use. This makes things difficult over time or as your data get larger and more complex. Aside from R's use as a glorified calculator, R is also a flexible data storage container. It is flexible in the sense that we can easily assign, arrange, and change data that we can assign to objects of our own naming. 

Objects in R may store data of many different arrangements -- simple values, variables with multiple values, data frames containing multiple variables, and more. Generally then, objects are an easy way to store and recall data with some implicit meaning. 

To create these objects, you must assign value to a variable name using `<-`. For example, let's say I want to assign the year `1995` to the variable name `my_birthday`. To do so I will simply type the intended variable name, the assignment operator, and the relevant value. To make sure that the variable has saved as intended, you can run the code `print(my_birthday)` to double check the output. 


```r
my_birthday <- 1995 
print(my_birthday)
```

```
## [1] 1995
```

Note how I have done this assignment from left-to-right. This is not necessary, but it is the strong norm except in certain relevant cases for assignment in R. 

Just as with the arithmetic performed above with actual numbers, these same operations can be performed on variables. Let's say you also stored the year `1998` in a variable named `sib_birthday`. To calculate the difference in birth years, you can neatly subtract them from each other.

**Challenge**: You can also place the arithmetic operations with these variables into a function. Let's say that you want R to return the absolute value of the difference. To do so, you can simply put the desired arithmetic operation with the variable names into the function call `abs()` as shown in the code below. How does this differ from the previous answer where the output did not specify the absolute value? 


```r
sib_birthday <- 1998 
my_birthday - sib_birthday
```

```
## [1] -3
```

```r
abs(my_birthday - sib_birthday)
```

```
## [1] 3
```

## Data Structures 

This section contains information adapted from Hadley Wickham' [Advanced R](http://adv-r.had.co.nz/Introduction.html). 

The values that you assign to objects can be composed of different types of data to create different data structures. We will classify data structures in R based on their dimensionality and whether the data that they contain are homogenous (all data are the same type) or heterogenous (the data are different types). See the below table to understand this classification system, then we'll go into detail on each of the potential structures and how they fit together.  


|Dimensions |Homogenous    |Heterogenous |
|:----------|:-------------|:------------|
|1          |Atomic Vector |List         |
|2          |Matrix        |Data Frame   |
|N          |Array         |             |

### Atomic Vectors 

Atomic vectors are the most basic variable component in R. In the table above, you will see that atomic vectors are unidimensional and homogenous. This means that a sequence of a single type or class of data compose a vector.

We can ask R to tell us what type of atomic vector our data are in two ways: 
1. Ask for `typeof()`, in which case the output is the class of the vector. 

2. Specifying a logical function to tell us if a vector *is* or *is not* a certain class. In this case, the output is a logical `TRUE` or `FALSE`.
  

### List 

A list is a less likely data structure compared to atomic vectors, but might become more common as you start assembling and cleaning your own data. Lists are unidimensional and heterogenous. Therefore, lists have different *classes* of data, but are only composed of the single dimension of elements. 


```r
list_example<-as.list(c('gray', 44.8, 67.9, 'purple', 210.4))

typeof(list_example)
```

```
## [1] "list"
```


### Matrices and Arrays 


### Data Frame 

Data frames are likely the most common type of data structure that you will encounter in actual data analysis. Data frames are multi-dimensional, heterogenous structures. This means that data frames for different types of data across both rows and columns. Furthermore, the multi-dimensional nature of data frames also allows for us to give our data meta-data of sorts, such as names and labels. 
