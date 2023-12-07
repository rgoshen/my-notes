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

#### What does that mean?

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
