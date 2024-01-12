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

> use sparingly because they are very taxing on the Splunk search

{style="warning"}

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

## Knowledge Objects

- tools and useful things to take advantage when conducting analysis

### What are Knowledge Objects?

![knowledge objects](Splunk-timechart-data-models-and-alert.png)

- a set of user-defined searches, fields, and reports that enrich your data and give it structure

1. Tools
    - conduct analysis, enrich your events
2. Fields, field extractions, a lookup, tags, a field alias, data model or a saved search
3. Teamwork
    - shareable, reusable, and searchable based on permission sets

### How are they managed?

1. Knowledge Manager
    - Ruler of the KOs
    - a person who provides centralized oversight and maintenance of KOs for a Splunk environment
    - Ex. Owner of a dashboard
2. Naming conventions
    - `<Group name>_<type>_<description>`
    - Ex. SOC_alert_LoginFailures

### Permissions

1. Private
    - only the person who created the object can use or edit it
2. This app only
    - objects persist in the context of a specific app
3. All apps
    - objects persist globally across all apps

## Show Me the Fields

### What are fields?

- key-value pairs
- searchable by name
- ability to search mutliple fields at once or exclude fields from a search
- created by Splunk or recognized from an Add-On

> field names are case-sensitive (when searching) but field values are not

> if no operators are set when searching fields, then Splunk assumes to search with `AND`

#### Meta-fields

1. Source
2. Source-type
3. Host

### Making Use of Your Fields

- you can create more seleccted fields

#### `!=` vs `NOT`

`index=web sourcetype=access_combined categoryId!=SPORTS`

- This will tell Splunk to search for everything that does not contain the field value of sports for that field

`index=web sourcetype=access_combined NOT categoryId!=SPORTS`

- will tell Splunk to search for everything that does not contain the field value of sports and all events where the
  category ID field doesn't exist

## Search Processing Language (SPL)

### Splunk syntax and colors

- Orange - command modifiers
    - tell the search what you are looking for
    - can include your boolean operators, your keywords, or your phrases with `as` or `by` clauses set
        - `OR`, `NOT`, `AND`, `as`, `by`
- Blue - commands
    - tell Splunk what you want to do with the results
        - `Stats`, `Table`, `Rename`, `Dedup`, `Sort`, `Timechart`
- Green - arguments
    - these are the variables that you apply to the search, usually to a function
        - `Limit`, `Span`
- Purple - functions
    - tell your search to do things such as perform mathematical functions or calculate fields
        - `Tostring`, `Sum`, `Values`, `Min`, `Max`, `Avg`

### Building effective SPLs

`index=web OR index=security | stats sum(bytes) as Total_Bytes | eval Total_Bytes = tostring(Total_Bytes, "commas")`

`index=web OR index=security`

- pull all data from disk
    - name you indexes and meta-fields

`stats sum(bytes) as Total_Bytes`

- set your command
    - what are we trying to do

`eval Total_Bytes = tostring(Total_Bytes, "commas")`

- determine your functions
    - do we need to calculate results?
- call your arguments
    - what fields are needed?

The search was built from left to right, starting with determining where the data resides, setting the calculations, and
then formatting the results, how to be displayed

### Table, rename, fields, dedup, sort

- `table`
    - make a table of the results based off the variables and arguments you set in your search.
- `rename`
    - rename the fields that currently exist in the data or rename fields that you've calculated and built in your
      searches
- `fields`
    - allows you to call on fields you want to include or exclude in your results
- `dedup`
    - stands for a duplicate and it will remove duplicated values from the results from the fields you select to
      duplicate
- `sort`
    - will sort your results based off the arguments you set

## Transforming Your Search

### What is a Transforming Command?

- search command that orders the results into a data table
- transform the specified cell value for each event into numerical values that Splunk can use for statistical purposes
- searches that use transforming commands are called transforming searches

> If you're running Splunk in Smart Mode, this is the mode that will toggle the search behavior
> based on if the search contains a transforming command. If it does, then it's gonna act like Fast mode, and if it does
> not, it's going to act like Verbose mode

### Three Transforming Commands

1. Top
    - finds the top common values of a field in a table
    - top 10 results by default
    - can use with arguments
2. Rare
    - finds the least common values of a field
    - opposite of top
3. Stats
    - calculate statistics
    - count, dc, sum avg list, values, etc.

## What are the Events Telling Me?

### Transaction Command

- Events can be grouped into transactions based on the associated and related identified fields
- helps enumerate that relation

#### Arguments

- maxspan
    - Max time between all related events
    - Ex: `maxspan=15m`
- maxpause
    - Max time between each event
    - Ex: `maxpause=1m`
- startswith & endswith
    - Set your variables for keywords, Windows EventIDs, or other searches of interest
    - Ex: `startswith=4624` & `endswith=4647`

> transaction command can be a very taxing search to run in your environment, so should be used sparingly, especially
> for huge data sets

{style="warning"}

### Investigating your events

- Events that span time
    - they can come from multiple hosts, relate to one host of interest
- Grouping of events
    - show the entire conversation, from start to finish in one view
- Aid investigations
    - relate user activity for logins, session lengths, browsing history, etc.
- Log validation
    - check to see if data is related to network logs of interest, website traffic, emails, etc.

### Transaction vs stat

| Transaction                                           | Stats                                                                                        |
|-------------------------------------------------------|----------------------------------------------------------------------------------------------|
| slow and will tax your environment                    | faster, more efficient searching                                                             |
| granular analysis (logs, user behavior, conversations | looking at larger pools of events for trend analysis (no limit on number of events returned) |
| small scope on one item of interest                   | broad searching and grouping events                                                          |
| correlations need to be found from start to end       | mathematical functions needed                                                                |

<seealso>
<!--Give some related links to how-to articles-->
</seealso>
