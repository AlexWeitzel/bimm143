Class 12: Structural Bioinformatics pt.1
================
Alex Weitzel
2/13/2020

## PDB statistics

Here w inspect the types of structures in the main database for 3D
biomolecular data - the PDB.

<https://www.rcsb.org/>

<https://www.rcsb.org/stats/summary> ^^csv from here^^

> Q1: Download a CSV file from the PDB site (accessible from “Analyze”
> -\> “PDB Statistics” \> “by Experimental Method and Molecular Type”.
> Move this CSV file into your RStudio project and determine the
> percentage of structures solved by X-Ray and Electron Microscopy.

``` r
# read in file
stats <- read.csv("Data Export Summary.csv", row.names = 1)

#calculate precentage values asked for
#stats["X-Ray",]$Proteins / sum(stats$Total)
#stats["Electron Microscopy",]$Proteins / sum(stats$Total)

ans <- stats$Total / sum(stats$Total) * 100
names(ans) <- rownames(stats)
round(ans,2)
```

    ##               X-Ray                 NMR Electron Microscopy               Other 
    ##               88.95                8.04                2.72                0.19 
    ##        Multi Method 
    ##                0.10

> Q2: Also can you determine what proportion of structures are protein?
> Aim to have a rendered GitHub document with working code that yields
> your answers.

``` r
round(sum(stats$Proteins)/ sum(stats$Total) * 100, 2)
```

    ## [1] 92.69

> Q3: Type HIV in the PDB website search box on the home page and
> determine how many HIV-1 protease structures are in the current PDB?
