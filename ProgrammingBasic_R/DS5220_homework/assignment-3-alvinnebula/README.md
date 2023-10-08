# assignment-3


## Due Date

###9/15/2021 11:59pm



## Part 1: CO2 dataset check (50 pts)

Create an issue named "import_data"
Install and library the "assertr" package. 
Prepare an R notebook named "10_import" that reads in the CO2 data, and checks for violations of expectations. 

### Using assert's or verify's, test one property (or more) for each of the following variables

### Requirement: "within_n_sds" and "is_uniq" are verp helpful helper functions. Explain these functions, try to apply them to the dataset.

- Plant
an ordered factor with levels Qn1 < Qn2 < Qn3 < ... < Mc1 giving a unique identifier for each plant.

- Type
a factor with levels Quebec Mississippi giving the origin of the plant

- Treatment
a factor with levels nonchilled chilled

- conc
a numeric vector of ambient carbon dioxide concentrations (mL/L).

- uptake
a numeric vector of carbon dioxide uptake rates (umol/m^2 sec).

Be sure to preface this code chunk with a description of the properties you will be testing based on consultation with your data expert. 

i.e.: The dataset should have the columns "Plant","Type","Treatment","conc","uptake".


## Part 2: R verbs (50 pts)