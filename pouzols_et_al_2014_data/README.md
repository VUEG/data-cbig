## DATA SET

Name: cbig_gpan_r15  
Version: 1.0.0  
Date-created: 2016-09-28
Date-modified: 2016-09-28
Metadata authors:  
+ Joona Lehtomäki <joona.lehtomaki@helsinki.fi>
+ Tuuli Toivonen <tuuli.toivonen@helsinki.fi>

## DATA DESCRIPTION

This data collectio contains the following datasets:

1. cbig_gpan_global2000_r15  
2. cbig_gpan_national2000_r15  
3. cbig_gpan_global2040_r15  
4. cbig_gpan_national2040_r15  

Each of the datasets includes the following files:

### 1. Performance curves data

`data/*/*.curves.txt`, contains the performance curves data
of the analysis. This is the standard curves file output produced by Zonation,
for further details see Zonation manual [1]. The TSV file has the following
columns:

    1. proportion of landscape lost
    2. the cost of the remaining landscape. If land costs are not included in
       the analysis, this column represents the number of cells remaining in the
       landscape.
    3. the lowest biodiversity feature distribution proportion remaining in the
       landscape (i.e., the situation of the worst-off features).
    4. the average proportion remaining over all features.
    5. the weighted average proportion of all features.
    6. the average extinction risk of biodiversity features as landscape is
       iteratively removed (as calculated from the species-area relation using
       parameter z).
    7. the weighted extinction risk where species-area extinction risk has been
       weighted by the feature weights.
    8...N the proportion of distribution remaining for each feature
       {1, 2, ..., N} in the same order as the features are listed in the
       beginning of the file.

### 2. Feature info

`data/*/*.features_info.txt` is a text file containing a
list of the biodiversity features and the relative weights (Weight) used in the
analysis. This file also shows the initial sum of feature distributions
(distribution_sum)and the level of cell removal at which point targets for
particular feature have been violated. The initial sum of distribution is simply
the sum of each feature's local occurrence levels throughout the landscape. For
example, if the biodiversity feature data is in probabilities of occurrence,
this is the sum of probabilities in all cells before any landscape has been
removed.

### 3. Grouped performance curves data

`data/*/*.txt` contains representation curves
for minimum, mean, weighted mean, and maximum representation as well as weighted
extinction risk during the course of cell removal for each group. The second
column of this file specifies the solution cost (duplicated from the global
.curves.txt file). In the per group weighted extinction risk columns, the
species-area extinction risks are weighted using the weights of the features
belonging to each particular group, similar to the ext2 column of the global
.curves.txt file.

### 4. Image file

`data/*/*.png` is an image of the map of the area illustrating
the Zonation results, ranked by using different colors to indicate the
biological value of the site. Here the best areas are displayed in red, the
worst areas in black, and the "no data" areas in white.

### 5. Rank priority map data

`data/*/*.rank.compressed.tif` is the resulting priority
raster map in GeoTIFF format. The pixel values range between 0 and 1
representing the priority of the pixel in the priority ranking produced by
Zonation, higher values indicating higher priority. Values equal and above 0.83
represent the best 17 % of the terrestrial land for protection, including the
current protected areas. For uncertainty of these values, see the sections 3.4
and 3.7 in the Supplementary material of the article [2].

Technical details of the raster data:

    Resolution: 0.017 degrees, equalling approximately 1.7 km at the Equator
    Columns & rows: 21600, 10800
    Number of bands: 1
    Pixel type: floating point, 32 bit
    Range: 0 to 1
    Nodata value: -1
    Coordinate Reference System: WGS84 (EPSG:4326)

### 6. Run info file

`data/*/*.run_info.txt` is a log file. The content of the
.run_info.txt file is identical to that of the .txt file.

### 7. Machine-readable metadata

`datapackage.json` contains data set metadata in machine-readable JSON file.
This file follows Open Knowledge Foundation's data package specification [3].  


## PROVENANCE INFORMATION

