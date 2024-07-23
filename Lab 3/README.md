## Lab 3: Snowpipe

**Description**: This is the SQL script that initializes the AWS connection, create the csv file format and uses copy into to take any csv files into a newly created snowflake transient table

---
### SQL Script
``` sql
CREATE OR REPLACE STAGE TECHCATALYST_DE.EXTERNAL_STAGE.ARYAN_WK6_LAB3_AWS_STAGE
        --STORAGE_INTEGRATION = s3_int
        URL='s3://aryan-techcatalyst-lab/'
        -- YOU HAVE TO PUT CREDENTIALS WITH KEY AND SECRET

CREATE OR REPLACE FILE FORMAT csv_format
TYPE = 'CSV'
FIELD_OPTIONALLY_ENCLOSED_BY = '"'
SKIP_HEADER = 1;

create or replace transient table techcatalyst_de.azodge.test
(
name string,
favnumber number
);

create or replace pipe techcatalyst_de.external_stage.aryan_pipe
auto_ingest = True

as 
copy into techcatalyst_de.azodge.test
from  @TECHCATALYST_DE.EXTERNAL_STAGE.ARYAN_WK6_LAB3_AWS_STAGE
FILE_FORMAT = 'csv_format';

alter pipe techcatalyst_de.external_stage.aryan_pipe refresh;

show pipes;

SELECT *
FROM techcatalyst_de.azodge.test
limit 10;
```