# Team 2: Data visualization design combining genomic data with epidemiological data for localized surveillance

List of participants and affiliations:
- Sidney Bell, CZI (Team Leader)
- Karthik Ramesh, Andersen Lab @ Scripps Research
- Hua Chen, Beijing Institute of Genomics
- Kristine Lacek, CDC
- Rong Jin, CDC
- Xueting Qiu, CCDD, Harvard T.H. Chan

## Project Goals

As novel pathogens like SARS-CoV-2 continually shape the landscape of genomic surveillence and patient care, clinicians, hospital administrators, and local health departments need up-to-date, targeted, and integrated data to inform public health and patient care measures. 

We aim to model a data visuaization pipeline that overlays healthcare metrics with population demographics and the antigenic landscape of a given circulating pathogen, while remaining conscious of health disparities and health equity using a two-fold approach.

### Clinical impacts

We aim to model dashboards empowering healthcare providers to answer:
- How will this pathogen or novel variant impact my facility or hospital census?
- Will I need to change my treatment paradigms?
- Is this variant antigenically novel with respect to current vaccination strategies or prior circulating variants?

### Adjusting surveillence stragegy

We aim to inform resource allocation from local health deprtments that may be asking:
- What is the necessary sampling size for variant detection?
- How can we assess case counts and sample emerging variants?
- How do cases and variant distributions vary between demographic groups?

## Approach

### Data 

Using San Diego as a model locality, we extracted epidemiological and genomic data from public repositories to build our pipeline.

Genomic data was ingested from [GISAID](https://www.gisaid.org/) and annotated with [Pangolin](https://cov-lineages.org/) Lineage calls and [NextClade](https://clades.nextstrain.org/) Clade designations.

Case counts, testing, and death data was downloaded from the [California State Public Health Department](https://data.chhs.ca.gov/dataset/covid-19-time-series-metrics-by-county-and-state/resource/046cdd2b-31e5-4d34-9ed3-b48cdbc4be7a) and filtered for San Diego County.

We created mock data modeled off of [facility testing data](https://github.com/NCBI-Codeathons/beyond-phylogenies-team2/blob/main/data/2022_facility_testing.csv) that to which institutions might have access.

From census data <source> we extracted median household income for locality zipcodes.

**Discussion Point #1** - Consolidation of genomic data:

_Problem_: Not all samples had zip-codes, there are too many to manage for all years, and some were not uploaded to GISAID.

_Action_: We consolidated the genomic data to include ~12.5k clinical samples (as opposed to environmental) which are 1) from 2022, 2) from San Diego, and 3) have both a zipcode and GISAID ID. We then got and extracted the lineage calls for these samples.

_Result_: We now have a (final version)[https://github.com/NCBI-Codeathons/beyond-phylogenies-team2/blob/main/data/2022_sd_weekly_genome_counts.csv] of the “variants over time” data for San Diego

**Discussion Point #2** - Simulated Data on Testing Volume and Positivity

_Problem_: The connection between the simulated data and genomic data is unclear

_Action_: We reiterated that there is no ID which can be used to connect lines of genomic and testing data. Instead, we confirmed that we will bin the data by week
instead, based on the dual assumptions that 1) those samples sequenced are a random subset of all positive tests and 2) county-wide statistics on new positives, hospitalizations, and deaths reflect proportionally those of any given facility. 

_Result_: We have 2 additional files and a reworked simulated dataset on individual tests just for 2022, which together give us a view of 1) true testing numbers and downstream hospitalizations / deaths in San Diego, 2) simulated individual test results at the health system level linked to generated patient categorical factors. 

### Figure generation

Using Python libraries [Geopandas](https://geopandas.org/en/stable/) and and [Matplotlb](https://matplotlib.org/) we created [iPython Notebooks](https://github.com/NCBI-Codeathons/beyond-phylogenies-team2/tree/main/notebooks) with dynamic visualizations incorporating genomic data with sample metadata, income demographics, and geographic overlays.


## Results

[TEAM 2 FINAL PRESENTATION](https://docs.google.com/presentation/d/1_dWI3wVtJVs9vGPWpTNgMXA4xjKCuZywtjtmZebjqh8/edit?usp=sharing)

## Future Work

- More actionable data would include phenotypic impacts of each variant (e.g., vaccine escape, treatment efficacy, severity, etc)
A machine-readable version of the Stanford CoV DB would be very beneficial

- Choropleth map: show changes over time

- Stacked area plot: add visual indicator of how test volume has changed over time 
