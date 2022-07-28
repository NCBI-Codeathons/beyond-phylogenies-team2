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


### Figure generation

Using Python libraries [Geopandas](https://geopandas.org/en/stable/) and and [Matplotlb](https://matplotlib.org/) we created [iPython Notebooks](https://github.com/NCBI-Codeathons/beyond-phylogenies-team2/tree/main/notebooks) with dynamic visualizations incorporating genomic data with sample metadata, income demographics, and geographic overlays.


## Results



## Future Work
