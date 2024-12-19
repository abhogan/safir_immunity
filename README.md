# **safirimmunity**

<!-- badges: start -->
[![R build
status](https://github.com/mrc-ide/safir/workflows/R-CMD-check/badge.svg)](https://github.com/mrc-ide/safir/actions)
[![CodeFactor](https://www.codefactor.io/repository/github/mrc-ide/safir/badge)](https://www.codefactor.io/repository/github/mrc-ide/safir)
[![codecov.io](https://codecov.io/github/mrc-ide/safir/coverage.svg?branch=main)](https://codecov.io/github/mrc-ide/safir?branch=main)
<!-- badges: end -->

This package is a fork from the original **safir**: **s**quire **a**nd **f**riends **i**ndividual **r**ewrite
(and maintains the squire naming
[theme](https://en.wikipedia.org/wiki/Knights_of_the_Round_Table#Safir)).
It uses the [`{individual}`](https://github.com/mrc-ide/individual)
package to specify and run the simulation.

From the original package:  
**safir** can run individual based stochastic versions of the **squire** and
**nimue** models, which recover trajectories from those aggregated population
models (see package vignettes). It also implements a model for vaccination
with an arbitrary number of doses and antibody titre dynamics which affect
protective efficacy as well as efficacy against severe disease outcomes.

Because **safir** implements multiple models as individual based simulations,
there is a large amount of code, but the central disease progression is shared
across the models within **safir**. Each vignette describes how the simulation
functions and where the relevant code can be found.

## How this package is different to safir
At the core of safir is an  immunological model that simulates individual-level SARS-CoV-2 immunity over time. In the model, immunity can be boosted by either vaccination or infection and is assumed to decay over time. A logistic function that captures the relationship between immunity, and protection from both infection and severe disease. These immunity processes are simulated at the population level by implementing the individual immunological protection model within an individual-based framework of SARS-CoV-2 transmission and disease.  

In this package, we modify the underlying individual-level immunity model in the following ways.
- For each individual or agent in the model, the infection- and vaccine-induced immunity are tracked independently, and decay independently, by default.
- At each infection- or vaccine-induced boost to immunity, the level of immunity returns to the maximum level for that type of boost. (In safir, an additive process is implemented).
- At each timepoint, the total level of immunity is the maximum of the two types (instead of the sum of the two types, as in safir). 

The population-level transmission model is identical to that in safir.

## Installation of the original package

``` r
install_github('mrc-ide/safir')
library(safir)
```

## Installation of safirimmunity  

```r
install_github('abhogan/safirimmunity')
library(safirimmunity)
```

Note that because these two packages have identical function names, you will need to only have one of these packages loaded at a time.  

## Documentation

[`{safir}`](https://github.com/mrc-ide/safir) is documented on a
[dedicated website](https://mrc-ide.github.io/safir).

This includes the following vignettes:

-   **`Squire Validation Run`**: comparison of
    [`{safir}`](https://github.com/mrc-ide/safir) to
    [`{squire}`](https://github.com/mrc-ide/squire).
-   **`Nimue Validation Run`**: comparison of
    [`{safir}`](https://github.com/mrc-ide/safir) to
    [`{nimue}`](https://github.com/mrc-ide/nimue).
-   **`Vaccine model with multiple doses`**: runs the model for
    explicit tracking of antibody titre for a 2 dose vaccine.
-   **`Natural Immunity`**: demonstrates how to modify the vaccine model
    to also include mechanistic incorporation of natural immunity
    from infection, as opposed to a generic R (recovered) class.
-   **`Modeling of antibody titre and immunity`**: describes how antibody
    titre and protection against infection and severe disease is modeled.
-   **`Differential modeling of infection and vaccine derived NATs`**: is a short
    description of how to model differential boost/decay of vaccine and infection
    derived neutralizing antibody titres.
    
## License

MIT © Imperial College of Science, Technology and Medicine