resource: pouzols_et_al_2014_data.tar.gz
retrieved_from: cbig-arnols
retrieved_date: 2016-09-28
retrieved_by: Joona Lehtomäki <joona.lehtomaki@gmail.com>
modified_date: 2016-09-284
modified_by: Joona Lehtomäki <joona.lehtomaki@gmail.com>
provenance_trail:
  1. On cbig-arnold
```
mkdir Data/pouzols_et_al_2014_data
cp -r Data/DATAPART1/Zprojects/GNoTPA-expansion/GNoTPA_output/antarctica_out_002_abf_noadmu_2000_ecor/ Data/pouzols_et_al_2014_data/
cp -r Data/DATAPART1/Zprojects/GNoTPA-expansion/GNoTPA_output/antarctica_out_102_abf_noadmu_2040_ecor/ Data/pouzols_et_al_2014_data/
cp -r Data/DATAPART1/Zprojects/GNoTPA-expansion/GNoTPA_output_admu/redist_reload_antarctica_out_0A002_abf_admu_2000_ecor/ Data/pouzols_et_al_2014_data/
rm -r Data/pouzols_et_al_2014_data/redist_reload_antarctica_out_0A002_abf_admu_2000_ecor/redist_reload_antarctica_out_0A002_abf_admu_2000_ecor.CAZ_MDE.rank.per_ADMU_outputs/
cp -r Data/DATAPART1/Zprojects/GNoTPA-expansion/GNoTPA_output_admu/redist_reload_antarctica_out_0A102_abf_admu_2040_ecor/ Data/pouzols_et_al_2014_data/
rm -r Data/pouzols_et_al_2014_data/redist_reload_antarctica_out_0A102_abf_admu_2040_ecor/redist_reload_antarctica_out_0A102_abf_admu_2040_ecor.CAZ_MDE.rank.per_ADMU_outputs/
```

## DESCRIPTION OF THE ANALYSES

The analysis identifies the priorities for expanding the current protected area
network to 17 % of the terrestrial land - and beyond. It compares the spatial
patterns and the performance of the prioritizations carried out globally and
nationally (using database of Global Administrative Areas [4]), limiting the
species ranges with present and future (2040) land use [5].

The analyses are based on the distributions of 24,757 terrestrial vertebrate
species and 826 ecoregions provided by IUCN Red List [6] and WWF Terrestrial
ecoregions [7]. The current protected area network was extracted from World
Database on Protected Areas [8] by selecting those polygons that belonged to
IUCN categories I to VI and had the status "designated". The analysis was
carried out using Zonation software [6] developed in the Conservation Biology
Informatics Group [9]. For full methodology and references, see the
supplementary material of the article [2].

## LICENCE

The data is licensed with Creative Commons Attribution 4.0 International (CC BY
4.0) lisence, see https://creativecommons.org/licenses/by/4.0/

## CITATION

The data set is an output of spatial conservation prioritization carried out for
global protected area expansion analyses published in Nature on 18th December
2014 with the title "Global protected area expansion is compromised by projected
land-use and parochialism":

http://dx.doi.org/10.1038/nature14032

You can cite to our data by citing the original paper:

  - Pouzols, Federico Montesino
  - Toivonen, Tuuli
  - Di Minin, Enrico
  - Kukkala, Aija
  - Kullberg, Peter
  - Kuustera, Johanna
  - Lehtomaki, Joona
  - Tenkanen, Henrikki
  - Verburg, Peter H.
  - Moilanen, Atte
 (2014) Global protected area expansion is compromised by projected land-use and
 parochialism. Nature, volume 516, issue 7531 pp.383-386.

## REFERENCES

[1] http://cbig.it.helsinki.fi/files/zonation/zonation_manual_v4_0.pdf  
[2] http://www.nature.com/nature/journal/vnfv/ncurrent/full/nature14032.html#supplementary-information  
[3] http://data.okfn.org/doc/data-package  
[4] http://www.gadm.org/  
[5] http://10.1111/j.1365-2486.2012.02759.x  
[6] http://www.iucnredlist.org  
[7] http://www.worldwildlife.org/publications/terrestrial-ecoregions-of-the-world  
[8] http://www.protectedplanet.net  
[9] http://cbig.it.helsinki.fi/software/zonation/  
