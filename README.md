#Apache Hadoop 2.7.1 Docker image(forked from sequenceiq's hadoop docker image)
# Build the image

If you'd like to try directly from the Dockerfile you can build the image as:

```
sudo docker build -t hadoop/bonsai-master:2.7.1 .
```
# Build and also run the worker images made available in other repository

```
sudo docker build -t hadoop/bonsai-worker:2.7.1 .
```

# Start the master

In order to successfully start the master, make sure that you have built the workers and started them

```
sudo docker run -it -h bonsai-master --ip 172.18.0.2 --add-host bonsai-worker-1:172.18.0.5 --add-host bonsai-worker-2:172.18.0.6 --add-host bonsai-worker-3:172.18.0.7 --net bonsai-net hadoop/bonsai-master:2.7.1 /etc/bootstrap.sh -bash
```

## Testing

You can run one of the stock examples in side the master container.

```
cd /usr/local/hadoop
1.  ./bin/hadoop fs -mkdir -p /user/root
2. ./bin/hadoop fs -put /usr/local/hadoop/etc/hadoop input
3. In one of the data nodes visit the following directory
/tmp/hadoop-root/dfs/data/current/BP-1336158358-172.17.0.2-1478152360927/current/finalized/subdir0/subdir0
```

