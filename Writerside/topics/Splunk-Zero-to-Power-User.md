# Splunk: Zero to Power User

## Introduction

### What is Splunk?

- Security Information and Event management (SIEM)
- Network analysis tool that serves as a platform to conduct your big data analytics
    - Bring our data into Splunk, we read the raw events, and then we structure those events to make sense of the data
      that we're looking at
    - Take any kind of data structure your information is in, and is going to parse them and then create raw event
      logs for you to then search
    - Can create a bunch of different visual displays with the data you bring in and generate reports
    - Lets you tell the story of what's happening on your network and can give you insight to intelligence indicators
      you put into it and traffic that's traversing your network

  ![splunk intro](splunk_intro.jpg)

## What Makes Up Splunk?

Big three components:

1. Forwarders
    - going to forward off your data
2. Indexers
    - going to index and process your data
3. Search Headers
    - going to allow you to query and search your environment

![splunk components](splunk-components.jpg)

### Forwarder

Three kinds:

1. Universal forwarder
2. Heavy forwarder
3. Intermediary forwarder

- going to forward off the data of those raw logs to an indexer from the machine that it resides on

### Indexer

- going to take the raw data and process it
- think of an indexer as a page
    - write one line at a time starting at the top going to the bottom until the page is full
- processes those raw logs are going to get sent over in the form of buckets
    - for now, think of a bucket as a stored directory of data that lives on the indexer, and it's grouped by time
      of that data for the events because the events are processed into these time groupings

### Search Head

- leverage your search head searching by time
- most efficient delimiter to set as it tells the indexer exactly where to pull the data from disk and where to search
  on the indexer's page
- main interface for querying your data that resides in your environment
- craft your spells here, execute your search requests, and then send those requests off to the indexers to be executed

### Types of Splunk Deploys

1. Stand-alone
   ![stand alone](splunk-stand-alone.jpg)
    - download Splunk on your local computer
    - Splunk server would function as the search head and the indexer
    - handle all those search requests and processing of the data
    - no need to deploy forwarders, so your inputs would reside with whatever configurations you make on that single
      server or your laptop
2. Basic
   ![basic](splunk-basic-deployment.jpg)
    - start utilizing forwarders that reside on a remote machines to forward the data from those machines back to the
      Splunk server
    - Splunk server is still going to be our search engine and our indexer, but the inputs can now be handled by setting
      up the forwarder agents out on our remote machines
3. Multi-instance
   ![multi-instance](splunk-multi-instance.jpg)
    - common for how most companies utilize Splunk for their large production environments
    - key here is functional separation from your search head
    - indexers and the forwarders each handle their own roles
        - search head search only
        - indexer index only
        - forwarders only forward

### Clustering

![clusters](splunk-clustering.jpg)

- can increase your search capacity when we have a clustered search head
- each user can collaborate their shared resources and knowledge objects
- each search in a clustered environment should be a one for one replica of another search head in that environment, and
  you need a minimum of three search heads to have a clustered search head environment
- a deployer is what you would use to manage your search, head, cluster environment
- clustering your indexers can increase your data availability by doing data replication
    - replication factors that get involved with that
- if you were to have hundreds of forwarders out in your environment, you would need to manage these through a
  deployment server

## Getting Data into Splunk

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
