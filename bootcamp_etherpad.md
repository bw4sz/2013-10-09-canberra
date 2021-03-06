# Welcome to the Canberra Software Carpentry Bootcamp  
***October 9th - 10th***
-------------------------------

Pleae enter you name on the right and join the discussion.

Please feel free to add notes to this etherpad during the workshop or after. If you have any questions for the instructors and/or helpers, please post them on the chat panel on the right. This etherpad will remain after the bootcamp and we'll also share a PDF copy with everyone.


---
GitHub repository for this bootcamp: https://github.com/swcarpentry/2013-10-09-canberra
xSchedule

---

Day 1
Welcome and introduction 9 - 9:20
Introduction to scientific programming with R 9:20 - 10
Break 10 - 10:20 
Data manipulation with R  10:20 - 12
Lunch 12 - 1 
Writing functions and other control structures 1 - 2 
Break 2 - 2:20
Writing functions and other control structures (cont) 2:20 - 3
Break 3 - 3:15
Data visualization in R 3:15 - 5

Day 2 


What follows are some basic headings to help you find the relevant place underwhich you might like to make notes and underwhich we'll post code etc as we go.


Introduction to scientific programming with R
=============================================


First make a new directory to store all the material you create.

Open your shell and type in:

```
mkdir bootcamp
cd bootcamp
```


**Save all your material and work here. We'll commit these changes to a version control repository on day 2.**


