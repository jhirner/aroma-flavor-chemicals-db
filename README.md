# aroma-flavor-chemicals-db
Extract data on aroma & flavor chemicals to a database.

## Purpose
This repository houses a database of food chemicals with aroma and/or flavor data. It includes Jupyter notebooks showing the extraction of that data from reference sources, as well as the data itself.

## Contents
This repository includes:
* Jupyter notebooks in the root directory:
    * `1-extraction-fenaroli.ipynb`: Crude data parsing of aroma/flavor data from a PDF copy of *Fenaroli's Handbook of Flavor Ingredients*.
    * `2-extraction-common-materials.ipynb`: Crude data parsing of additional aroma/flavor data from a PDF copy of *Common Fragrance and Flavor Materials*.
    * `3-nlp-cleaning.ipynb`: A natural language approach to further cleaning the descriptions extracted in the first two notebooks. Broad categories for flavor/smell descriptors are defined, and molecules are assigned to one or more categories.
    * `4-data-validation.ipynb`: Validation of chemical names from notebook 3 and lookup of chemical structures. Both steps use the PubChem database.
* Data files in the `processed-data` directory:
    * `aromas-flavors.db`: A SQLite database containing the extracted flavor and aroma data. Included tables:
        * `fenaroli`: Crudely extracted data from *Fenaroli's Handbook*. Each row represents one molecule, and the included fields are: the chemical `name`, its unique `CAS_num`, and a `full_description`. This data table is used only for storage of partially processed data and is not intended as a primary source of readily usable information.
        * `common-materials` Similar to above, except with data extracted from *Common Fragrance and Flavor Materials*. Also as above, this table is not intended as a primary source of readily usable information.
        * `categorized-descriptors`: Cleaned & well structured sensory information. With one row per molecule, fields are: a molecule's `common_name`, a list of categories describing its `aroma`, and a list of categories describing its `flavor`. (Categories are defined in `lexicon.csv`, below).
        * `structures`: Chemical structures for all the molecules present in the `categorized-descriptors` table. With one row per molecule, fields are: the molecule's `common_name` and its chemical structure as both a `SMILES_code` and an `InChI_code`.
    * Several CSV files:
        * `lexicon.csv`: A set of 29 categories/subcategories generated to describe flavors and aromas for this project.
        * `stems-to-lexicon.csv`: A translation dictionary that equates Snowball-stemmed sensory descriptors to categories defined in the lexicon. For example, "rosy" is assigned to the category "floral".
        * `aromas-flavors-categorized.csv`: Tab-separated file to avoid convolution by molecule names that also contain commas. Each entry describes one molecule by its `name`, its unique `CAS_num` identifier, and lists of categories from the lexicon describing both its `aroma` and `flavor`.
