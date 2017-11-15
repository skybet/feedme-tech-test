# FeedMe Tech Test

The FeedMe tech test comes with a mock data feed service that represents one of the many types of data feeds we have to process everyday at Sky Bet.

The challenge is to consume and transform the proprietary mock data. The proprietary data format will need to be parsed and enriched with the relevant field names and data types. For more information about the feed please read the provider README: https://hub.docker.com/r/sbgfeedme/provider/

## Tasks

We realise everyone has different levels of skill and experience when it comes to development so we have listed different levels of tasks below for you to choose from. If you do not have the time or the knowledge to complete them all then that's ok, we just want to see how you approach the problem and get a feel for how you code.

#### Basic Tasks
* Create an app that connects the provider service on the exposed TCP port
* Transform the proprietary data format into JSON using the field names and data types defined in the provider /types endpoint
* Write unit tests

#### Intermediate Tasks
* Save the JSON into a NoSQL store with a document per fixture. Each document should contain the event data and the child markets and outcomes for the fixture

#### Advanced Tasks
Imagine that your app has been in use for a while now but the company has decided to start offering more fixtures. This has massively increased the number of packets being received and you have noticed that your NoSQL writes have become a bottleneck causing a packet latency that is too high for your real time data needs.

Separating the responsibility of transforming to JSON and writing to NoSQL into separate apps should help remove the bottleneck and therefore reduce the packet latency. To facilitate doing this you will need to work out a sensible way of sharding / partitioning the JSON packets by implementing the use of a message queue service such as RabbitMQ or Kafka. 

With that context in mind:

* Implement a way of sharding / partitioning the transformed JSON packets via one or more message queues
* Utilising the message queue(s) move your NoSQL logic into another app that can be run multiple times to enable concurrent NoSQL writes

#### Additional Tasks
* Implement a front end that displays the hierarchical NoSQL data. Use the Sky Bet website for layout and navigational inspiration
* Create a Dockerfile for your app(s)

## Languages

We use a mixture of coding languages at Sky Bet but for data consumption we mainly use NodeJS and Java. For this tech test we recommend you use either NodeJS or Java, but if you don't know either or you can show off your skills better in another language then please do so.

## Getting Started

* Install Docker and Docker Compose: https://docs.docker.com/compose
* Start the mock data feed by typing `docker-compose up` in the root of the test directory
* Test mock feed API by opening a browser and navigating to http://localhost:8181/types
* Test mock feed by opening a new terminal and typing `telnet localhost 8282`. You should see a stream of packets.
* If the tests above succeed then you are ready to start coding. If you decide to attempt the Intermediate and Advanced tasks then we suggest adding to or using the services listed in the docker-compose.yml file
* To destroy the test environment you can type `docker-compose down`

## The Deliverable

Replace the contents of this README.md with:

  1. A covering note explaining the technology choices you have made.
  1. Any instructions required to run your solution and tests in a Linux environment.

Email as an attachment or a link the git bundled repository showing your commit history with all your commits on the master branch:

        git bundle create <anything>.bundle --all --branches

## Equality & Diversity

We consider all candidates equally, fairly and without bias.  To that end, we ask that you do not leave any personally identifying information in your submission (such as your name within an author field or file, or in use as test data).  We run all VCS-based submissions through an anonymiser before assessment, so that there is no identifying information in the commit history, but this will only remove references in the committing author and email address, not deep in the code submitted.
