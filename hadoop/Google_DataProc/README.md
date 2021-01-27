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

## Upload this data to google bucket

```bash
$ gsutil cp *.csv gs://bucket_name
```

Copy the bucket back to your system
```bash
# Copy data to your current working directory
$ gsutil cp gs://bucket_name/yellow_tripdata_2020-02.csv ./
```

Copy data to hadoop system
```bash
# Copy data from the bucket to your directory
$ hdfs dfs -cp gs://bucket_name/yellow_tripdata_2020-02.csv /user/your_gmail_account_name/

# Check that you have received the data you want
$ hdfs dfs -ls /user/my_gmail_account_name
```
