<!-- README.md is generated from README.Rmd. Please edit that file -->

promedr
=======

<!-- badges: start -->

[![Travis build
status](https://travis-ci.org/sangeetabhatia03/promedr.svg?branch=master)](https://travis-ci.org/sangeetabhatia03/promedr)
[![Codecov test
coverage](https://codecov.io/gh/sangeetabhatia03/promedr/branch/master/graph/badge.svg)](https://codecov.io/gh/sangeetabhatia03/promedr?branch=master)
<!-- badges: end -->

The goal of promedr is to pre-process data from ProMED and HealthMap and
produce a clean incidence time series that can be used in analysis
downstream.

ProMED/HealthMap data are made available as a CSV with the following
columns:

-   Location
-   Country
-   Region/City
-   Disease
-   Species
-   Feed Language
-   HM Alert ID
-   Headline
-   URL
-   Issue Date
-   Alert Tag
-   New SC
-   New SD
-   New CC
-   New CS
-   Cumulative SC
-   Cumulative SD
-   Cumulative CC
-   RO
-   Feed Name
-   Report Source - Primary
-   Secondary Report Source

Processing this data consists of the following steps:

-   Extract the total cumulative case count as a sum of desired case
    categories (Confirmed, Suspected, or both)
-   If there are any duplicate alerts for a given day, merge them
    according to pre-specified set of rules.
-   Any inconsistent data points at the end of the time series i.e.,
    those that make the cumulative case count non-increasing, are moved
    using Chebyshev’s inequality.
-   Any points in the middle of the time series that cause the
    cumulative case count to be decreasing, are removed using
    pre-specified rules.
-   Finally, missing data are imputed.

Installation
------------

You can install the development version from
[GitHub](https://github.com/) with:

    # install.packages("devtools")
    devtools::install_github("sangeetabhatia03/promedr")