See links to all the material I demo'ed this morning here:
[https://github.com/swcarpentry/2013-10-09-canberra/tree/master/01-R-basics#introduction-to-the-r-language-and-r-ecosystem](https://github.com/swcarpentry/2013-10-09-canberra/tree/master/01-R-basics#introduction-to-the-r-language-and-r-ecosystem)

Each section is a link and all the code should be easy to copy and paste.

Please take 5 minutes to run through a simple exercise. 

[https://github.com/swcarpentry/2013-10-09-canberra/blob/master/01-R-basics/exercise01.md](https://github.com/swcarpentry/2013-10-09-canberra/blob/master/01-R-basics/exercise01.md)


Enclosing command in brackets will force it to print to screen

How to install Rdocumentation: 
[https://github.com/swcarpentry/2013-10-09-canberra/blob/master/01-R-basics/04-seeking-help.md#seeking-help](https://github.com/swcarpentry/2013-10-09-canberra/blob/master/01-R-basics/04-seeking-help.md#seeking-help)

## Answers to exercise 1
---------------------

```coffee
mtcars[-c(1,2,5), ]
```



**Functions**

```coffee
ls()
# This function takes 2 inputs, adds them and returns an output
# improving fn, adding defaults
add <- function(x = 1, y = 2) {
        x + y
}

add(1, 2)

add2 <- function(x, y, z) {
        x + y
}

add2(1,2)

n = 5
add4 <- function(x, y) {
        x + y + n
}

add4(1, 2)
```


--------


```coffee
cube <- max.power(3)
class(cube)
[1] "function"
square <- max.power(2)
class(square)
[1] "function"
```
      

```coffee
y <- rnorm(10)
mean(y)

if(mean(y) > 0) {
        print("y is greater than zero")
        }
        else {
        print("y less than zero")
        }
        
        
        
        y <- rnorm(10)
mean(y)

if(mean(y) > 0) {
        print("y is greater than zero")
        } else if(new_condition) {
        print("y less than zero")
        } else {
         # if nothing was met
 
 
 x <- rnorm(10)
for(i in x) {
        print(x[i])
}
```       
        
        
Please try this exercise after lunch:
[https://github.com/swcarpentry/2013-10-09-canberra/blob/master/03-functions/exercises.md](https://github.com/swcarpentry/2013-10-09-canberra/blob/master/03-functions/exercises.md)

Please work on questions 1 through 3. Skip 4 for now.


---



# functions exercise solutions


----

```coffee
# Write a function which takes a numeric vector as argument and calculates the mean of the vector.
my_mean <- function(vec) {
        total <- sum(vec)
        len <- length(vec)
        return(total/len)
}

x <- 1:100
my_mean(x)
mean(x)
```

----

**Write a function which takes a single numeric value X as argument and returns a logical value which is TRUE if X is larger than 15, or FALSE otherwise.**

```coffee
test_fn <- function(x) {
        if(x > 15) {
        TRUE
        } else {
        FALSE
        }
}


test_fn <- function(x) {
        ifelse(x > 15, TRUE, FALSE)
        # ifelse(condition,succesful_outcome, alternative)
}
```


----

**Extend the previous function by including an extra argument which sets the threshold (i.e. 15 in the previous question).**

```coffee
test_fn <- function(x, threshold = 15) {
        ifelse(x > threshold, TRUE, FALSE)
        # ifelse(condition,succesful_outcome, alternative)
}
test_fn(5)
# change the threshold
test_fn(5, 2)
```

----

manual way to do apply 


```
mean_iris <- function(dataset) {
        sepal_length <- mean(dataset$Sepal.Length)
        petal_length <- mean(dataset$Petal.Length)
        sepal_width <- mean(dataset$Sepal.Width)
        petal_width <- mean(dataset$Petal.Width)

        output <- data.frame(Species = unique(dataset$Species), sepal_length, petal_length, sepal_width, petal_width)
        return(output)
}
```

```
result1 <- mean_iris(sp1)
result2 <- mean_iris(sp2)
result3 <- mean_iris(sp3)
final_result <- rbind(result1, result2, result3)
```

----

More examples of apply: [https://github.com/swcarpentry/2013-10-09-canberra/blob/master/02-data-manipulation/02-apply-family.md#apply](https://github.com/swcarpentry/2013-10-09-canberra/blob/master/02-data-manipulation/02-apply-family.md#apply)


```
ddply(iris, .(Species), mean_iris)
     Species sepal_length petal_length sepal_width petal_width
1     setosa        5.006        1.462       3.428       0.246
2 versicolor        5.936        4.260       2.770       1.326
3  virginica        6.588        5.552       2.974       2.026
?ddply
?ddply
```

```
result <- ddply(iris, .(Species), function(x) {
data.frame(mean_sepal_length = mean(x$Sepal.Length))
})
```

Forget Cloning, do this
--------------
In R type the following 2 lines:

```
url <- "http://inundata.org/gapminderDataFiveYear.txt"
df <- read.delim(url)
```

Please look around the file
e.g.. `head(df), tail(df), str(df), names(df)`

Here is your exercise:https://etherpad.mozilla.org/swccanberra

Read the gapminderDataFiveYear.txt dataset in the data folder into an object. Split the data by continent and country, find the year with the highest life expectancy for each combination and return those results back into a data.frame.

Hints: 

Here is a function to find and return the row with the highest life expectancy.

```
hle <- function(data) {
    # we'll use a function called which.max to return the location of the max value.
    # try which.max(1:10). It returns 10 because that has the highest value.
    # note that I am returning the row with the highest life expectancy.
    return(data[which.max(data$lifeExp), ])
    }
```
    
Use this with the ddply. You can improve upon this function.     

**Solution**


[Read the gapminderDataFiveYear.txt dataset in the data folder into an object. Split the data by continent and country, find the year with the highest life expectancy for each combination and return those results back into a data.frame](https://github.com/swcarpentry/2013-10-09-canberra/blob/master/02-data-manipulation/02-apply-family.md#apply)

**Reading the data from the web**

```
url <- "http://inundata.org/gapminderDataFiveYear.txt"
df <- read.delim(url)
```


**Please run dim(df); str(df); names(df) to see all the attributes of the object**

```
names(df)
```

**Our goal is easy with ddply. Split this dataset by country and continent. Then for each piece (of data.frame), grab the one row with the highest life expectancy**

**We can do this with a function that we define.**

```
hle <- function(data) {
    # we'll use a function called which.max to return the location of the max value.
    # try which.max(1:10). It returns 10 because that has the highest value.
    # note that I am returning the row with the highest life expectancy.
    return(data[which.max(data$lifeExp), ])
    }

 result <- ddply(df, .(continent, country), hle)
 ```
---------------


--

# Problem 2

```coffee
# to download the data
url2 <- "http://inundata.org/mammals.csv"
mammals <- read.csv(url2, stringsAsFactors = FALSE, header = TRUE)
```


**From this data frame, split by Order_or_higher (there are 33 unique Orders), and for each piece, return a data.frame that contains the following information:**
Order_or_higher, mean(Mass_ln_g), max(Mass_ln_g), length/count of unique Species

**Hints: inside your function, format a data.frame. Use unique(), max(), min() and length() to find the outputs needed to compile the output to a data.frame**

Your result should have a dimension of 33  4.

Thanks to someone in the room, we've run into another complication. There aren't 33 unique (actual = 31) orders. Some are duplicates. 

```coffee
e.g. see > unique(mammals$Order_or_higher)
 [1] "Cimolesta"                        "Condylarthra"
 [3] "Arctostylopida"                   "Artiodactyla"
 [5] "artiodactyla"                     "Carnivora"
 [7] "Creodonta"                        "Dermoptera"
 [9] "Didelphimorphia"                  "Didelphimorphia\xca"
[11] "Didelphimorphia "                 "Dinocerata"
[13] "Eutheria incertae sedis"          "Lagomorpha"
[15] "Leptictida"                       "Lipotyphla"
[17] "Mesonychia"                       "Metatheria incertae sedis"
[19] "Multituberculata"                 "Multituberculata  incertae sedis"
[21] "Pantolesta"                       "Perissodactyla"
[23] "Pholidota"                        "Plesiadapiformes"
[25] "Primates"                         "Proboscidea "
[27] "Proboscidea"                      "Rodentia"
[29] "Spalacotheroidea"                 "Taeniodonta"
[31] "Tillodontia"                      "Triconodonta"
[33] "Xenarthra"
```

Artiodactyla is also a duplicate entry as artiodactyla (case mismatch)
Didelphimorphia is duplicated three times. These issues can occur during data transcription. Two things to fix:
a) Remove special characters from mammals$Order_or_higher
b) Capitalize first letter of each Order_or_higher

Then push through ddply. I'll provide a solution tommorow morning.

----
**Solution to the mammal problem.**

pseudocode: Read the data
            Clean the Orders_or_higher column 
            (remove extra spaces, extra characters, capitalize words)
            Then use ddply to split and create that data.frame
            
The library called "stringr" has a whole bunch of useful string functions. Things we're looking for are ones that can replace those unintended characters, strip out while spaces. We also need to find (or write) a function to capitalize words.            

```coffee
capwords <- function(s, strict = FALSE) {
         cap <- function(s) paste(toupper(substring(s, 1, 1)),
                       {s <- substring(s, 2); if(strict) tolower(s) else s},
                                  sep = "", collapse = " " )
         sapply(strsplit(s, split = " "), cap, USE.NAMES = !is.null(names(s)))
     }
     
# test out capwords
capwords("karthik")
# should return Karthikur12
str_trim("  Karthik  ")
# should also return karthik
# Now we can use str_split_fixed to split by a " " and return the first word
str_split_fixed("Karthik Ram", " ", 2)[[1]]
# will return Karthik     

# to get my pacakge with custom functions
library(devtools)
install_github("coyote", "karthikram")
# Source for lsp
# Karthik's function which lists the functions in a package:
lsp <- function(package, pattern, all.names = FALSE) {
    package <- deparse(substitute(package))
    ls(pos = paste("package", package, sep = ":"), all.names = all.names,
        pattern = pattern)
}
```


```coffee
clean_orders <- function(order_name) {
    order_name <- capwords(order_name)
    #order_name <- str_trim(order_name)
   # order_name <- str_sub(order_name, "\\\xca", "")
    # order_name <- str_split_fixed(order_name, " ", 2)[[1]]
    return(order_name)
 } 
 ```      


```
sapply(mammals$Order_or_higher, clean_orders, simplify = TRUE)
```



```coffee
result <- ddply(mammals, .(Order_or_higher), function(x) {
        unique_species_count <- length(unique(x$Species))
        mean_mass <- mean(x$Mass_ln_g)
        max_mass <- max(x$Mass_ln_g)
        Order_or_higher <- unique(x$Order_or_higher)
        return(data.frame(unique_species_count, mean_mass, max_mass, Order_or_higher))
})


install.packages("stringr")
apropos("<part of a function name>")
```

----------
## Shell


 git clone https://github.com/swcarpentry/2013-10-09-canberra
 
 For windows users
 
 ```
 cd C:
 ls
 cd C:/Users/Karthik\ Ram/Documents
```

To get manual pages if you're using Git Bash (where the 'man' command doesn't work), use this website

[http://man.he.net/](http://man.he.net/)

e.g. for the cp command, this is the documentation:
http://man.he.net/?topic=cp&section=all


# Introduction to Git
---------------------

Slides for this section: [http://karthikram.github.io/git_intro/](http://karthikram.github.io/git_intro/)
Notes for this section are here: [https://github.com/swcarpentry/2013-10-09-canberra/tree/master/06-version-control#introduction-to-git](https://github.com/swcarpentry/2013-10-09-canberra/tree/master/06-version-control#introduction-to-git)

Something for after the workshop - if you think that Git looks useful, but the commandline version doesn't quite do it for you, there are windows and Mac GUIs for GitHub:

[http://windows.github.com/](http://windows.github.com/)
[http://mac.github.com/](http://mac.github.com/)

```coffee
git config --global alias.st status 
git config --global alias.ci commit 
git config --global alias.co checkout 
git config --global alias.hist 'log --graph --decorate --pretty=oneline --abbrev-commit'
git config --global alias.ls 'log --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)[%an]%Creset" --abbrev-commit'
git config --global alias.ll 'log --pretty=format:"%C(yellow)%h%Cred%d %Creset%s%Cblue [%cn]" --decorate --numstat'

echo "first git folder" > README.md
git add README.md
git commit -m "Initial commit"
git status
```

**Some examples of how to git add**  

```
git add README.md
git add *.md
git add *.R

echo "here's another file" > script.R
git add script.R
git commit -m "Adding our first script"
git log
```

 **To add and commit a previously tracked  file, use **  
`git commit -am "commit message"`

 **the -a adds right before committing.**  

 **Basic git workflow**  
For a new project:
`git init`

 **To add a file**  
```
git add <file>
git add .
```

 **To  commit change**  

`git commit`
 **pressing enter will launch default editor**  

 **to skip editor**  
`git commit -m "message"`

 **To add changes to previously tracked file and commit at same time**  

`git commit -am "message"`

----------
For the afternoon, follow along here: 
[http://pcottle.github.io/learnGitBranching/?NODEMO](http://pcottle.github.io/learnGitBranching/?NODEMO)


**Merging**

# Documenting how to merge git.

To merge documents on Git, checkout a branch, then type in:

git merge <other branch>
  

---

# Visualization with ggplot2

[https://github.com/swcarpentry/2013-10-09-canberra/tree/master/04-data-visualization](https://github.com/swcarpentry/2013-10-09-canberra/tree/master/04-data-visualization)

```coffee
library(reshape2)
result <- melt(iris, id.var = "Species")
first_plot <- ggplot(iris, aes(Sepal.Length, Sepal.Width))

summary(first_plot)

first_plot <- first_plot + geom_point()
```

# Line plot

```coffee
climate <- read.csv("http://inundata.org/climate.csv", header = TRUE)

head(climate)
    X   Source Year Anomaly1y Anomaly5y Anomaly10y Unc10y
1 102 Berkeley 1901        NA        NA     -0.162  0.109
2 103 Berkeley 1902        NA        NA     -0.177  0.108
3 104 Berkeley 1903        NA        NA     -0.199  0.104
4 105 Berkeley 1904        NA        NA     -0.223  0.105
5 106 Berkeley 1905        NA        NA     -0.241  0.107
6 107 Berkeley 1906        NA        NA     -0.294  0.106

ggplot(climate, aes(Year, Anomaly10y)) + geom_line()


ggplot(climate, aes(Year, Anomaly10y))  + 
geom_ribbon(aes(ymin = Anomaly10y - Unc10y, ymax = Anomaly10y + Unc10y)) + 
geom_line(size = 1, color = "steelblue")

# Now let's make the ribbon a little bit transparent

ggplot(climate, aes(Year, Anomaly10y))  + 
geom_ribbon(aes(ymin = Anomaly10y - Unc10y, ymax = Anomaly10y + Unc10y), alpha = 0.1) + 
geom_line(size = 1, color = "steelblue")


ggplot(climate, aes(Year, Anomaly10y))  + 
geom_ribbon(aes(ymin = Anomaly10y - Unc10y, ymax = Anomaly10y + Unc10y), alpha = 0.1) + 
geom_line(size = 1, color = "steelblue") + theme_bw() + ggtitle("Berkeley climate uncertainty data")
```

Plot ala Pete...  

```coffee
example_plot <- ggplot(climate, aes(Year, Anomaly10y)) +
  geom_line(aes(Year, (Anomaly10y - Unc10y)), size = 1, color = "red", linetype = "dashed") + 
  geom_line(aes(Year, (Anomaly10y + Unc10y)), size = 1, color = "red", linetype = "dashed") + 
  geom_line(size = 1, color = "black") + theme_bw() + 
  ggtitle("Berkeley climate uncertainty data")
example_plot
```

```coffee
# pseudocode for a plot function (not tested)
    uncertainty_plot <- function(data, v1, v2, def_title="", geom = "point") {
        if(geom == "point") {
    ggplot(data, aes(v1, v2)) + geom_point() + ggtitle(title)
    } else { 
         ggplot(data, aes(v1, v2)) + geom_line() + ggtitle(title)
     }
    }

uncertainty_plot(climate)
```

**Academic accounts for GitHub**

github.com/edu









 















































