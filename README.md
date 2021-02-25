# SOI_harmonization

The data harmonization repository for the ESIP [Soil Ontology and Informatics cluster](https://wiki.esipfed.org/Soil_Ontologies_and_Informatics).

## Propsed data descriptors

The purpose of these proposed data descriptors are to provide a sufficent description of datasets that will enable a general harmonizaiton script to merge datasets into a common database.
We are assuming the data is presented as a relational database.
Take from https://github.com/ESIPFed/soil_data_model_survey/tree/master/data

1) `data_structure`: Description of the columns in a database
    - `data_product`: ID for the dataset being described. Free text, should be a unique ID
    - `data_table`: ID for the data table being described. Free text, should be a unique ID.
    - `data_column`: Column name. Free text, should be a unique ID.
    - `data_type`: Type of the data in that column. Control vocabulary. Suggested vales:
      + `value_number`: a numerical value
      + `value_factor`: a control vocabulary value
      + `value_string`: a character value or free text
      + `unit`: a unit, generally associated with a value column
      + `method`: a method description, generally associated with a value column
      + `id`: a unique identifier
      + `note`: a note, generally associated with a value column
      + `sigma`: standard deviation/sigma uncertainty

data_product|data_table|data_column|data_type
------------|----------|-----------|---------
ISCN3|layer|13c (‰)|value_number
ISCN3|layer|14c (‰)|value_number
ISCN3|layer|14c_sigma (‰)|sigma
ISCN3|layer|14c_age (BP)|value_number
ISCN3|layer|14c_age_sigma (BP)|sigma

2) `data_meta`: Descriptions of the metadata that applies to the entire table
    - `data_product`: ID for the dataset being described. Free text, should be a unique ID
    - `data_table`: ID for the data table being described. Free text, should be a unique ID. Could be NA, suggesting meta applies to entire product
    - `data_column`: Column name. Free text, should be a unique ID. Could be NA, suggesting meta applies to entire table
    - `data_type`: Type of the data in that column. Control vocabulary. Suggested vales:
      - `value_number`: a numerical value
      - `value_factor`: a control vocabulary value
      - `value_string`: a character value or free text
      - `unit`: a unit, generally associated with a value column
      - `method`: a method description, generally associated with a value column
      - `id`: a unique identifier
      - `note`: a note, generally associated with a value column
      - `sigma`: standard deviation/sigma uncertainty
    - `entry`: assigned value to that property for the product/table/column of interest
    
data_product|data_table|data_column|data_type|entry
------------|-----------|----------|----------|-----
ISCN3|layer|13c (‰)|unit|permille
ISCN3|layer|14c (‰)|unit|permille
ISCN3|layer|14c_sigma (‰)|unit|permille
ISCN3|layer|14c_age (BP)|method|14C age model
ISCN3|layer|14c_age (BP)|unit|BP

3) `thesaurus`: Description mapping provided variable to a common vocabulary
    - `variable_location`: Where is the variable described in the dataset? Either a column_name or variable_name to cover wide and long tables
    - `data_product`: ID for the dataset being described. Free text, should be a unique ID
    - `data_table`: ID for the data table being described. Free text, should be a unique ID. Could be NA, suggesting meta applies to entire product
    - `provided_variable`: variable name from the original dataset, often column header matching `data_column` in `data_meta`
    - `variable`: common vocabulary that is being mapped to this should reference some external URI

variable_location|data_product|data_table|provided_variable|variable
----------------|------------|------------|-----------------|--------
column_name|ISCN3|layer|13c (‰)|13c
column_name|ISCN3|layer|14c (‰)|14c
column_name|ISCN3|layer|14c_sigma (‰)|14c


## Ways to contribute:

1) Identify soil data products for evaluation via https://github.com/ESIPFed/SOI_harmonization/issues/2
2) Describe how layer location (geolocation, depth, and sampling time) are described in the data product https://github.com/ESIPFed/SOI_harmonization/issues/1
