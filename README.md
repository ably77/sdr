# Task 1

Use Case: As applications scale up, data services also need to be scaled up to meet the demand

Challenges: Developing automation to scale for many data services can be a challenge for some Operations teams. Traditional method is to overprovision stateful services, but this is a waste of resource utilization

Solution: DC/OS provides and supports automation for Scaling data service frameworks out-of-the-box for all of our Certified Data Services Frameworks through both UI and CLI. Scaling up is non-disruptive so it solves both Challenge 1 (Cluster management) and Challenge 2 (Service Lifecycle Management) management goals for Operations teams.

In the DC/OS UI, navigate to the Services --> prod --> dataservices --> Cassandra service and select Edit

![](https://github.com/ably77/sdr/blob/master/resources/cassandra1.png)

Navigate to the Nodes tab and change the count from the default 3 --> 4 nodes:

![](https://github.com/ably77/sdr/blob/master/resources/cassandra2.png)

Select Review and Run --> Run Service to initiate scaling of the Cassandra service:

![](https://github.com/ably77/sdr/blob/master/resources/cassandra3.png)

Using the DC/OS Cassandra CLI you can also check the status of your Cassandra service
```
dcos cassandra plan status deploy --name=/prod/dataservices/cassandra
```

Output should look like below:
```
$ dcos cassandra plan status deploy --name=/prod/dataservices/cassandra
deploy (<UNKNOWN> strategy) (IN_PROGRESS)
└─ node-deploy (<UNKNOWN> strategy) (IN_PROGRESS)
   ├─ node-0:[server] (COMPLETE)
   ├─ node-1:[server] (COMPLETE)
   ├─ node-2:[server] (COMPLETE)
   └─ node-3:[server] (STARTING)

$ dcos cassandra plan status deploy --name=/prod/dataservices/cassandra
deploy (<UNKNOWN> strategy) (COMPLETE)
└─ node-deploy (<UNKNOWN> strategy) (COMPLETE)
   ├─ node-0:[server] (COMPLETE)
   ├─ node-1:[server] (COMPLETE)
   ├─ node-2:[server] (COMPLETE)
   └─ node-3:[server] (COMPLETE)
```

# Task 2

# Task 3

# Task 4

# Task 5

# Task 6

# Task 7

# Task 8
