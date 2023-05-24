When model data is collected to blob storage, we need to roll the data to different path to avoid logging all of them in a single blob file.
If the rolling rate is hour, all data will be collected in the blob path /yyyy/MM/dd/HH/.
If it's day, all data will be collected in blob path /yyyy/MM/dd/.
The other benefit of rolling path is that model monitoring ui is able to select a time range of data very quickly.