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
construction_regex <- "(?i)(Architect|Building Contractor|Building Inspector|Building Maintenance Technician|Building Surveyor|Carpenter|Concrete Finisher|Construction Equipment Operator|Construction Laborer|Construction Manager|Construction Project Manager|Construction Superintendent|Crane Operator|Drywall|Electrician|Environmental Engineer|Estimator|Fire Sprinkler Installer|Floor Installer|General Contractor|Glazier|Heavy Equipment Operator|HVAC Technician|Interior Designer|Ironworker|Landscape Architect|Landscaper|Mason|Painter|Pipefitter|Plumber|Project Engineer|Real Estate Agent|Roofing Contractor|Roofer|Scaffolder|Sheet Metal Worker|Structural Engineer|Surveyor|Tiler|Welder|Boilermakers|Carpet Installers|Elevator|Fence|Floor Layers|Floor Sanders and Finishers|Hazardous Materials Removal Workers|Highway Maintenance Workers|Insulation Workers|Paving, Surfacing, and Tamping Equipment Operators|Paperhangers|Pile Driver Operators|Pipelayers|Rail-Track Laying and Maintenance Equipment Operators|Reinforcing Iron and Rebar Workers|Rock Splitters, Quarry|Septic Tank Servicers and Sewer Pipe Cleaners|Solar Photovoltaic Installers|Structural Iron and Steel Workers|Tapers|Terrazzo Workers and Finishers|Tile and Marble Setters|Tile and Stone Setters)"

# Use grep function to extract occupation titles that match the Construction sector regex
construction_occupations <- unique(grep(construction_regex, occupation_titles, value = TRUE))
```

## List of Occupation Titles in the Construction Sector

Using this text analysis, I was able to extract relevant job positions
with a **success rate of 81%**. The list of successful extracted
occupation titles are below:

| Construction Occupations                                                                             |
|:-----------------------------------------------------------------------------------------------------|
| Construction Managers                                                                                |
| Architectural and Engineering Managers                                                               |
| Cost Estimators                                                                                      |
| Computer Network Architects                                                                          |
| Architecture and Engineering Occupations                                                             |
| Architects, Except Landscape and Naval                                                               |
| Landscape Architects                                                                                 |
| Surveyors                                                                                            |
| Environmental Engineers                                                                              |
| Architectural and Civil Drafters                                                                     |
| Environmental Engineering Technicians                                                                |
| Architecture Teachers, Postsecondary                                                                 |
| Fine Artists, Including Painters, Sculptors, and Illustrators                                        |
| Interior Designers                                                                                   |
| Boilermakers                                                                                         |
| Brickmasons and Blockmasons                                                                          |
| Stonemasons                                                                                          |
| Carpenters                                                                                           |
| Carpet Installers                                                                                    |
| Floor Layers, Except Carpet, Wood, and Hard Tiles                                                    |
| Floor Sanders and Finishers                                                                          |
| Tile and Marble Setters                                                                              |
| Cement Masons and Concrete Finishers                                                                 |
| Terrazzo Workers and Finishers                                                                       |
| Construction Laborers                                                                                |
| Paving, Surfacing, and Tamping Equipment Operators                                                   |
| Operating Engineers and Other Construction Equipment Operators                                       |
| Drywall and Ceiling Tile Installers                                                                  |
| Tapers                                                                                               |
| Electricians                                                                                         |
| Glaziers                                                                                             |
| Insulation Workers, Floor, Ceiling, and Wall                                                         |
| Insulation Workers, Mechanical                                                                       |
| Painters, Construction and Maintenance                                                               |
| Paperhangers                                                                                         |
| Pipelayers                                                                                           |
| Plumbers, Pipefitters, and Steamfitters                                                              |
| Plasterers and Stucco Masons                                                                         |
| Reinforcing Iron and Rebar Workers                                                                   |
| Roofers                                                                                              |
| Sheet Metal Workers                                                                                  |
| Structural Iron and Steel Workers                                                                    |
| Solar Photovoltaic Installers                                                                        |
| Helpers–Brickmasons, Blockmasons, Stonemasons, and Tile and Marble Setters                           |
| Helpers–Carpenters                                                                                   |
| Helpers–Electricians                                                                                 |
| Helpers–Painters, Paperhangers, Plasterers, and Stucco Masons                                        |
| Helpers–Pipelayers, Plumbers, Pipefitters, and Steamfitters                                          |
| Construction and Building Inspectors                                                                 |
| Elevator Installers and Repairers                                                                    |
| Fence Erectors                                                                                       |
| Hazardous Materials Removal Workers                                                                  |
| Highway Maintenance Workers                                                                          |
| Septic Tank Servicers and Sewer Pipe Cleaners                                                        |
| Refractory Materials Repairers, Except Brickmasons                                                   |
| Coil Winders, Tapers, and Finishers                                                                  |
| Welders, Cutters, Solderers, and Brazers                                                             |
| Cabinetmakers and Bench Carpenters                                                                   |
| Painters, Transportation Equipment                                                                   |
| Helpers–Roofers                                                                                      |
| Marine Engineers and Naval Architects                                                                |
| Rail-Track Laying and Maintenance Equipment Operators                                                |
| Rock Splitters, Quarry                                                                               |
| Electrical, Electronic, and Electromechanical Assemblers, Except Coil Winders, Tapers, and Finishers |
| Database Administrators and Architects                                                               |
| Environmental Engineering Technologists and Technicians                                              |
| Tile and Stone Setters                                                                               |
| Elevator and Escalator Installers and Repairers                                                      |
| Pile Driver Operators                                                                                |
| Database Architects                                                                                  |
