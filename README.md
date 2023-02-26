# aroma-flavor-chemicals-db
Extract data on aroma & flavor chemicals to a database.

## Purpose
This repository houses a database of food chemicals with aroma and/or flavor data. It includes Jupyter notebooks showing the extraction of that data from reference sources, as well as the data itself.

## Contents
This repository includes:
* Jupyter notebooks:
    * `1-extraction-fenaroli.ipynb`: Crude data parsing of aroma/flavor data from a PDF copy of *Fenaroli's Handbook of Flavor Ingredients*.
    * `2-extraction-common-materials.ipynb`: Crude data parsing of additional aroma/flavor data from a PDF copy of *Common Fragrance and Flavor Materials*.
* Data files:
    * `aromas-flavors.db`: A SQLite database containing the extracted flavor and aroma data.
