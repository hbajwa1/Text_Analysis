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

The OCC data contains information on occupations for all NAICS
industries across all metropolitan regions in the U.S. I want to analyze
the `OCC_TITLE` variable in the dataset and isolate Construction and
Real Estate job types only.

``` r
text_data <- read_csv("Data/occupation_titles.csv.zip", show_col_types = FALSE)
```

    ## Multiple files in zip: reading 'occupation_titles.csv'
    ## New names:

``` r
# Sample data
occupation_titles <- text_data$oes_master.OCC_TITLE

# Define regular expressions to match Construction sector occupation titles
construction_regex <- "(?i)(Architect|Building Contractor|Building Inspector|Building Maintenance Technician|Building Surveyor|Carpenter|Concrete Finisher|Construction Equipment Operator|Construction Laborer|Construction Manager|Construction Project Manager|Construction Superintendent|Crane Operator|Drywaller|Electrician|Environmental Engineer|Estimator|Fire Sprinkler Installer|Flooring Installer|General Contractor|Glazier|Heavy Equipment Operator|HVAC Technician|Interior Designer|Ironworker|Landscape Architect|Landscaper|Mason|Painter|Pipefitter|Plumber|Project Engineer|Real Estate Agent|Roofing Contractor|Roofer|Scaffolder|Sheet Metal Worker|Structural Engineer|Surveyor|Tiler|Welder)"


# Use grep function to extract occupation titles that match the Construction sector regex
construction_occupations <- unique(grep(construction_regex, occupation_titles, value = TRUE))

# View the extracted occupation titles
#construction_occupations
```
