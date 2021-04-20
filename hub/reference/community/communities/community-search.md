

# Community Search
Defines the public API endpoints that are used to search communities. A community provides a way to share information, such as data streams, between customers.

## Search Streams2

<a id="opIdCommunitySearch_Search Streams2"></a>

Searches for streams within a community by query.

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/communities/{communityId}/search/streams
?query={query}&count={count}
```

#### Parameters

`string tenantId`
<br/>The id of the owning tenant.<br/><br/>`string communityId`
<br/>The id of the community.<br/><br/>
`[optional] string query`
<br/>The query. This is in the same format as used by SDS. See<br/><br/>`[optional] integer count`
<br/>The maximum total results.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[StreamSearchResult](#schemastreamsearchresult)|Returns the stream information that matches the search criteria. This is a set of objects of type `StreamSearchResult`.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad Request. The server could not understand the request due to invalid syntax.|
|401|None|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. The client does not have the required permissions to make the request.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found. The requested community was not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Request Timeout. The request has timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal Server Error. The server has encountered a situation it doesn't know how to handle.|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "TypeId": "string",
  "Description": "string",
  "Self": "string"
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Community Administrator</li>
<li>Community Member</li>
<li>Community Moderator</li>
<li>Tenant Administrator</li>
</ul>

---

## Search Streams

<a id="opIdCommunitySearch_Search Streams"></a>

Searches for streams within a community by query.

### Request
```text 
GET /api/v1-preview/tenants/{tenantId}/search/communities/{communityId}/streams
?query={query}&count={count}
```

#### Parameters

`string tenantId`
<br/>The id of the owning tenant.<br/><br/>`string communityId`
<br/>The id of the community.<br/><br/>
`[optional] string query`
<br/>The query. This is in the same format as used by SDS. See<br/><br/>`[optional] integer count`
<br/>The maximum total results.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[StreamSearchResult](#schemastreamsearchresult)|Returns the stream information that matches the search criteria. This is a set of objects of type `StreamSearchResult`.|
|400|[ErrorResponse](#schemaerrorresponse)|Bad Request. The server could not understand the request due to invalid syntax.|
|401|None|Unauthorized. The client has not been authenticated.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden. The client does not have the required permissions to make the request.|
|404|[ErrorResponse](#schemaerrorresponse)|Not Found. The requested community was not found.|
|408|[ErrorResponse](#schemaerrorresponse)|Request Timeout. The request has timed out.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal Server Error. The server has encountered a situation it doesn't know how to handle.|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "Name": "string",
  "TypeId": "string",
  "Description": "string",
  "Self": "string"
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Community Administrator</li>
<li>Community Member</li>
<li>Community Moderator</li>
<li>Tenant Administrator</li>
</ul>

---
# Definitions

## StreamSearchResult

<a id="schemastreamsearchresult"></a>
<a id="schema_StreamSearchResult"></a>
<a id="tocSstreamsearchresult"></a>
<a id="tocsstreamsearchresult"></a>

The StreamSearchResult Data Transfer Object. This is the model representation exposed to callers of controller endpoints.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|string|false|true|The id.|
|Name|string|false|true|The name.|
|TypeId|string|false|true|The type id.|
|Description|string|false|true|The description.|
|Self|string|false|true|The self link.|

```json
{
  "Id": "string",
  "Name": "string",
  "TypeId": "string",
  "Description": "string",
  "Self": "string"
}

```

---

## ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|Gets or sets Operation Id of action that caused the Error.|
|Error|string|false|true|Gets or sets the Error description.|
|Reason|string|false|true|Gets or sets the Reason for the Error.|
|Resolution|string|false|true|Gets or set the Resolution for the Error.|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string"
}

```

---

