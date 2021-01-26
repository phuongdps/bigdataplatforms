# Hadoop and Hive 

## Download the NewYork taxi dataset

To download the taxi dataset, you can use the following commands:

```bash
  # use big O for saving the file with its name.
  $ curl -O https://s3.amazonaws.com/nyc-tlc/trip+data/yellow_tripdata_2020-01.csv
```

For downloading more data, you only need to change the filename of each csv file according to the date. For example, to download 1 year data you can use the following script:

```bash
  # Use the following script to download one year data
  for x in 01 02 03 04 05 06 07 08 09 10 11 12
  do
    #wget -c https://nyctaxitrips.blob.core.windows.net/data/trip_fare_$x.csv.zip
  	curl -O https://s3.amazonaws.com/nyc-tlc/trip+data/yellow_tripdata_2020-$x.csv
  done
```