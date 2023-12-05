# DynamoDB

**incomplete?**

## What is Amazon DynamoDB? {collapsible="true" default-state="expanded"}

> "Fully managed NoSQL database service that provides fast and predictable performance with seamless scalability." —
> Amazon DynamoDB Developer Guide

- create database tables that can store and retrieve any amount of data and serve any level of request traffic
    - can scale up or scale down the table's throughput capacity without downtime or performance degradation
- provides on-demand backup capability
    - create on-demand backups and enable point-in-time recovery for your database
    - with point-in-time recovery, you can restore a table to any point in time during the last 35 days
- it allows you to delete expired items from tables automatically to help reduce storage usage and the cost of storing
  data that is no longer relevant

### High Availability and Durability

- automatically spreads the data and traffic for your tables over a sufficient number of servers to handle your
  throughput and storage requirements
- maintains consistent and fast performance
    - stored on SSDs and automatically replicated across multiple Availability Zones in an AWS region
    - can use global tables to keep DynamoDB tables in sync across AWS regions

## Amazon DynamoDB: How it Works {collapsible="true" default-state="expanded"}

### Cheat Sheet for DynamoDB

#### Basic Actions

##### Create a table

_Default_

```bash
aws dynamodb create-table \
        --table-name Music \
        --attribute-definitions \
            AttributeName=Artist,AttributeType=S \
            AttributeName=SongTitle,AttributeType=S \
        --key-schema \
            AttributeName=Artist,KeyType=HASH \
            AttributeName=SongTitle,KeyType=RANGE \
        --provisioned-throughput \
            ReadCapacityUnits=10,WriteCapacityUnits=5
```

_Windows_

```bash
aws dynamodb put-item --table-name Music --item "{\"Artist\": {\"S\": \"No One You Know
\"}, \"SongTitle\": {\"S\": \"Call Me Today\"}, \"AlbumTitle\": {\"S\": \"Somewhat
 Famous\"}, \"Awards\": {\"N\": \"1\"}}"
```

##### Read item to a table

```bash
aws dynamodb put-item \ --table-name Music \ --item file://item.json
```

##### Write item to a table

```bash
aws dynamodb get-item \ --table-name Music \ --item file://item.json
```

##### Delete item from a table

```bash
aws dynamodb delete-item --table-name Music --key file://key.json
```

##### Query a table

```bash
aws dynamodb query --table-name Music
--key-condition-expression "ArtistName=:Artist and SongName=:Songtitle"
```

##### Delete a table

```bash
aws dynamodb delete-table --table-name Music
```

##### List table names

```bash
aws dynamodb list-tables
```

#### Naming Rules

- All names must be encoded using UTF-8 and are case sensitive.
- Table names and index names must be between 3 and 255 characters long, and can contain only the following characters:
    - a-z
    - A-Z
    - 0-9
    - \_(underscore)
    - -(dash)
    - .(dot)
- Attribute names must be at least one character long, and less than 64 KB in size.

#### Service Quota Basics

##### Read and write units

- **Read capacity unit (RCU)**—One strongly consistent read per second, or tow eventually consistent reads per second,
  for items up to 4 KB in size.
- **Write capacity unit (WCU)**—One write per second, for items up to 1 KB in size.

##### Table limits

- **Table size**—no practical limit on table size (i.e., no constraints on number of items or number of bytes)
- **Number of tables**—initial quota of 2,500 tables per AWS Region
- **Page size limit for a query and scan**—1 MB per page, per query or scan
    - if a query or scan returns more than 1 MB of data, DynamoDB returns the initial matching items and
      a `LastEvaluatedKey` property that you can use in a new request to read the next page

<seealso>
[Amazon DynamoDB](https://aws.amazon.com/dynamodb/) | [Developer Guide](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)
</seealso>
