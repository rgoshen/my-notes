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

![data pipeline](splunk-datapipeline.jpg)

1. Forwarders
    - have the data, and they're forwarding it off, and your data is going to be in streams
    - If it's not coming from a forwarder, it may be coming from local logs, could be from a TCP port monitoring some
      kind of network traffic event, generations, etc.
    - anything in Splunk can really be inputted into the SIM
2. Parsing
    - handled by indexer
    - turned from streams into events and then also handled by the indexer
3. Indexing
    - compressed and written to disk
4. Search
    - query and display results

### Input Types

- Http event collector
- log files
- network traffic
- etc.

### Metadata

- host-who sent the data
- source-path to the data
- source type-how the data will be formatted
- index

## App vs Add-on

### App

- something that can be launched and has a GUI component
- usually reside on the search head and visibly displayed in the drop-down in the app's menu

### Add-on or technology add-on (TA)

- can also reside in the drop-down in the app's menu, but need to change the visibility settings for add-ons to be
  displayed there
- added to Splunk instance for additional functionality
- usually runs in the background and also usually vendor specific for the type of data involved
- workstation display does not change
- can land on indexers, search head, or forwarder

## The Basics of Searching

### Search Types

- Keywords and phrases
    - designate phrases inside `""`
- File paths

### Wildcards

- `LIKE` function with the percent `( % )` symbol as a wildcard for matching multiple characters
- underscore `( _ )` character to match a single character
- asterisk `( * )` character as a wildcard to match an unlimited number of characters in a string

### Boolean Operators

- `AND`
- `OR`
- `NOT` (exclude results from your search)

> operators must be capitalized

{style="note"}

### Comparison Operators

| Operator | Example    | Result                                                      |
|----------|------------|-------------------------------------------------------------|
| `=`      | field=foo  | Multivalued field values that exactly match "foo"           |
| `!=`     | field!=foo | Multivalued field values that don't exactly match "foo"     |
| `<`      | field<x    | Numerical field values that are less than x                 |
| `>`      | field>x    | Numerical field values that are greater than x              |
| `<=`     | field<=x   | Numerical field values that are less than and equal to x    |
| `>=`     | field>=x   | Numerical field values that are greater than and equal to x |

- `!=` (value does not match the value you specify)

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
