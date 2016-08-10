# Connect API (Alpha)

Write Date: April 14, 2016  
Last Update: July 5, 2016  
API Version Prefix: `/api`

## Routes

### GET `/catalog/track` 

Gets all tracks. You can use default collection query options.

**WARNING**
> Even though this route is publicly available it may not be available in future releases.
> It is advised to fetch releases and their tracks. See below.

### GET `/catalog/track/:id` 

Gets a track by id.

### GET `/catalog/release` 

Gets all releases. You can use default collection query options.

### GET `/catalog/release/:catalog_id` 

Gets a release by id OR catalog id.

### GET `/catalog/release/:id/tracks` 

Gets you tracks for a release. You can use default collection query options.

### GET `/catalog/artist`

Gets you artists.

### GET `/catalog/artist/:vanity_uri`

Gets you an artist by id or their vanity URI

### GET `/catalog/artist/:vanity_uri/releases`

Gets you an artists releases.

### GET `/playlist` 

Gets you a playlist that is publicly available.

### GET `/playlist/:id/tracks` 

Gets you tracks for a playlist. You can use default collection query options.

## Query Options

Query options are simple URL query string key values.

### Collections

#### Fields 

`fields=a,b,c`

Specifiy what fields you wish to recieve by a comma separated string.

**WARNING**
> Some fields are manatory and will appear anyways.

#### Identifiers 

`ids=id1,id2`

Specifies specific ids you want to fetch instead of the whole collection.

#### Offset/Skip 

`skip=100`

Specifies the starting point of the collection you wish to fetch.

#### Amount/Limit 

`limit=10`

Specifies the number of results you wish to fetch.

**WARNING**
> In the future it may be capped.

#### Fuzzy Match

`fuzzy=field,value,field2,value2`

Specifies searches with fuzzy matching. This is an AND operation. Use `fuzzyOr` for OR operations.  
The parameter value is a comma separated pair list.

#### Filter Match

`filter=field,value,field2,value2`

Specifies searches with exact matching. This is an AND operation. Use `filterOr` for OR operations.  
The parameter value is a comma separated pair list.
