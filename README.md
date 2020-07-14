# RCardiacHTS

Analysis tools for high-throughput screening of cardiomyocyte biology.

Some of the scripts are specific to the Vala Sciences KIC platform, others are applicable to other platforms. Functions which are KIC specific have the 'kic' prefix.

## Installation

```
# install using devtools and github
devtools::install_github("abruyneel/RCardiacHTS")
```

## Use

### Vala KIC data processing


```
# read the KIC data's file structure
files <- RCardiacHTS.kic.readfolders()

# define the analysis parameters
config <- RCardiacHTS.kic.readconfig(rows = NA, names = c(2), 
                            colnames_pi = c("Pi.on.Wm.API.FWHM.Time_Mean",                                                  
                                            "Pi.on.Wm.API.CTD75.Time_Mean", 
                                            "Pi.on.Wm.API.CTD90.Time_Mean"), 
                            colnames_primary = c("Pi.on.Wm.API.Beats.per.Minute_Mean"))

# define the grouping and plate map linking function
ident <- function(x) {return(x)}
groups <- RCardiacHTS.kic.readgroups(grouptable = NA, groupfunction = ident, 
                            groupcolin = 2, groupcolout = 2, groupcolinmap = 1)

# extract the data
dataextract <- RCardiacHTS.kic.extract(files, config, groups)
```

### Data normalization and correction


### Plotting

## References

McKeithan WL, Savchenko A, Yu MS, Cerignoli F, Bruyneel AAN, Price JH, et al. An Automated Platform for Assessment of Congenital and Drug-Induced Arrhythmia with hiPSC-Derived Cardiomyocytes. Front Physiol. 8, 766, 2017. https://www.frontiersin.org/articles/10.3389/fphys.2017.00766/full
