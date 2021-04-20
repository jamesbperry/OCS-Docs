

# Settings
APIs for getting Identity Storage Service settings.

## Get Identity Storage Service setting value

<a id="opIdSettings_Get Identity Storage Service setting value"></a>

Returns the value of an Identity Storage Service setting.

### Request
```text 
GET /ops/v1/services/identitystorage/Settings/{settingKey}
```

#### Parameters

`string settingKey`
<br/>Name of the setting to read.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|string|Value of the requested service setting.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Requested setting not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

#### Example response body
> 401 Response

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "DynamicProperties": {
    "property1": null,
    "property2": null
  },
  "property1": null,
  "property2": null
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Cluster Operator</li>
<li>Cluster SecretsAdministrator</li>
<li>Cluster Support</li>
</ul>

---

## Get header for Identity Storage Service setting

<a id="opIdSettings_Get header for Identity Storage Service setting"></a>

Get header for an Identity Storage Service setting.

### Request
```text 
HEAD /ops/v1/services/identitystorage/Settings/{settingKey}
```

#### Parameters

`string settingKey`
<br/>Name of the setting to read.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|None|Header of the requested service setting.|
|401|None|Unauthorized.|
|403|None|Forbidden.|
|404|None|Requested setting not found.|
|500|None|Internal server error.|

### Authorization

Allowed for these roles: 
<ul>
<li>Cluster Operator</li>
<li>Cluster SecretsAdministrator</li>
<li>Cluster Support</li>
</ul>

---
# Definitions

## ErrorResponse

<a id="schemaerrorresponse"></a>
<a id="schema_ErrorResponse"></a>
<a id="tocSerrorresponse"></a>
<a id="tocserrorresponse"></a>

Object returned whenever there is an error.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|Operation unique identifier of action that caused the error.|
|Error|string|true|false|Error description.|
|Reason|string|true|false|Reason for the error.|
|Resolution|string|true|false|Resolution to resolve the error.|
|DynamicProperties|object|false|true|Additional properties.|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "DynamicProperties": {
    "property1": null,
    "property2": null
  },
  "property1": null,
  "property2": null
}

```

---

