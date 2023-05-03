Text Analysis
================

## Overview

I conduct text analysis of occupations from the [Occupational Employment
and Wage Statistics](https://www.bls.gov/oes/) database by the U.S.
Census as part of a ‘Real Estate Construction’ project that I worked on
with the [Economy League](https://economyleague.org). The goal of this
project was to conduct a landscape study of the Construction landscape
of Greater Philadelphia and identify the demand and supply for
construction projects and employment in the region in coming years.

## Primary Objective

Extract all occupations from the OEWS dataset that are related to
construction and real estate.

## Reason for Text Analysis

The U.S. Census stores a large amount of information on occupation types
across industries and sub-industries in the OEWS dataset. Although the
U.S. Census does categorize occupations by industry and occupation
codes, we had to create a new classification scheme to identify ONLY
construction related jobs in Greater Philadelphia because Mining jobs
are bundled with the Occupation jobs in the OEWS dataset. These Mining
jobs inflate the average wage calculations that we needed to make as
part of our analysis. Since manually identifying occupations from the
long list of occupations in the OEWS dataset is cumbersome and creates
chances of error and bias, I decided to use text analysis in `R` to
create this classification.

## Text Analysis

The OES data contains information on occupations for all NAICS
industries across all metropolitan regions in the U.S. I want to analyze
the `OCC_TITLE` variable in the dataset and isolate Construction and
Real Estate job types only. I use `tidytext` package for this analysis.

``` r
oes_data <- read.csv("Data/oes_data.csv")

occupation_text <- data.frame(oes_data$OCC_TITLE)

text_data_tokens <- occupation_text %>% 
  unnest_tokens(word, oes_data.OCC_TITLE)
```

I split the `occupations` variable from the OES data into text data
tokens to analyze them using `tidytext` package in R. The text tokens
look like this at this stage:

``` r
head(text_data_tokens)
```

    ##          word
    ## 1         all
    ## 2 occupations
    ## 3  management
    ## 4 occupations
    ## 5       chief
    ## 6  executives
