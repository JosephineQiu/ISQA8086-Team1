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

We have joined csv files as per the sites through Rscript, there are 8 sites so finally we have 8 consolidated R data for each site.
There are some data which we have to clean to make a good sense of files. 

1) Remove the headers for each file as we need just 1 common header and they specify the first column of Header as "#" so we have removed the rows starting with "#".

 2) Each file has 1st row with data like "Plot " so which we don't need these rows as well, so we have removed those rows which has value like "Plot"

3) We have checked for duplicate values for Date&Time column, and if we have found duplicates then we removed extra rows and just Keep 1 row.

# R Script


# References


# Contributorship Statement
Dhwani Kumrawat, Josephine Qui, Ranga Tanishk Reddy have worked collectively to generate the documentation of this project work plan.

# Proofreader Signoff
The above contents are reviewed and confirmed by Josephine Qiu.
