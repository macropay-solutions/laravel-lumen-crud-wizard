# laravel-lumen-crud-wizard
## Url query language lib for RESTful CRUD (micro) services using lumen/laravel 8-9-10
![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/f0ac4fef-55b8-494d-87b5-6fbb2d17e341)


### Build RESTful services with lightning speed for any number of resources and relations using rest crud library that offers revolutionary filtering (and aggregating) capabilities for resources and their relations.

## You get:

- crud-wizard-builder: request builder that is used to encode the request in the request initiator project + documentation (min PHP 7.4 or 8.0)
- laravel-crud-wizard: request parser or translator into sql for the request target project + documentation (min PHP 8.0)
- laravel 9 demo project that uses laravel-crud-wizard

The code follows **PSR 12** coding standard and **DRY** principle.

Can be used with **laravel/lumen 8-9-10** and **sql** databases (tested on mysql atm).

Can be used to generate sql for **Elasticsearch**.

**The lib is proprietary and it can be used only after an agreement.**

**On request we can issue a test token to be used on a laravel 9 DEMO project that has a dummy db.**

**If interested, please contact us https://macropay.net/contact/**

## Features:

### composite primary key using user defined separator: 12_35 or 34__56 etc
### multi sorting on the resource's columns and on its agregations
### aggregations

    sums,
  
    averages,
  
    distinct column(s) fetching,
  
    group by (including counts, sums and averages),
  
    sub totals,
  
    sub averages,
  
    count distinct,
  
    group count,
  
    count relations,
  
    havings (including counts, sums and averages),

### filters for resource and relations:

    from (inclusive),
  
    to (inclusive),
  
    in,
  
    not in,
  
    starts with,
  
    is null,
  
    is not null,
  
    contains (not fulltext search),

### pagination (LengthAwarePaginator)

    page,
  
    limit,

### sql debugging
### error logging
### in header query
### conditions on relations

    with/without relations,
  
    with distinct relations,
  
    has relations,
  
    has distinct relations,
  
    doesn't have relations,
  
    relations filters,

### update or create  a resource
### get resource
### delete resource
### custom relations

    HasManySelfThroughSelf,
  
    HasManyThrough2LinkTables,

    HasManyThrough3LinkTables,
  
    HasOneSelfThroughSelf,
  
    HasOneThrough2LinkTables,
  
    HasOneThrough3LinkTables,
