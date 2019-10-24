# Data Source Description
(1-2 paragraph text description of the data source/s (how much, where from, what it contains, etc.) with a properly formatted citation for each data source. This should include how many rows & columns (&/or tables) and sample column headers. Each data source you're using should have a similar description)

# Intellectual Policy Constraints
Specifically identify any intellectual policy constraints, or lack thereof (licensing).

# Meta Data Description
1 paragraph description of the metadata: what is available to help you interpret and understand the data?

# Issues of the Dataset(s)
We have identified the following issues of the datasets:
* Missing Values - The datasets have some missing values that need further investigation.
* Columns that are unable to match - In order to analyze on the influence of temperature on the phenomenon of breaking leaf buds, we identify the necessity to join the tables. However, while we were working on the datasets, we found out that the intensity table and the temperature tables don't have shared primary keys, which caused the failure to match the phenophase column and the temperature column.
* Lack of site names on the datasets - The tables are organized according to datetimes but on each dataset, there is no such column that marks the site name where the temperature observations are gathered from.
* Unmatched columns in the datasets - The datasets generated before 5/2015 don't have any intensity columns, which causes the joined data table to lose the intensity observations. After evaluation we've decided to remove the data tables generated before 5/2015 or without the intesnsity observations. 
* Lack of common column names - The column names that are used to record the temperature observations are not uniform, and thus columns with diffrent headers can't be directly joined, which leads to a lot of extra work when we are combining the data tables.

# Rationale of Dataset Handling
1 paragraph description of your rationale for the steps you're taking to remediate data. For example, if you need to fill in empty fields, specify what value you chose and why.

# R Script


# References


# Contributorship Statement
Dhwani Kumrawat, Josephine Qui, Ranga Tanishk Reddy have worked collectively to generate the documentation of this project work plan.

# Proofreader Signoff
The above contents are reviewed and confirmed by Josephine Qiu.
