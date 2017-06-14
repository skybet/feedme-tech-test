# FeedMe Tech Test

The FeedMe tech test comes with a mock data feed service that represents one of the many types of data feeds we have to process everyday at Sky Bet.

The challenge is to consume and transform the proprietary mock data. The proprietary data format will need to be parsed and enriched with the relevant field names and data types. For more information about the feed please read the provider README: https://hub.docker.com/r/sbgfeedme/provider/

## Tasks

We realise everyone has different levels of skill and experience when it comes to development so we have listed different levels of tasks below for you to choose from. If you do not have the time or the knowledge to complete them all then that's ok, we just want to see how you approach the problem and get a feel for how you code.

**Basic Tasks**
* Create an app that connects the provider service on the exposed TCP port
* Transform the proprietary data format into JSON using the field names and data types defined in the provider README and the /types endpoint

**Intermediate Tasks**
* Write tests
* Create a _feedme_ mongo database with a _fixture_ collection
* Store the JSON in the collection with a document per fixture. Each document should contain the event data and the child markets and outcomes for the fixture

**Advanced Tasks**
* Implement mongo indexes to allow for fixture queries by _startTime_, _category_, _subCategory_ and _displayed_
* Implement a way of sharding / partitioning the packets
* Utilising the sharding / partitioning refactor your app(s) to support running parallel instances 

**Additional Tasks**
* Implement a front end that displays the hierarchical mongo data. Use the Sky Bet website for layout and navigational inspiration

## Languages

We use a mixture of coding languages at Sky Bet but for data consumption we mainly use NodeJS and Java. For this tech test we recommend you use either NodeJS or Java, but if you don't know either or you can show off your skills better in another language then please do so.

## Getting Started

* Install Docker and Docker Compose: https://docs.docker.com/compose
* Start the mock data feed by typing `docker-compose up` in the root of the test directory
* Test mock feed API by opening a browser and navigating to http://localhost:8181/types
* Test mock feed by opening a new terminal and typing `telnet localhost 8282`. You should see a stream of packets.
* If the tests above succeed then you are ready to start coding. If you decide to attempt the Intermediate and Advanced tasks then we suggest adding to or using the services listed in the docker-compose.yml file
* To destroy the test environment you can type `docker-compose down`

## Submitting Your Test

Please ensure your work is tracked in git and you are committing regularly so we can see how you worked through the various tasks. Please zip up your repo and send it over accompanied by any work notes you feel will help explain your thinking.

Good luck!