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

- Dataset with occupation titles: `occupation_titles.csv.zip`
- Variable with occupation titles: `oes_master.OCC_TITLE`

I used ChatGPT to create an exhaustive list of occupation titles
associated with the Construction sector. Then, I use `regex` function in
R to match construction sector titles from the `occupation_titles`
dataset.

``` r
# Define regular expressions to match Construction sector occupation titles
construction_regex <- "(?i)(Architect|Building Contractor|Building Inspector|Building Maintenance Technician|Building Surveyor|Carpenter|Concrete Finisher|Construction Equipment Operator|Construction Laborer|Construction Manager|Construction Project Manager|Construction Superintendent|Crane Operator|Drywaller|Electrician|Environmental Engineer|Estimator|Fire Sprinkler Installer|Flooring Installer|General Contractor|Glazier|Heavy Equipment Operator|HVAC Technician|Interior Designer|Ironworker|Landscape Architect|Landscaper|Mason|Painter|Pipefitter|Plumber|Project Engineer|Real Estate Agent|Roofing Contractor|Roofer|Scaffolder|Sheet Metal Worker|Structural Engineer|Surveyor|Tiler|Welder)"

# Use grep function to extract occupation titles that match the Construction sector regex
construction_occupations <- unique(grep(construction_regex, occupation_titles, value = TRUE))
```

## List of Occupation Titles in the Construction Sector

| Construction Occupations                                                   |
|:---------------------------------------------------------------------------|
| Construction Managers                                                      |
| Architectural and Engineering Managers                                     |
| Cost Estimators                                                            |
| Computer Network Architects                                                |
| Architecture and Engineering Occupations                                   |
| Architects, Except Landscape and Naval                                     |
| Landscape Architects                                                       |
| Surveyors                                                                  |
| Environmental Engineers                                                    |
| Architectural and Civil Drafters                                           |
| Environmental Engineering Technicians                                      |
| Architecture Teachers, Postsecondary                                       |
| Fine Artists, Including Painters, Sculptors, and Illustrators              |
| Interior Designers                                                         |
| Brickmasons and Blockmasons                                                |
| Stonemasons                                                                |
| Carpenters                                                                 |
| Cement Masons and Concrete Finishers                                       |
| Construction Laborers                                                      |
| Operating Engineers and Other Construction Equipment Operators             |
| Electricians                                                               |
| Glaziers                                                                   |
| Painters, Construction and Maintenance                                     |
| Plumbers, Pipefitters, and Steamfitters                                    |
| Plasterers and Stucco Masons                                               |
| Roofers                                                                    |
| Sheet Metal Workers                                                        |
| Helpers–Brickmasons, Blockmasons, Stonemasons, and Tile and Marble Setters |
| Helpers–Carpenters                                                         |
| Helpers–Electricians                                                       |
| Helpers–Painters, Paperhangers, Plasterers, and Stucco Masons              |
| Helpers–Pipelayers, Plumbers, Pipefitters, and Steamfitters                |
| Construction and Building Inspectors                                       |
| Refractory Materials Repairers, Except Brickmasons                         |
| Welders, Cutters, Solderers, and Brazers                                   |
| Cabinetmakers and Bench Carpenters                                         |
| Painters, Transportation Equipment                                         |
| Helpers–Roofers                                                            |
| Marine Engineers and Naval Architects                                      |
| Database Administrators and Architects                                     |
| Environmental Engineering Technologists and Technicians                    |
| Database Architects                                                        |
