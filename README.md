# aroma-flavor-chemicals-db
Extract data on aroma & flavor chemicals to a database.

## Purpose
This repository houses a database of food chemicals with aroma and/or flavor data. It includes Jupyter notebooks showing the extraction of that data from reference sources, as well as the data itself.

## Contents
This repository includes:
* Jupyter notebooks:
    * `1-extraction-fenaroli.ipynb`: Crude data parsing of aroma/flavor data from a PDF copy of *Fenaroli's Handbook of Flavor Ingredients*.
    * `2-extraction-common-materials.ipynb`: Crude data parsing of additional aroma/flavor data from a PDF copy of *Common Fragrance and Flavor Materials*.
    * `3-nlp-cleaning.ipynb`: A natural language approach to further cleaning the descriptions extracted in the first two notebooks. Broad categories for flavor/smell descriptors are defined, and molecules are assigned to one or more categories.
* Data files:
    * `aromas-flavors.db`: A SQLite database containing the extracted flavor and aroma data. Included tables:
        * `fenaroli`: Crudely extracted data from *Fenaroli's Handbook*. Each row represents one molecule, and the included fields are: the chemical `name`, its unique `CAS_num`, and a `full_description`.
        * `common-materials` Similar to above, except with data extracted from *Common Fragrance and Flavor Materials*.
        * `categorized-descriptors`: Cleaned & well structured sensory information. With one row per molecule, fields are: a molecule's `name`, its unique `CAS_num` identifier, a list of categories describing its `aroma`, and a list of categories describing its `flavor`.
    * Several CSV files:
        * `lexicon.csv`: A set of 29 categories/subcategories generated to describe flavors and aromas for this project.
        * `stems-to-lexicon.csv`: A translation dictionary that equates Snowball-stemmed sensory descriptors to categories defined in the lexicon. For example, "rosy" is assigned to the category "floral".
        * `aromas-flavors-categorized.csv`: Tab-separated file to avoid convolution by molecule names that also contain commas. Each entry describes one molecule by its `name`, its unique `CAS_num` identifier, and lists of categories from the lexicon describing both its `aroma` and `flavor`.
