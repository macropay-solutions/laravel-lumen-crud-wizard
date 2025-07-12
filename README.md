# laravel-lumen-crud-wizard - MaravelQL - maravel-rest-wizard

![laravel-lumen-crud-wizard-logo](https://github.com/user-attachments/assets/6dab67d1-0d72-4eb8-8dcb-19c6caf87a04)

## Url query language lib for RESTful CRUD (micro) services using lumen/laravel 8-9-10-11-12, maravel/maravelith 10

### This is not just another CRUD lib!
It has built in filtering capabilities that can be used for listing but also for mass deleting, so it could be called a CRU**F**D (create, read, update, **filter** and delete) lib instead.

#### Build RESTful services with lightning speed for any number of resources and relations using rest crud library that offers revolutionary filtering (and aggregating) capabilities for resources and their relations.

```Long story short: so you don't have to code the filters by hand.```

For free version see [Laravel Crud Wizard Free](https://github.com/macropay-solutions/laravel-crud-wizard-free)

See also [Laravel Lumen Crud Wizard Decorator](https://github.com/macropay-solutions/laravel-lumen-crud-wizard-decorator).



I. [You get](#i-you-get)

II. [Features](#ii-features)

II.1. [Create resource](#ii1-create-resource)

II.2. [Read / Get resource](#ii2-readget-resource)

II.3. [Update / Upsert / Increment resource](#ii3-updateupsertincrement-resource)

II.4. [Delete resource](#ii4-delete-resource)

II.5. [Bulk delete resource](#ii5-bulk-delete-resource)

II.6. [List resource](#ii6-list-resource)

II.7. [Composite primary key](#ii7-composite-primary-key)

II.8. [Sql debugging/logging](#ii8-sql-debugginglogging)

II.9. [Error handling/logging](#ii9-error-handlinglogging)

II.10. [Datetime NOT timestamp for created_at and updated_at columns](#ii10-datetime-not-timestamp-for-created_at-and-updated_at-columns)

II.11. [Autocomplete on model properties](#ii11-autocomplete-on-model-properties)

II.12. [Read-only DTO for model](#ii12-read-only-dto-for-model)

III. [Usage](#iii-usage)

IV. [Try it](#iv-try-it)



## I. You get:

- [laravel-crud-wizard-client](https://github.com/macropay-solutions/laravel-lumen-crud-wizard-client): request builder that is used to encode the request in the request initiator project + documentation (min PHP 7.4 or 8.0) capable of async calls for count to speed up the list on big tables
- laravel-crud-wizard: request parser or translator into sql for the request target project + documentation (min PHP 8.0)
- [laravel 9 demo project that uses laravel-crud-wizard](https://github.com/macropay-solutions/laravel-crud-wizard-demo)

The code follows **PSR 12** coding standard and **DRY** principle.

Can be used with **laravel/lumen 8-9-10-11-12** and **sql** databases (tested on mysql/mariadb but can also support sqlite, sqlsrv, pgsql).

Can be used to generate sql for **Elasticsearch**.

**The lib is proprietary and can be used only after an agreement.**

**On request we can issue a test token to be used on a laravel 9 DEMO project that has a dummy db. The url query language can be tested/tried without a token (only for filtering) in our [demo page](https://laravel-crud-wizard.com/laravel-9/laravel-lumen-crud-wizard).**

**If interested, please [contact us](https://macropay.net/contact/).**



## II. Features:

#### II.1. Create resource
- only with allowed fields

#### II.2. Read/Get resource
- also with relations, appends, count relations and exist relations

#### II.3. Update/Upsert/Increment resource
- only with allowed fields (or create if not found, if (pk) incrementing = false or by custom condition if the identifier is other than the pk)
- also with relations, appends, count relations and exist relations
- supports **incrementing** for the summable columns ONLY. Use "++x[.xx]" or "--x[.xx]". Incrementing can be made together with other updates. Incrementing is possible only on existing resource.

#### II.4. Delete resource
- only if allowed

#### II.5. Bulk delete resource
- only if coded using $service->list({Controlled filters})->delete();
- not built-in

#### II.6. List resource

-  **list resource** /resource?...

-  **list the resource's relation (as a resource)** /resource/{pk}/{relationName}?...

-  **list response as JSON or XLS**

   (with relations in different sheets) controlled via request header `Accept application/xls or application/json`

-  **multi sorting on the resource's columns and on its aggregations and default sort**

-  **in header query for GET requests or POST requests for filtering with sensitive data**
  
-  **to avoid 499 http code in access logs and DB block via api call, the DB select statements are restricted with a timeout for mysql >= 5.7.4 and mariadb >= 10.1.1**

-  **aggregations** (**including on the relation's columns**)

    sums,
  
    averages,    
  
    minimums,
    
    maximums,
  
    distinct column(s) fetching (including custom sql: 'distinct COALESCE(NULLIF(`{table}`.`column`, ""), `{table}`.`column2`) as column)',
  
    group by (columns of the resource plus relation counts and date cast able columns, but if index required on filtering is enabled then first group by column MUST be indexed and not casted; if distincts are used then group by is disregarded),
  
    sub totals,
  
    sub averages,
      
    sub minimums,
      
    sub maximums,
  
    count distinct,
  
    group count,
  
    count relations,

    exist relations,
  
    havings (including relation counts, group counts, count distincts, sums, averages, minimums, maximums),

-  **filters for resource and relations:**

    from (inclusive),
  
    to (inclusive),
  
    in,
  
    not in,
  
    starts with,
  
    is null (inluding also (column in (...) OR column IS NULL) condition),
  
    is not null,
  
    contains (not fulltext search),

    notContains,

- **pagination** (LengthAwarePaginator as default or Paginator or CursorPaginator)

    page,
  
    limit, // limit=0 for count only without pages

    simplePaginate (request response without total count)

    cursor
    
-  **conditions on relations**

    with/without relations,

    with appends, (need custom coding)
  
    with distinct (columns from) relations,
  
    has relations,
  
    has distinct relations,
  
    doesn't have relations,
  
    relations OPTIMIZED filters (except morph relations),

-  **custom NEW relations**

    HasManySelfThroughSelf,
  
    HasManyThrough2LinkTables,

    HasManyThrough3LinkTables,
  
    HasOneSelfThroughSelf,
  
    HasOneThrough2LinkTables,
  
    HasOneThrough3LinkTables,
   
-  **MVCC DB "select count(*) from table" slow query solution in MySql >= 8**

    In worst case scenario will estimate the count rather than execute the count without index filter

-  **Prevent DB blocking via API with long running queries for mysql >= 5.7.4 and mariaDB >= 10.1.1**

-  **retroactive working StreamedJsonResponse https://github.com/laravel/framework/discussions/55509**
  

#### II.7. Composite primary key
- using user defined separator (default _): 12_35

#### II.8. Sql debugging/logging

#### II.9. Error handling/logging

#### II.10. Datetime NOT timestamp for created_at and updated_at columns

#### II.11. Autocomplete on model properties

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/206319cc-157d-4282-8ac1-c78fb720b237)

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/51e4c334-b7d2-4997-aeac-d2aa1a5e2681)

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/0b0590e5-e0a5-4a6f-a749-0daad6d3560f)

Also if autocomplete is needed on the model itself, them @ mixin can be added on the model:

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/865f3efd-d1ca-413e-b54c-6dae8de3d74a)

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/b24c2e88-445a-4ee6-8bf3-545173b3bc05)

Putting @ property on the model is less effective as opposed to this new Attribute class because of the public properties from eloquent model. Also it will avoid polluting the autocomplete with functions and properties from Eloquent model.

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/07c5e84e-f46f-4a65-8a6b-9bd05940da87)

#### II.12. Read-only DTO for model


## III. Usage:

Changes required for the first resource on laravel 9 for example:
![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/eefd0dd6-3762-4241-876a-d32cc27b690d)
With green are the changes needed for a new resource (except ResourceController).

See [laravel 9 demo project that uses laravel-crud-wizard](https://github.com/macropay-solutions/laravel-crud-wizard-demo)

## IV. Try it:

Postman [collection](https://laravel-crud-wizard.com/laravel-10-crud-test.postman_collection.json). Please [contact us](https://macropay.net/contact/) for a bearer token.

The lib filtering capabilities (url query language) can be tested WITHOUT bearer token on [laravel 9 demo page](https://laravel-crud-wizard.com/laravel-9/laravel-lumen-crud-wizard) or [laravel 10 demo page](https://laravel-crud-wizard.com/laravel-10/laravel-lumen-crud-wizard)

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/83ff915a-c455-462f-8461-c39797e4fc66)

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/30c453e2-6357-4191-9511-4a77dd960385)

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/33f5ff45-a97d-49c1-a6b1-dc6910382fd5)

Use our demo UI url query builder:

![image](https://github.com/macropay-solutions/laravel-lumen-crud-wizard/assets/153634237/8570a5f7-5739-4daa-bccc-9fa0998cd421)


Note that the demo db has over 3.7 million operations.
