---
title: 'Redis Helpers'
pubDate: 2021-07-01 14:00:00
description: 'Redis Helpers'
author: 'Doug Stowell'
authorAvatar: '/src/assets/dougs.jpg'
image:
    url: '/src/assets/redis.png'
    alt: 'Redis Helpers'
tags: ["redis", "spine"]
isPinned: true
---

## General

```text
redis-cli -n 12
```

## Spine Specific.

```text
# DB ids - no names for some reason.
https://nhsd-confluence.digital.nhs.uk/display/SPINE/Redis+Database+List

# Connect to redis and list some practices starting with Y and look at the detail. e.g. retrieveCCG uses this.
redis-cli
select 12
keys Y*

redis-cli -n 12
keys Y*

hgetall L83073
hgetall Y00254
hgetall A91169
hgetall Y00613

hget PostCodeMap LS10_1NE

smembers 'DispensingPractices'
sismember 'DispensingPractices' 'Y00254'
sismember 'DispensingPractices' 'X00254'

# Connect to ODS DB and query GP list
select 3

smembers GPPracticeCodeList

sismember GPPracticeCodeList Y00001
sismember GPPracticeCodeList W00005

# Connect to Web session DB
redis-cli
select 0
hgetall a556446b-8ab6a22dddbb40398272d1c700b4d2c7

hgetall DSA011201001_MD

# See if NHAIS or not.
redis-cli
select 0
smembers 993101234567_CATBAG
smembers 482095086013_CATBAG

# PAF Data - note only LS loaded in dev
redis-cli -n 8
hgetall LS177HZ

```
