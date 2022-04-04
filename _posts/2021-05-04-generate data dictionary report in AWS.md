## Automatically generate data dictionary report in AWS

Occasionally users will ask what data is stored in your datalake. You can manually keep a spreadsheet containing all the meta data. I decided to write a script using python and boto3 to generate the report. The script generates two files. One describes the database level and the other describes the data at the table level. 


<https://gist.github.com/udelblue/7505932e90adfb74d0652f2a1d363936>

