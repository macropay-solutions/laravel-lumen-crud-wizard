# laravel-lumen-crud-wizard
## Url query language lib for RESTful CRUD (micro) services using lumen/laravel 8-9-10


#### Build RESTful services with lightning speed for any number of resources and relations using rest crud library that offers revolutionary filtering (and aggregating) capabilities for resources and their relations.

## You get:

- crud-wizard-builder: request builder that is used to encode the request in the request initiator project + documentation (min PHP 7.4 or 8.0)
- laravel-crud-wizard: request parser or translator into sql for the request target project + documentation (min PHP 8.0)
- [laravel 9 demo project that uses laravel-crud-wizard](https://github.com/macropay-solutions/laravel-crud-wizard-demo)

The code follows **PSR 12** coding standard and **DRY** principle.

Can be used with **laravel/lumen 8-9-10** and **sql** databases (tested on mysql but can also support sqlite, sqlsrv, pgsql).

Can be used to generate sql for **Elasticsearch**.

**The lib is proprietary and it can be used only after an agreement.**

**On request we can issue a test token to be used on a laravel 9 DEMO project that has a dummy db.**

**If interested, please contact us https://macropay.net/contact/**



## Features:

#### 1. Create resource
- only with allowed fields

#### 2. Read / Get resource
- also with relations

#### 3. Update / Upsert resource
- only with allowed fields (or create if not found, if incrementing = false)

#### 4. Delete resource
- only if allowed

#### 5. Bulk delete resource
- only if codded using $service->list({Controlled filters})->delete();
- not builtin

#### 6. List resources

-  **list resource** /resource?...

-  **list the resource's relation (as a resource)** /resource/{pk}/{relationName}?...

-  **list response as JSON or XLS**

   (with relations in different sheets) controlled via request header `Accept application/xls or application/json`

-  **multi sorting on the resource's columns and on its agregations**

-  **in header query**

-  **aggregations**

    sums,
  
    averages,    
  
    minimums,
    
    maximums,
  
    distinct column(s) fetching,
  
    group by (including counts, sums, averages, minimums, maximums),
  
    sub totals,
  
    sub averages,
      
    sub minimums,
      
    sub maximums,
  
    count distinct,
  
    group count,
  
    count relations,
  
    havings (including counts, sums, averages, minimums, maximums),

-  **filters for resource and relations:**

    from (inclusive),
  
    to (inclusive),
  
    in,
  
    not in,
  
    starts with,
  
    is null,
  
    is not null,
  
    contains (not fulltext search),

- **pagination** (LengthAwarePaginator)

    page,
  
    limit,
    
-  **conditions on relations**

    with/without relations,
  
    with distinct relations,
  
    has relations,
  
    has distinct relations,
  
    doesn't have relations,
  
    relations filters,

-  **custom NEW relations**

    HasManySelfThroughSelf,
  
    HasManyThrough2LinkTables,

    HasManyThrough3LinkTables,
  
    HasOneSelfThroughSelf,
  
    HasOneThrough2LinkTables,
  
    HasOneThrough3LinkTables,

#### 7. Composite primary key
- using user defined separator (default _): 12_35

#### 8. Sql debugging/logging

#### 9. Error handling/logging

## Usage:

Changes required for the first resource on laravel 9 for example:
![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/eefd0dd6-3762-4241-876a-d32cc27b690d)
With green are the changes needed for a new resource (except ResourceController).

