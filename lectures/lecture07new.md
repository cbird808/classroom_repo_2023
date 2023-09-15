# Week07 R Data Visualization w/ Tidyverse R Package

![](https://d33wubrfki0l68.cloudfront.net/795c039ba2520455d833b4034befc8cf360a70ba/558a5/diagrams/data-science-explore.png)

###  Assignment 6 is due by beginning of class (complete Mind Expanders 8.2-8.5)

### [Lecture Stream]()

___

## Computer Preparation

You are expected to start this lecture with R Studio open with a fresh and empty text document in the upper left panel and an empty environment.  If R Studio was open on your computer, close it and open it again.

```R
# clear all variables from environment
rm(list = ls())
```

### *_PLEASE INSTALL TIDYVERSE IN R STUDIO AS SOON AS YOU READ THIS_*

```
# RUN THE FOLLOWING LINE IN THE CONSOLE (LOWER LEFT PANEL)
install.packages("tidyverse")

# ADD THE FOLLOWING LINE TO YOUR TEXT DOCUMENT (UPPER LEFT PANEL), THEN EXECUTE IT (CTRL-ENTER)
library(tidyverse)
```

### *_GENERAL COMPUTER SETUP (SHOULD ALREADY BE DONE)_* 

<details><summary>Ubuntu on Windows</summary>
<p>

  * If the Windows Terminal or Ubuntu app are not installed, then follow [these instructions](../resources/README.md)

  * Open an Ubuntu window in Windows Terminal.  _We will not use `gitbash` unless you can't get Ubuntu running._ After logging in, You are in your home directory.

  * It's always a good idea to keep your apps in `Ubuntu` up to date. _The first time you do this, it could take a long time to finish. After that, if you do this when you log in, it should go quickly._
    ```bash
    sudo apt update
    sudo apt upgrade
    ```

</p>
</details>

<details><summary>MacOS</summary>
<p>

  * Open a terminal window

  * If you haven't already, install [homebrew](https://brew.sh/).  You will be able to use homebrew to install linux software, such as `tree`, which is used in the slide show.


</p>
</details>


<details><summary>If it's not already there, clone the CSB repository to your home dir</summary>
<p>

We will use the [open source files that accompany the CSB text book](https://github.com/tamucc-comp-bio-2022/CSB) in lectures and assignments.

If the `CSB` directory does not exist in your home directory (check with `ls`), then run the following code to clone the [`CSB` repository](https://github.com/tamucc-comp-bio-2022/CSB) into your home directory:

1. Open a terminal window
	* For Win laptops, use `Windows Terminal` to open Ubunutu.  
	* For Mac laptops, open your `Terminal`.

2. Run the code line by line in the code block below
```bash
# check that you're in home dir, you should be there when you log in
pwd

# if you are not in your home dir, then move there
cd ~

# if pwd does not return `/home/yourusername` then let Dr. Bird know
pwd

# clone the CSB repository to your home dir
git clone git@github.com:tamucc-comp-bio-2022/CSB.git
```

The repository is named CSB, and it contains all of the example files and directories necessary to conduct the exercises in the text book.

</p>
</details>

[If you have not already, install R](../resources/install_r.md)

[If you have not already, install RStudio](../resources/install_rstudio.md)



---

## [I. Lecture Slides](Week07_files/ggplot2_1.pptx)

---

## II. Review Material Covered for Homework



<details><summary>Copy the `r` dir to your repo</summary>
<p>

Start the assignment by copying the `r` dir from the `CSB` repo to your homework repo.


---

</p>
</details>


<details><summary>Use the Pseudocode and Solutions</summary>
<p>
The first key to completing the exercise is using the information provided to you in the `CSB/r/solutions` repository


### `WilmesUnpub_pseudo.md`

#### Hints and pseudo code for Exercise 8.23.3 (Wilmes, unpublished)

1. Write a `for` loop that processes all images using the function `getArea` that is provided in `CSB/r/solutions/getArea.R`. The function accepts a single file name as argument, and returns the projected leaf area, measured in pixels. Your loop should record the leaf area for each image, and store it in the data frame `results`. To loop over all files, you can use the function `list.files` along with its pattern matching option, to produce a list of all the files with extension `.JPG` in the directory `CSB/r/data/leafarea/`. Work in your `sandbox` or change paths in the `getArea.R` function accordingly.

2. Plot the area of each plant as measured on time point 1 versus time point 2.

3. Determine if the plants significantly differ at time point 1 and 2 using a paired t-test.


**Hints**: 

- you will need to install the EBImage package and load it. You can use the code:

```r
# install the EBImage package: run the following two commands
source("http://bioconductor.org/biocLite.R")
biocLite("EBImage")
# note that to install EBImage, you might need to install other libraries


# now load the library
library(EBImage)
```

- create an empty `data.frame` to record results

```r
results <- data.frame(JPG = character(), 
                      area = numeric(), 
                      stringsAsFactors = FALSE)
```

- the function `list.files` can be used to list all the files in a directory

- write a `for` loop and call the `getArea` function for each file; store the area in the data frame.

- to extract the information on time point and plant name, parse the file name

- to run a t-test in `R`, simply call `t.test`

---

Following the hint given above, we run the following

```R
> source("http://bioconductor.org/biocLite.R")
Error: With R version 3.5 or greater, install Bioconductor packages using BiocManager; 
see https://bioconductor.org/install
```

If you follow the instructions given in the error message, you will find that bioconductor can now be installed with the package manager

```R
> install.packages("BiocManager")
Installing package into ‘C:/Users/cbird/Documents/R/win-library/4.0’
(as ‘lib’ is unspecified)
trying URL 'https://cran.rstudio.com/bin/windows/contrib/4.0/BiocManager_1.30.10.zip'
Content type 'application/zip' length 100063 bytes (97 KB)
downloaded 97 KB

package ‘BiocManager’ successfully unpacked and MD5 sums checked

The downloaded binary packages are in
	C:\Users\cbird\AppData\Local\Temp\RtmpOGXlUN\downloaded_packages
```

And then we can load the package using `library`

```R
> library(BiocManager)
Bioconductor version 3.11 (BiocManager 1.30.10),
  ?BiocManager::install for help
```

Continuing from the bioconductor website, with an eye on the pseudocode hints, we see that there is a new way to load the `EBImage` bioconductor library. biocLite has been depricated (scroll to bottom of bioconductor page to see).

_Note that we prefix the `install` command with `BiocManager::`.  We did this because `install` could be a function in another R package.  When this is a concern, you can add the name of the package for the command you want to run to make sure the correct function is run. 5% of mysterious R behavior is caused by different packages having functions with the same name but the user does not realize it._

```R
BiocManager::install("EBImage")
```

#### To review, the following lines should be in your text editor panel, documenting how you installed the `EBImage` library from bioconductor.

```R
install.packages("BiocManager")
library(BiocManager)
BiocManager::install("EBIimage")
library("EBImage")
```

---

</p>
</details>

<details><summary>Begin Answering the First Question</summary>
<p>

#### Now we can continue addressing the question 

```R
# make sure you are in the right working diretory, `r/sandbox`
setwd(dirname(rstudioapi::getActiveDocumentContext()$path))

# source the getArea.R function
source("../solutions/getArea.R")

# make list of files to processes
files <- list.files("../data/leafarea", 
                    pattern = ".JPG")

# create a data frame to record results
results <- data.frame(JPG = character(), 
                      area = numeric(), 
                      stringsAsFactors = FALSE)

# run function getArea on all images
for (f in files) {
    area <- getArea(f)
    results[nrow(results) + 1, ] <- c(f, area)
}

# convert the area column in the results data frame to numeric data
results$area <- as.numeric(results$area)
```

_Note that it is poor form to write a function with dependencies, like `EBImage`, without including the code to install and load the package in the script.  This is the fault of the script author, but you will find that the onus falls on you to solve these types of issues with open source software. Imagine if you had to write the function from scratch; it is usually easier to troubleshoot an existing script that is theoretically function with a little tweaking._

---

</p>
</details>

<details><summary>Second Question</summary>
<p>


#### Next we extract information from the file names to rearrange the data frame

Let us break down what is about to happen.  The function `substr()`, which is short for substring, is being applied to the `JPG` column in `results`.  If you type `substr` into the help panel (lower right) you will see what the 1 and 2 mean.

```R
# extract time point information and save into new column called tp then make the tp datatype be a factor
results$tp <- substr(results$JPG, 1, 2)
results$tp <- as.factor(results$tp)
```

The `sapply` function is fast for loop.  The vector given to the loop is column `JPG`. One by one, each value in the column is stored into the variable `x` and then the commands `unlist(strsplit(x, "[_]|[.]"))[2])` are run on `x`.  

A function called `strsplit` can be used to break up the file names by delimiters (characters that signify a column break). Here we use the `_` and `.` to break up the name and then select the second "column" to keep.  `strsplit()` outputs a list, so the `unlist()` command is used to convert that list to a vector, and then we grab the second element in the vector `[2]`, which is the plant information

```R
# extract plant information
results$plant <- sapply(results$JPG, 
                        function(x) unlist(strsplit(x, "[_]|[.]"))[2])
results$plant <- as.factor(results$plant)
```

#### And then we can plot the results

Here, we will use base R to make a plot, and then we will give you a taste of "the tidyverse" by using `ggplot` to make the figure.

```r 
# rearrange data into vectors for plotting
tp1 <- results[results$tp == "t1", ]$area
tp2 <- results[results$tp == "t2", ]$area

plot(tp2 ~ tp1, 
     xlab = "Projected leaf area, tp1", 
     ylab = "Projected leaf area, tp2")
abline(c(0,1)) # add the 1-to-1 line
```

*_[`Tidyverse`](https://www.tidyverse.org/) to the rescue!_*

We will learn more about how this all works, for now, marvel at the power of the [`Tidyverse`](https://www.tidyverse.org/)

```r 
library(tidyverse)
results %>%                                   # the %>% is a pipe, in bash it was |
  select(-JPG) %>%                            # remove the JPG column, we have to remove this col for the next command to work
  pivot_wider(names_from = tp, 
              values_from = area) %>% # pivot_wider makes columns named according to the unique names in the tp col and fills them with the values from the area column
  ggplot(aes(x=t1, 
             y=t2)) +                   # assign data to plot elements, in ggplot, the + means more ggplot settings follow on next line
    geom_point(color="red4") +                # visualize the data with points
    geom_abline(linetype = "dashed") +        # draw y=x line
    labs(y="Projected leaf area (time 2)",    # edit the labels
         x="Projected leaf area (time 1)",
         title = "Change in Leaf Area",
         subtitle = "Tidyverse >> Base R") +
    theme_classic()                           # make it pretty
```

---

</p>
</details>

<details><summary>Third Question</summary>
<p>


#### Lastly, run the statistical test, using Base R

```r 
> t.test(tp1, 
         tp2, 
         paired = TRUE, 
         alternative = "less")

	Paired t-test

data:  tp1 and tp2
t = -20.01, df = 21, p-value = 1.856e-15
alternative hypothesis: true difference in means is less than 0
95 percent confidence interval:
      -Inf -6486.002
sample estimates:
mean of the differences 
              -7096.227
```

---

</p>
</details>

---

## III. [`Tidyverse`](https://www.tidyverse.org/) Data Visualization w/ `ggplot2`

 R packages for data science

The tidyverse is an opinionated collection of R packages designed for data science. All packages share an underlying design philosophy, grammar, and data structures.

Today, I am going to project a ppt slide show.  I would like you to set up R Studio as follows:

* download the [`data_visualization_ggplot2.R`](Week07_files/data_visualization_ggplot2.R) script which has the code from the ppt slides

  * move `data_visualization_ggplot2.R` into your `CSB/data_wrangling/sandbox` dir
  
  * open `data_visualization_ggplot2.R` in R Studio, and execute the lines as we go in the ppt.


---


## Mind Expanders

Complete the following mind expanders:

[Mind Expander 9.5](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUOE9LM0ZWOUZWVlZTUzBKQkZaUkcwRVg4Qy4u)

[Mind Expander 9.6](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlURDFBNlc2UFFEOVJVMEpaWVZJWkJJNEc1US4u)

---

## Homework 

* Complete the Lecture Slides and [Mind Expander 9.6](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlURDFBNlc2UFFEOVJVMEpaWVZJWkJJNEc1US4u)

* Complete the [Assignment 7 Questions](https://classroom.github.com/a/G7cmolw_)
	* clone this repo to your computer, update the R script, then push the changes to github

