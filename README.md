# Class


- [Introduction to Programming in R](#introduction-to-programming-in-r)
  - [Setup](#setup)
  - [Project Structure](#project-structure)
    - [Git](#git)
    - [Docker](#docker)
    - [Codespaces](#codespaces)
    - [RStudio Cloud](#rstudio-cloud)
  - [Class Plan](#class-plan)
    - [Week 1](#week-1)
    - [Week 2](#week-2)
    - [Week 3](#week-3)
    - [Week 4](#week-4)
    - [Week 5](#week-5)
    - [Week 6](#week-6)
  - [Instructor Bio](#instructor-bio)

<!-- README.md is generated from README.Rmd. Please edit that file -->

# Introduction to Programming in R

<!-- badges: start -->
<!-- badges: end -->

Welcome to Introduction to Programming in R at [Columbia Business
School](https://academics.business.columbia.edu/phd/academics/dro). This
repo has information to properly setup your environment.

## Setup

For this course you need a recent version of R. Anything greater than
4.1 is good but 4.4.1 is even better. I also highly recommend using your
IDE/code editor of choice. Most people use either
[RStudio](https://www.rstudio.com/products/rstudio/) or [VS
Code](https://code.visualstudio.com/) with [R Language
Extensions](https://code.visualstudio.com/docs/languages/r).

After you have R and your favorite editor installed, you should install
the packages needed for this class with the following line of code. You
can copy and paste it into the R console.

<div class="wrapMe sourceCode r">

    install.packages(c('here', 'markdown', 'rmarkdown', 'knitr', 'tidyverse', 'ggthemes', 'ggridges', 'tidymodels', 'coefplot', 'glmnet', 'xgboost', 'vip', 'DiagrammeR', 'here', 'DBI', 'themis', 'vetiver', 'fable', 'tsibble', 'echarts4r', 'leaflet', 'leafgl', 'leafem', 'tictoc'))

</div>

## Project Structure

To make your life easier, you should have a folder for just this class,
you could call it `r_class`. The structure should looke like this.

    .
    ├── cbs2024fall.Rproj
    ├── code
    │   └── code.md
    └── data
        └── data.md

All the code you write will go in the `code` folder within this folder.
And all of the data files will go in the `data` folder.

You can either create it yourself or follow one (**and only one**) of
the methods below.

### Git

If you are comfortable with git, you can clone this repo and the project
structure will be all set for you.

``` sh
git clone https://github.com/jaredlander/cbs2024fall.git
```

This includes the `{renv}` lock file, so you can install all the
packages with the following R code.

``` r
renv::restore(repos=c('https://torch-cdn.mlverse.org/packages/cu118/0.13.0', 'https://packagemanager.posit.co/cran/latest'))
```

### Docker

If you are having trouble installing R or the packages, but are
comfortable with Docker, you can pull the Docker image using the
following command in your terminal.

``` sh
docker pull jaredlander/r-ml:cpu-4.4.1
```

You can run the container with the following command which will also
mount a folder as a volume for you to use.

``` sh
docker run -it --rm --name rstudio_ml -e PASSWORD=password -e ROOT=true -p 8787:8787 -v $PWD/workshop:/home/rstudio/workshop jaredlander/r-ml:cpu-4.4.1
```

Then if you visit port 8787 at the URL for your machine (likely
<http://localhost:8787>) then enter rstudio/password for your
credentials, you will have an RStudio interface.

All of the needed R packages will already be installed.

### Codespaces

The Docker image should work natively in [GitHub
Codespaces](https://github.com/features/codespaces) so you can run a
remote instance of VS Code with all the packages ready to go. You can
theoretically even launch RStudio from within the VS Code instance,
though I haven’t figured that out yet.

To launch Codespaces, first click the green `Code` button at the top of
this page.

![Green Code Button](images/github-code-button.png)

Then click where it says `Codespaces` then the green
`Create codespaces on main` button.

![Green Codespaces Button](images/github-codespaces-button.png)

This will open an instance of VS Code in the browser that will give you
R, all the packages and even the code we write during this workshop. You
can even attach to this image from VS Code on your own computer.

Be sure to stop the codespace when you are done so you do not get
charged.

### RStudio Cloud

If you are still having trouble setting up the project and getting
everything installed, sign up for an
[RStudio.cloud](https://rstudio.cloud/) account,.

## Class Plan

This is the general plan for the class though we may adapt as we
progress through the class.

### Week 1

#### Introduction to R

- The RStudio Interface
- Basic Math
- Assigning Variables
- Working Directories
- Relative Paths
- Reading Data
  - Read from text files with
    [readr](https://www.rdocumentation.org/packages/readr/)
  - Read from Excel files with
    [readxl](https://www.rdocumentation.org/packages/readxl/)
- Writing Functions

#### RMarkdown

- [RMarkdown](https://rmarkdown.rstudio.com/) Primer
  - Sections
  - Text Formatting
  - Lists
  - Links
- Integrating R into Markdown
  - Chunk Options
- Including Figures
- Output Formats
  - HTML
  - PDF
  - Word
- Presentations

### Week 2

#### Data Manipulation with [dplyr](https://www.rdocumentation.org/packages/dplyr/)

- Understanding a
  [tibble](https://www.rdocumentation.org/packages/tibble/topics/tbl)
- Use [pipes](https://magrittr.tidyverse.org/) for cleaner code
- Select columns with
  [select](https://www.rdocumentation.org/packages/dplyr/topics/select)
- Filter rows with
  [filter](https://www.rdocumentation.org/packages/dplyr/topics/filter)
- Change and create columns with
  [mutate](https://www.rdocumentation.org/packages/dplyr/topics/mutate)
- Calculate summary statistics with
  [summarize](https://www.rdocumentation.org/packages/dplyr/topics/summarize)
- Group data for calculations with
  [group_by](https://www.rdocumentation.org/packages/dplyr/topics/group_by)
- Joins with
  [left_join](https://www.rdocumentation.org/packages/dplyr/topics/left_join)

#### Creating Visualizations

- [ggplot2](https://www.rdocumentation.org/packages/ggplot2/) paradigm
- Aesthetics
- Scatter plots
  - Color Coding
  - Size
  - Shape
  - Opacity
- Small multiple plots
- Histograms
- Density Plots
- Combining Layers
- Violin Plots
- Themes

### Week 3

#### Reading Data

- CSVs with [readr](https://www.rdocumentation.org/packages/readr/)
- Databases with [DBI](https://www.rdocumentation.org/packages/DBI/)
- JSON with
  [jsonlite](https://www.rdocumentation.org/packages/jsonlite/)
- Scraping web pages with
  [rvest](https://www.rdocumentation.org/packages/rvest/)

#### Iterate Over Lists with [purrr](https://www.rdocumentation.org/packages/purrr/)

- Basics of functional programming
- Mapping over a list
- Difference from
  [lapply](https://www.rdocumentation.org/packages/base/topics/lapply)
- Consistent Data Types
- Mapping to different data types
  - `chacracter`
  - `numeric`
  - `data.frame`
- Mapping functions with multiple arguments

#### Reshaping Data

- Convert from wide to long with
  [pivot_longer](https://www.rdocumentation.org/packages/tidyr/versions/1.2.0/topics/pivot_longer)
- Convert from long to wide with
  [pivot_wider](https://www.rdocumentation.org/packages/tidyr/versions/1.2.0/topics/pivot_wider)

### Week 4

#### Linear Models

- Simple Linear Model with
  [lm](https://www.rdocumentation.org/packages/stats/topics/lm)
- The Formula Interface
- Multiple Regression
- Tidying models with
  [broom](https://www.rdocumentation.org/packages/broom/)
- Visualizing models with
  [coefplot](https://www.rdocumentation.org/packages/coefplot/)

#### Generalized Linear Models

- Logistic Regression for Binary Data
- Poisson Regression for Count Data
- Quasipoisson Regression for Overdispersed Count Data

#### Assessing Model Quality

- AIC
- BIC

### Week 5

#### Cross-Validation

- Use Cross-Validation for Model Assessment

#### Penalized Regression

- L1 Penalty (Lasso)
- L2 Penalty (Ridge)
- Implement via the Elastic Net with
  [glmnet](https://www.rdocumentation.org/packages/glmnet/)
- Tuning Hyperparameters

#### Boosted Trees

- Decision Trees
- Boosted Trees
- Fit Model with
  [xgboost](https://www.rdocumentation.org/packages/xgboost/)

### Week 6

#### Forecasting Time Series Data

- Time Series formats
  - ts
  - xts
  - tsibble
- Visualizing Time series
- Benchmark Models
  - mean
  - naive
  - random walk
- Advanced Models
  - ETS
  - ARIMA
- Model Fitting
- Model Evaluation
  - AICc
  - Time Series Cross Validation
- Forecasting

## Instructor Bio

Jared P. Lander is Chief Data Scientist of [Lander
Analytics](https://www.landeranalytics.com), the Organizer of the [New
York Open Statistical Programming Meetup](https://www.nyhackr.org) and
the [New York R](https://rstats.ai/nyc) and [R in
Government](https://rstats.ai/gov) Conferences, an Adjunct Professor at
[Columbia Business School](https://business.columbia.edu/). With a
masters from [Columbia University](https://www.columbia.edu) in
statistics and a bachelors from [Muhlenberg
College](https://www.muhlenberg.edu) in mathematics, he has experience
in both academic research and industry. He is the author of [R for
Everyone](https://amzn.to/4e1Q6HI) (now in its second edition), a book
about R Programming geared toward Data Scientists and Non-Statisticians
alike and a Series Editor for his publisher, Pearson. Additionally, he
is an [R Consortium Board Member](https://www.r-consortium.org/). Very
active in the data community, Jared is a frequent speaker at
conferences, universities and meetups around the world. His writings on
statistics can be found at [jaredlander.com](https://jaredlander.com)
and his work has been featured in publications such as
[Forbes](https://www.forbes.com/sites/prishe/2017/03/07/reflections-from-the-2017-mit-sports-analytics-conference/#1a95a3473f75)
and the [Wall Street
Journal](https://www.wsj.com/articles/a-data-scientist-dissects-the-2016-nfl-draft-1461793878).
