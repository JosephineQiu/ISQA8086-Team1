# Data Source Description

Linda Loring Nature Foundation being the organization running and maintaining all the species of plants to study the effects, and we as a team being the one to analyze and support further study of the organization, the data sets provided to us came from Linda Loring Nature Foundation.
They keep track of temperature of the surrounding air and the Intensity of the sunlight throughout the day across all the sites, recording temperature multiple of times a day. We have not considered the factor **Intensity** for this project and hence will be excluded in the future.

Starting from the year 2015, holds record for 4 different months or two different seasons i.e. March, May, August, and December.

2016, holds record for 4 different months i.e. April, June, May, October.

2017, holds record for 3 different i.e. April, June and October.

2018, holds record for 2 different months i.e. February and May.

Another data set includes soil temperature for the year 2017 calculated multiple times throughout the
day every day for the whole year.
Moreover, Data Set includes recording for 8 different sites named from **A** to **H** for each and every month of the year named above.
Recording of each month has four _columns, namely, Date, Time, Temperature and Intensity_.

# Intellectual Policy Constraints

The analysis which we are going to conduct will have MIT license issued. We have been permitted to use the data given by the Linda Loring Foundation to conduct the study to support their cause. For further assistance with the data and to guide through the limitations of using the data sets will be provided by **Dr.Sarah T.Bois** associated with LLNF organization.

# Meta Data Description

For the study of the different plant related events, we will be focusing more on the **Temperature**
factor and therefore we have temperature recorded using a device with thousands of entries since the
year 2016 which would be enough to comprehend the effects of the temperature mainly on the event
**breaking of bud**.
Each site is at different elevation and hence the factor of elevation will be considered to study its effect on plants. Still the team has not yet planned out as of how to use the factor of elevation into the study and hence the issue needs to be consulted with our advisors. Another data set which we received from **Nature’s Notebook** needs to be studied well and further plan will be to integrate some of the columns from that data set to the current one, like the time when the even **breaking of the event** occurred.

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

# R Script (Overview)
We used below scripts for Each sites to get the clean data

## Site A
```
temp = list.files(path = "C:/Users/Dhwani/Documents/Site F G H/SiteA_Temp",pattern="*.csv",full.names = TRUE)

temp_SiteA <- ldply(temp,read_csv,skip=1)
colnames(temp_SiteA)
names(temp_SiteA)[names(temp_SiteA) == "Date Time, GMT-04:00"] <- "DateTime"
names(temp_SiteA)[names(temp_SiteA) == "Temp, Â°C (LGR S/N: 10511284, SEN S/N: 10511284)"] <- "Temperature"
names(temp_SiteA)[names(temp_SiteA) == "Intensity, Lux (LGR S/N: 10511284, SEN S/N: 10511284)"] <- "Intensity"
names(temp_SiteA)[names(temp_SiteA) == "Temp, Â°C (LGR S/N: 10638850, SEN S/N: 10638850)"] <- "Temperature1"
names(temp_SiteA)[names(temp_SiteA) == "Intensity, Lux (LGR S/N: 10638850, SEN S/N: 10638850)"] <- "Intensity1"
names(temp_SiteA)[names(temp_SiteA) == "Date Time, GMT-05:00"] <- "DateTime1"

temp_SiteA <- temp_SiteA %>% mutate(as.factor)
temp_SiteA <- temp_SiteA %>% mutate_if(is.na,"")
temperature <- paste(temp_SiteA$Temperature,temp_SiteA$Temperature1)
DateTime <- paste(temp_SiteA$DateTime,temp_SiteA$DateTime1)
Intensity <- paste(temp_SiteA$Intensity,temp_SiteA$Intensity1)
temp_SiteA <- data.frame(DateTime,temperature,Intensity)
gsub("NA, ","",temp_SiteA)
```

## Site E

```
files_E = list.files(path = "C:/Users/Dhwani/Documents/Site F G H/Site E", pattern = "*.csv", full.names = TRUE)

datacsv_E= ldply(files_E,read.csv,header= FALSE)
datacsv_E=datacsv_E[, !(colnames(datacsv_E) %in% c("V5","V6","V7","V8"))]
datacsv_E=datacsv_E[(!duplicated(datacsv_E$V2)  & !grepl("Plot",datacsv_E$V1) & !grepl("#",datacsv_E$V1)),]
colnames(datacsv_E)
names(datacsv_E)[names(datacsv_E) == "V1"] <- "Seq"
names(datacsv_E)[names(datacsv_E) == "V2"] <- "Date&Time"
names(datacsv_E)[names(datacsv_E) == "V3"] <- "Temperature"
names(datacsv_E)[names(datacsv_E) == "V4"] <- "Intensity"
write.csv(datacsv_E, file = "MyData.csv")

```
For whole script please refer [DataCleaningLLNF.Rmd](https://github.com/JosephineQiu/ISQA8086-Team1/blob/master/DataCleaningDocumentation/DataCleaningLLNF.Rmd)

# Contributorship Statement
Dhwani Kumrawat, Josephine Qui, Ranga Tanishk Reddy have worked collectively to generate the documentation of this project of Data cleaning documentation.

# Proofreader Signoff
The above contents are reviewed and confirmed by Josephine Qiu.



