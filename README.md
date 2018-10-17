# Task 1 - Data Services Team

## Scale up Cassandra

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

# Task 2 - Data Services Team

## Scale up Kafka

Use Case: As applications scale up, data services also need to be scaled up to meet the demand

Challenges: Developing automation to scale for many data services can be a challenge for some Operations teams. Traditional method is to overprovision stat$

Solution: DC/OS provides and supports automation for Scaling data service frameworks out-of-the-box for all of our Certified Data Services Frameworks throu$

In the DC/OS UI, navigate to the Services --> prod --> dataservices --> Kafka service and select Edit

![](https://github.com/ably77/sdr/blob/master/resources/kafka2.png)

Select Review and Run --> Run Service to initiate scaling of the Kafka service:

![](https://github.com/ably77/sdr/blob/master/resources/kafka3.png)

Validate in the UI that a 4th Kafka broker service is healthy and running

# Task 3 - Data Services Team

## Deploy a Second Kafka Cluster

Use Case: Development teams may want their own dedicated data service cluster for their own team. Reasons why include data isolation, control, flexibility with updates, easier lifecycle management

Challenges: As many development teams enter the platform, each demanding their own dedicated service cluster for each team, IT Operations gets burdened with managing to "keep-the-lights-on" for their internal customers rather than innovating themselves

Solution: DC/OS provides full lifecycle management for data services and provides tooling that makes scenarios such as scaling easy to do

In the DC/OS UI, navigate to the Catalog and search for Kafka:

![](https://github.com/ably77/sdr/blob/master/resources/kafka4.png)

Change the name to kafka-MLteam and click Review and Run:

![](https://github.com/ably77/sdr/blob/master/resources/kafka4.png)

Note that your deployment will ERROR because you do not have the correct RBAC permissions to deploy into the main folder:

![](https://github.com/ably77/sdr/blob/master/resources/kafka5.png)

Press back and add `/prod/dataservices/` in front of `kafka-mlteam` and try to Review and Run again:

![](https://github.com/ably77/sdr/blob/master/resources/kafka6.png)

This should be successful because you are part of a team that has access to the `/prod/dataservices/` folder!

# Task 4 - Microservices Team

## Scale the Message Listener

Use Case: As more devices are connecting to the application, the message listener needs to be scaled up to meet the demand

Navigate to the prod --> microservices --> connectedcar --> message-handler folder

![](https://github.com/ably77/sdr/blob/master/resources/microservices1.png)

Select the message-listener service and click edit at the top right

![](https://github.com/ably77/sdr/blob/master/resources/microservices2.png)

Scale up the message-listener service by increasing the instances from 1 --> 3. Click Review and Run

![](https://github.com/ably77/sdr/blob/master/resources/microservices3.png)

Check in the UI to see that the message-listener service has now scaled up

![](https://github.com/ably77/sdr/blob/master/resources/microservices4.png)

Congrats! Your app is now ready to take on more incoming traffic!

# Task 5 - Microservices Team

## Scale up the CPU and MEM of the UI service

Use Case: As more traffic goes to our UI, we will probably need more than 0.1 CPU and 512MB of RAM so our website isn't super slow

Navigate to the prod --> microservices --> connectedcar --> ui folder

![](https://github.com/ably77/sdr/blob/master/resources/ui1.png)

Select the ui service and click edit at the top right

![](https://github.com/ably77/sdr/blob/master/resources/ui2.png)

Scale up the UI service to use 1 CPU and 2000 MB of MEM and select Review and Run

![](https://github.com/ably77/sdr/blob/master/resources/ui3.png)

Check the DC/OS UI to see that a new UI service is deployed and then the old one is killed afterwards

![](https://github.com/ably77/sdr/blob/master/resources/ui4.png)

# Task 6 - superuser

## Give team permissions

Use case: Since many people are using this cluster, we want to be able to control access to who has what security permissions

In the sidebar navigate to Organizations --> Users and select add new user + at the top right

![](https://github.com/ably77/sdr/blob/master/resources/rbac1.png)

Create the new-hire Gurjeet with the information below:
- Fullname: gurjeet nijjar
- Name: gurjeet
- Password: mesosphere

![](https://github.com/ably77/sdr/blob/master/resources/rbac2.png)

Go to the Organizations --> Groups page and select the Superusers group

![](https://github.com/ably77/sdr/blob/master/resources/rbac3.png)

In the Groups page, select users and add gurjeet to the superusers group:

![](https://github.com/ably77/sdr/blob/master/resources/rbac4.png)

Verify that Gurjeet has full superuser permissions by clicking on his name in the group

![](https://github.com/ably77/sdr/blob/master/resources/rbac5.png)

# Task 7

# Task 8
