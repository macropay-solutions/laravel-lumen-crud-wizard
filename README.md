# laravel-lumen-crud-wizard
Url query language lib for RESTful CRUD (micro) services using lumen/laravel 8-9-10

# Build RESTful services with lightning speed for any number of resources and relations using rest crud library that offers revolutionary filtering (and aggregating) capabilities for resources and their relations.

It features:

## multi sorting on the resource's columns only
## aggregations

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

## filters for resource and relations:

    from (inclusive),
  
    to (inclusive),
  
    in,
  
    not in,
  
    starts with,
  
    is null,
  
    is not null,
  
    contains (not fulltext search),

## pagination (LengthAwarePaginator)

    page,
  
    limit,

## sql debugging
## error logging
## in header query
## conditions on relations

    with/without relations,
  
    with distinct relations,
  
    has relations,
  
    has distinct relations,
  
    doesn't have relations,
  
    relations filters,

## update or create  a resource
## get resource
## delete
## custom relations

    HasManySelfThroughSelf,
  
    HasManyThrough2LinkTables,

    HasManyThrough3LinkTables,
  
    HasOneSelfThroughSelf,
  
    HasOneThrough2LinkTables,
  
    HasOneThrough3LinkTables,




The code follows **PSR 12** coding standard and **DRY** principle.

Can be used with **laravel/lumen 8-9-10** and **sql** databases (tested on mysql atm).

Can be used to generate sql for **Elasticsearch**.

**The lib is proprietary and it can be used only after an agreement.**

**If interested, please contact us https://macropay.net/contact/**
