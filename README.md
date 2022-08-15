# Separating-or-breaking-apart-columns-with-separate-function-in-R-programming-
# Breaking apart columns in R programming 
library(tidyverse)

### US government Center for Medicare and Medicaid services

### Reading the data 

### Using your own names for the columns 
names <- c('DRG', 'ProviderID', 'Name','Address', 'City', 'State', 'ZipCode',
           'Region', 'Discharges', 'AverageCharges', 'AverageTotalPayments', 
           'AverageMedicarePayments')

inpatient <- read_tsv('http://594442.youcanlearnit.net/inpatient.tsv', 
                      col_names = names, skip = 1)
glimpse(inpatient)

### Looking at the unique values of the DRG 
unique(inpatient$DRG)

### Separating DRG by -
separate(data = inpatient, col = DRG, into = c("DRGCode", "DRGDescription"), sep = '-')

### You realise some of the values did not go through so let take a look at this values
inpatient$DRG[45895]
### You realise drug eluting has dash in them and this is the reason 

### Another way is to break or separate these columns by the forth item
inpatient <- separate(data = inpatient, col = DRG, into = c("DRGCode", "DRGDescription"), sep = 4)
glimpse(inpatient)


