

# Identity Providers
APIs for getting a list of all supported identity providers.

## Get Identity Provider Consent

<a id="opIdIdentityProviders_Get Identity Provider Consent"></a>

Returns an IdentityProviderConsent object.

### Request
```text 
GET /ops/v1/IdentityProviders/{identityProviderId}/Consent
?idpTenantDomain={idpTenantDomain}&idpTenantId={idpTenantId}&format={format}
```

#### Parameters

`string identityProviderId`
<br/>Identity provider unique identifier.<br/><br/>
`[optional] string idpTenantDomain`
<br/>Identity provider tenant domain. Mutually exclusive to idpTenantId. Currently only supports AAD domain.<br/><br/>`[optional] string idpTenantId`
<br/>Identity provider tenant unique identifier. Mutually exclusive to idpTenantDomain. Currently only supports AAD tenant unique identifier.<br/><br/>`[optional] any format`
<br/>Output format.<br/><br/>

### Response

|Status Code|Body Type|Description|
|---|---|---|
|200|[IdentityProvider](#schemaidentityprovider)|IdentityProviderConsent object.|
|400|[ErrorResponse](#schemaerrorresponse)|Missing or invalid inputs.|
|401|[ErrorResponse](#schemaerrorresponse)|Unauthorized.|
|403|[ErrorResponse](#schemaerrorresponse)|Forbidden.|
|404|[ErrorResponse](#schemaerrorresponse)|Identity provider or specified AAD tenant not found.|
|500|[ErrorResponse](#schemaerrorresponse)|Internal server error.|

#### Example response body
> 200 Response

```json
{
  "Id": "string",
  "DisplayName": "string",
  "Scheme": "string",
  "UserIdClaimType": "string",
  "ClientId": "string",
  "IsConfigured": true,
  "Capabilities": {
    "User": {
      "SignIn": null,
      "Invitation": null,
      "Search": null
    },
    "Group": {
      "Authorize": null,
      "Search": null
    }
  }
}
```

### Authorization

Allowed for these roles: 
<ul>
<li>Cluster Operator</li>
<li>Cluster Support</li>
</ul>

---
# Definitions

## IdentityProvider

<a id="schemaidentityprovider"></a>
<a id="schema_IdentityProvider"></a>
<a id="tocSidentityprovider"></a>
<a id="tocsidentityprovider"></a>

The model for an Identity Provider in Identity Storage.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Id|guid|false|false|Identity provider unique identifier.|
|DisplayName|string|false|true|Identity provider display name to use.|
|Scheme|string|false|true|Name of the cookie handler that will temporarily store the outcome of the external authentication.|
|UserIdClaimType|string|false|true|Type of claim.|
|ClientId|string|false|true|Client Id of the identity provider.|
|IsConfigured|boolean|false|false|Whether the identity provider has been configured.|
|Capabilities|[IdentityProviderCapabilities](#schemaidentityprovidercapabilities)|false|true|Capabilities of the identity provider.|

```json
{
  "Id": "string",
  "DisplayName": "string",
  "Scheme": "string",
  "UserIdClaimType": "string",
  "ClientId": "string",
  "IsConfigured": true,
  "Capabilities": {
    "User": {
      "SignIn": null,
      "Invitation": null,
      "Search": null
    },
    "Group": {
      "Authorize": null,
      "Search": null
    }
  }
}

```

---

## IdentityProviderCapabilities

<a id="schemaidentityprovidercapabilities"></a>
<a id="schema_IdentityProviderCapabilities"></a>
<a id="tocSidentityprovidercapabilities"></a>
<a id="tocsidentityprovidercapabilities"></a>

The model for the capabilities of an identity provider.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|User|[IdentityProviderUserCapabilites](#schemaidentityproviderusercapabilites)|false|true|User level capabilities.|
|Group|[IdentityProviderGroupCapabilites](#schemaidentityprovidergroupcapabilites)|false|true|Group level capabilities.|

```json
{
  "User": {
    "SignIn": true,
    "Invitation": true,
    "Search": true
  },
  "Group": {
    "Authorize": true,
    "Search": true
  }
}

```

---

## IdentityProviderUserCapabilites

<a id="schemaidentityproviderusercapabilites"></a>
<a id="schema_IdentityProviderUserCapabilites"></a>
<a id="tocSidentityproviderusercapabilites"></a>
<a id="tocsidentityproviderusercapabilites"></a>

The model for the user level capabilities of an identity provider.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|SignIn|boolean|false|false|Value indicating whether user log in is supported.|
|Invitation|boolean|false|false|Value indicating whether authorization via the invitation flow is supported.|
|Search|boolean|false|false|Value indicating whether user search is supported.|

```json
{
  "SignIn": true,
  "Invitation": true,
  "Search": true
}

```

---

## IdentityProviderGroupCapabilites

<a id="schemaidentityprovidergroupcapabilites"></a>
<a id="schema_IdentityProviderGroupCapabilites"></a>
<a id="tocSidentityprovidergroupcapabilites"></a>
<a id="tocsidentityprovidergroupcapabilites"></a>

The model for the group level capabilities of an identity provider.

### Properties

|Property Name|Data Type|Required|Nullable|Description|
|---|---|---|---|---|
|Authorize|boolean|false|false|Value indicating whether authorization via groups is supported.|
|Search|boolean|false|false|Value indicating whether group search is supported.|

```json
{
  "Authorize": true,
  "Search": true
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

## AadIdentityProviderConsentOutputFormat

<a id="schemaaadidentityproviderconsentoutputformat"></a>
<a id="schema_AadIdentityProviderConsentOutputFormat"></a>
<a id="tocSaadidentityproviderconsentoutputformat"></a>
<a id="tocsaadidentityproviderconsentoutputformat"></a>

#### Enumerated Values

|Property|Value|
|---|---|
|DumpAll|0|
|AadTenantSharingSummary|1|

---

