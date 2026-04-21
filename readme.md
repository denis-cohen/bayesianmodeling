
# Bayesian Modeling: From Foundations to Custom Solutions

Denis Cohen  
<denis.cohen@uni-mannheim.de>

*Version: GESIS Training Program, April 2026*

## Abstract

Bayesian methods have become increasingly central to the social sciences
and many adjacent fields. Once a niche methodology with steep
computational and software entry barriers, Bayesian statistics is now a
readily accessible toolbox available through user-friendly interfaces in
R. Yet, despite the growing popularity of these methods, many
researchers remain unsure when and why to use Bayesian approaches, how
to interpret their results, and how to move beyond standard
pre-implemented model types toward custom solutions.

This four-day workshop, spread across two weeks, provides an integrated
path from foundations to custom applications of Bayesian modelling. The
first half introduces participants to the core ideas and workflow of
Bayesian statistics, juxtaposing Bayesian and frequentist perspectives,
covering estimation, inference, and prediction, and demonstrating how to
use the R package brms for applied Bayesian modelling with minimal
coding effort. The second half then opens the black box: participants
learn how to build their own Bayesian models in Stan, the probabilistic
programming language underlying brms. Through a combination of
conceptual input, guided lab sessions, and hands-on coding exercises,
participants will gain both the theoretical grounding and practical
skills to understand, use, and design Bayesian models for their own
research questions—ranging from straightforward applications to fully
custom model specifications.

By the end of the course, participants will be familiar with the
Bayesian workflow, fluent in interpreting and diagnosing Bayesian models
in R, and capable of implementing tailored modelling solutions in Stan
that go beyond the limits of off-the-shelf packages.

## Software Requirements

This workshop requires installations of recent versions of
[`R`](https://cran.r-project.org/mirrors.html),
[`RStudio`](https://rstudio.com/products/rstudio/download/#download), as
well as the packages
[`rstan`](https://cran.r-project.org/web/packages/rstan/index.html),
[`brms`](https://cran.r-project.org/web/packages/brms/index.html) (which
depends on `rstan`), and
[`marginaleffects`](https://cran.r-project.org/web/packages/marginaleffects/index.html).

Setting up `rstan` can be somewhat time-consuming as it requires the
installation of a free-of-charge C++ compiler. Before the workshop,
participants should follow [these
instructions](https://github.com/stan-dev/rstan/wiki/RStan-Getting-Started)
on the Stan Development Team’s GitHub to install and configure the
`rstan` package and its prerequisites on their operating system. If you
do not have administrator privileges on your machine, please approach
your system administrator in advance of the workshop. Should you
encounter problems, feel free to send me an email.

## Course Structure

### Week 1

| Session | Topics |
|:---|:---|
| **Day 1 (April 16): Bayesian and frequentist inference - A juxtaposition** |  |
| **Morning session I (9:00-10:30)** | Introduction |
|  | Refresher on R and frequentist inference |
|  | Limitations of frequentist inference |
| **Morning session II (10:45-12:15)** | Fundamental concepts in Bayesian inference |
|  | Analytical Bayes |
|  | Numerical Bayes via Markov-Chain Monte Carlo sampling |
| **Afternoon session (13:45-15:15)** | Group exercises |
|  | Solutions and discussion |
| **Day 2 (April 17): Applied Bayesian statistics - A gentle introduction** |  |
| **Morning session I (9:00-10:30)** | Going Bayesian in applied research: When, why, and how? |
|  | Software solutions: An overview |
|  | The Bayesian workflow |
| **Morning session II (10:45-12:15)** | The brms package: Functionality |
|  | Doing Bayesian data analysis with brms: A step-by-step walkthrough |
| **Afternoon session (13:45-15:15)** | Group exercises |
|  | Solutions and discussion |

### Self-study

1.  Take-home exercise: Statistical programming in R
2.  Start your own data project with `brms`

### Week 2

| Session | Topics |
|:---|:---|
| **Day 3 (April 23) Statistical programming in R and Stan - An advanced introduction** |  |
| **Morning session I (9:00-10:30)** | Programming in R: Review |
|  | Generalized linear models |
| **Morning session II (10:45-12:15)** | Stan: Programming language and documentation |
|  | Programming and modeling in Stan: implementation, inference, and workflow |
| **Afternoon session (13:45-15:15)** | Group exercises |
|  | Solutions and discussion |
| **Day 4 (April 24) Applied Bayesian modeling in Stan** |  |
| **Morning session I (9:00-10:30)** | Programming and modeling in Stan: extensions |
|  | Efficiency tuning |
|  | Post-processing posterior draws |
| **Morning session II (10:45-12:15)** | Choosing between pre-implemented and custom solutions |
| **Afternoon session (13:45-15:15)** | Individual consultations |

## Using the workshop materials

### Interactive workshop materials

The workshop materials come as
[`learnr`](https://rstudio.github.io/learnr/) tutorials wrapped in an R
package. To download, install, and use the interactive materials, run
the following code:

``` r
# Package installation ----
## Detach if loaded ----
if ("bayesianmodeling" %in% (.packages())) {
  detach(package:bayesianmodeling, unload = TRUE)
}

## Uninstall if installed ----
if ("bayesianmodeling" %in% installed.packages()) {
  remove.packages("bayesianmodeling")
}

## Install if not installed ----
if (!("devtools" %in% installed.packages())) {
  install.packages("devtools")
}

## Load from GitHub ----
library(devtools)
devtools::install_github("denis-cohen/bayesianmodeling")

## Load to library ----
library(bayesianmodeling)

# Run the tutorials (one at a time) ----
## Introduction ----
learnr::run_tutorial("00-00-int", package = "bayesianmodeling")

## Day 1 ----
learnr::run_tutorial("01-01-lec", package = "bayesianmodeling")
learnr::run_tutorial("01-02-lec", package = "bayesianmodeling")
learnr::run_tutorial("01-03-lab", package = "bayesianmodeling")

## Day 2 ----
learnr::run_tutorial("02-01-lec", package = "bayesianmodeling")
learnr::run_tutorial("02-02-lec", package = "bayesianmodeling")
learnr::run_tutorial("02-03-lab", package = "bayesianmodeling")

## Take home exercise ----
learnr::run_tutorial("03-00-the", package = "bayesianmodeling")

## Day 3 ----
learnr::run_tutorial("03-01-lec", package = "bayesianmodeling")
learnr::run_tutorial("03-02-lec", package = "bayesianmodeling")
learnr::run_tutorial("03-03-lab", package = "bayesianmodeling")

## Day 4 ----
learnr::run_tutorial("04-01-lec", package = "bayesianmodeling")
learnr::run_tutorial("04-02-lec", package = "bayesianmodeling")
```

### Static workshop materials

- You can find HTML scripts of the **lecture slides** in the folder
  `lecture-materials`.
- Likewise, you can find HTML scripts of the **lab exercises** in the
  folder `lab-materials`. These contains both exercises and solutions.
  If you prefer working on the exercises outside of the interactive
  `learnr` environment (i.e., in a regular R session), you can use the
  `Rmd` files supplied in the same folder.

## About the Instructor

Denis Cohen is a Senior Research Fellow in the Data and Methods Unit at
the [Mannheim Centre for European Social Research
(MZES)](https://www.mzes.uni-mannheim.de/), [University of
Mannheim](https://www.uni-mannheim.de/). He is also lead organizer of
the [MZES Social Science Data
Lab](https://www.mzes.uni-mannheim.de/socialsciencedatalab/page/events/)
and lead editor of the blog [Methods
Bites](https://www.mzes.uni-mannheim.de/socialsciencedatalab/).
