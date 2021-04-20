

# User Information
Returns user properties via a call to an external Identity Provider for which we have a "Deeper Integration".

## Get User Info for Authentication

<a id="opIdUserInformation_Get User Info for Authentication"></a>

Get UserInformation for Authentication.

### Request
```text 
GET /cluster/v1/tenants/{tenantId}/identityproviders/{identityProviderId}/users/{identityProviderSpecificUserId}/UserInformation
?claimTypes={claimTypes}
```

#### Parameters

`string tenantId`
<br/>Id of Tenant.<br/><br/>`string identityProviderId`
<br/>Identity Provider Id.<br/><br/>`string identityProviderSpecificUserId`
<br/>Identity Provider Specific User Id. Ex. ExternalUserId for AD, ObjectId for AAD.<br/><br/>`string claimTypes`
<br/>Claim Types.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[UserInformationResponse](#schemauserinformationresponse)|UserInformation or UserInformationMultiStatusResponse.|
|207|[UserInformationMultiStatusResponse](#schemauserinformationmultistatusresponse)|UserInformation or UserInformationMultiStatusResponse.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs, or Client limit exceeded.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

#### Example response body
> 200 Response

```json
{
  "UserInformation": {
    "property1": [
      "string"
    ],
    "property2": [
      "string"
    ]
  }
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Tenant Administrator</li>
</ul>

---
# Definitions

## UserInformationResponse

<a id="schemauserinformationresponse"></a>
<a id="schema_UserInformationResponse"></a>
<a id="tocSuserinformationresponse"></a>
<a id="tocsuserinformationresponse"></a>

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|UserInformation|object|false|true|None|

```json
{
  "UserInformation": {
    "property1": [
      "string"
    ],
    "property2": [
      "string"
    ]
  }
}

```

---

## UserInformationMultiStatusResponse

<a id="schemauserinformationmultistatusresponse"></a>
<a id="schema_UserInformationMultiStatusResponse"></a>
<a id="tocSuserinformationmultistatusresponse"></a>
<a id="tocsuserinformationmultistatusresponse"></a>

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|false|true|None|
|Error|string|false|true|None|
|Reason|string|false|true|None|
|ChildErrors|[[MultiStatusResponseChildError](#schemamultistatusresponsechilderror)]|false|true|None|
|Data|[UserInformationResponse](#schemauserinformationresponse)|false|true|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "ChildErrors": [
    {
      "OperationId": "string",
      "Error": "string",
      "Reason": "string",
      "Resolution": "string",
      "StatusCode": 0,
      "ModelId": "string",
      "property1": null,
      "property2": null
    }
  ],
  "Data": {
    "UserInformation": {
      "property1": [
        "string"
      ],
      "property2": [
        "string"
      ]
    }
  }
}

```

---

## MultiStatusResponseChildError

<a id="schemamultistatusresponsechilderror"></a>
<a id="schema_MultiStatusResponseChildError"></a>
<a id="tocSmultistatusresponsechilderror"></a>
<a id="tocsmultistatusresponsechilderror"></a>

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|OperationId|string|true|false|None|
|Error|string|true|false|None|
|Reason|string|true|false|None|
|Resolution|string|true|false|None|
|StatusCode|int32|false|false|None|
|ModelId|string|false|true|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "StatusCode": 0,
  "ModelId": "string",
  "property1": null,
  "property2": null
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
|OperationId|string|true|false|None|
|Error|string|true|false|None|
|Reason|string|true|false|None|
|Resolution|string|true|false|None|

```json
{
  "OperationId": "string",
  "Error": "string",
  "Reason": "string",
  "Resolution": "string",
  "property1": null,
  "property2": null
}

```

---

