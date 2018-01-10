--- 

title: apisandbox.dev.clover.com 

language_tabs: 
   - shell 

toc_footers: 
   - <a href='#'>Sign Up for a Developer Key</a> 
   - <a href='https://github.com/lavkumarv'>Documentation Powered by lav</a> 

includes: 
   - errors 

search: true 

--- 

# Introduction 

**Version:** 3 

# /V3/MERCHANTS/{MID}
## ***GET*** 

**Summary:** Get a single merchant

### HTTP Request 
`***GET*** /v3/merchants/{mId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| expand | query | Expandable fields: [employees, bankProcessing, externalMerchant, merchantBoarding, deviceBoarding, programExpress, hierarchy, shifts, orders, address, logos, owner, items, tags, tenders, payments, gateway, printers, modifierGroups, properties, tipSuggestions, openingHours, partnerApp, selfBoardingApplication] | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Update a merchant

### HTTP Request 
`***POST*** /v3/merchants/{mId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| expand | query | Expandable fields: [employees, bankProcessing, externalMerchant, merchantBoarding, deviceBoarding, programExpress, hierarchy, shifts, orders, address, logos, owner, items, tags, tenders, payments, gateway, printers, modifierGroups, properties, tipSuggestions, openingHours, partnerApp, selfBoardingApplication] | No | array |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/ADDRESS
## ***GET*** 

**Summary:** Get a merchant's address

### HTTP Request 
`***GET*** /v3/merchants/{mId}/address` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/DEFAULT_SERVICE_CHARGE
## ***GET*** 

**Summary:** Get default service charge for a merchant

**Description:** The Merchant's default service charge, set via the Setup App (https://www.clover.com/setupapp).

### HTTP Request 
`***GET*** /v3/merchants/{mId}/default_service_charge` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/DEVICES
## ***GET*** 

**Summary:** Get all devices provisioned to a merchant

**Description:** Returns a list of all devices that are provisioned to the a merchant. This list can be viewed from the Setup App on the merchant's device or web dashboard (https://www.clover.com/setupapp/m/{mId}/devices).

### HTTP Request 
`***GET*** /v3/merchants/{mId}/devices` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| filter | query | Filter fields: [id, model, name, orderPrefix, serial, deleted_time, merchant.id, merchant.name, deviceTypeName] | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/DEVICES/{DEVICEID}
## ***GET*** 

**Summary:** Get a single device provisioned to a merchant

**Description:** Returns a single device that is provisioned to a merchant.

### HTTP Request 
`***GET*** /v3/merchants/{mId}/devices/{deviceId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| deviceId | path | Device Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/GATEWAY
## ***GET*** 

**Summary:** Get a merchant's payment gateway configuration

### HTTP Request 
`***GET*** /v3/merchants/{mId}/gateway` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/OPENING_HOURS
## ***GET*** 

**Summary:** Get a list this merchant opening hours

### HTTP Request 
`***GET*** /v3/merchants/{mId}/opening_hours` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Create a set of merchant opening hours

### HTTP Request 
`***POST*** /v3/merchants/{mId}/opening_hours` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/OPENING_HOURS/{HID}
## ***DELETE*** 

**Summary:** Delete a set of merchant opening hours

### HTTP Request 
`***DELETE*** /v3/merchants/{mId}/opening_hours/{hId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| hId | path |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***GET*** 

**Summary:** Get a specific set of merchant opening hours

### HTTP Request 
`***GET*** /v3/merchants/{mId}/opening_hours/{hId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| hId | path |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Update a set of merchant opening hours

### HTTP Request 
`***POST*** /v3/merchants/{mId}/opening_hours/{hId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| hId | path |  | Yes | string |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/ORDER_TYPE_CATEGORIES
## ***POST*** 

**Summary:** Create or delete a order type category

### HTTP Request 
`***POST*** /v3/merchants/{mId}/order_type_categories` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/ORDER_TYPES
## ***GET*** 

**Summary:** Get all order types for a merchant

**Description:** Merchants have the ability to create custom order types via the Setup App (https://www.clover.com/setupapp). These custom order types can be associated with a System Order Type (see /v3/merchants/{mId}/system_order_types). Custom Order Types can support items in all categories (filterCategories=false) or a subset of the merchant's categories (filterCategories=true and categories property contains the list of supported categories). Note that when expanding the categories for an order type, they will only be returned if this orderType only supports a subset of the categories (filterCategories=true). If the orderType supports all categories (filterCategories=false) then you should make a GET request to /v3/merchants/{mId}/categories.

### HTTP Request 
`***GET*** /v3/merchants/{mId}/order_types` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| filter | query | Filter fields: [id, deletedTime] | No | array |
| expand | query | Expandable fields: [hours, attributes, categories] | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Create Order Type For Merchant

### HTTP Request 
`***POST*** /v3/merchants/{mId}/order_types` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| expand | query | Expandable fields: [hours, attributes, categories] | No | array |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/ORDER_TYPES/{ORDERTYPEID}
## ***DELETE*** 

**Summary:** Delete an order type

### HTTP Request 
`***DELETE*** /v3/merchants/{mId}/order_types/{orderTypeId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| orderTypeId | path | Order Type Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***GET*** 

**Summary:** Get a single order type

### HTTP Request 
`***GET*** /v3/merchants/{mId}/order_types/{orderTypeId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| orderTypeId | path | Order Type Id | Yes | string |
| expand | query | Expandable fields: [hours, attributes, categories] | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Update a single order type

### HTTP Request 
`***POST*** /v3/merchants/{mId}/order_types/{orderTypeId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| orderTypeId | path | Order Type Id | Yes | string |
| expand | query | Expandable fields: [hours, attributes, categories] | No | array |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/PROPERTIES
## ***GET*** 

**Summary:** Get a merchant's properties

### HTTP Request 
`***GET*** /v3/merchants/{mId}/properties` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Update merchant properties

### HTTP Request 
`***POST*** /v3/merchants/{mId}/properties` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/ROLES
## ***GET*** 

**Summary:** Get all roles from a merchant

### HTTP Request 
`***GET*** /v3/merchants/{mId}/roles` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| filter | query | Filter fields: [modifiedTime, systemRole, name, id, deletedTime] | No | array |
| expand | query | Expandable fields: [employees] | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Create a role

### HTTP Request 
`***POST*** /v3/merchants/{mId}/roles` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/ROLES/{RID}
## ***DELETE*** 

**Summary:** Delete a role

### HTTP Request 
`***DELETE*** /v3/merchants/{mId}/roles/{rId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| rId | path | Role Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***GET*** 

**Summary:** Get a single role

### HTTP Request 
`***GET*** /v3/merchants/{mId}/roles/{rId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| rId | path | Role Id | Yes | string |
| expand | query | Expandable fields: [employees] | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Update a single role

### HTTP Request 
`***POST*** /v3/merchants/{mId}/roles/{rId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| rId | path | Role Id | Yes | string |
| expand | query | Expandable fields: [employees] | No | array |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/SYNC/{TABLE}
## ***GET*** 

**Summary:** Get a sync token (deprecated)

### HTTP Request 
`***GET*** /v3/merchants/{mId}/sync/{table}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| table | path | Table Name | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/SYSTEM_ORDER_TYPES
## ***GET*** 

**Summary:** Return a list of system order types

**Description:** Merchants can create custom Order Types via "/v3/merchants/{mId}/order_types". It is useful to associate these custom order types with particular system order types in order to group things functionally. For example, a merchant may have a "Lunch Take-Out" order type and a "Dinner Take-Out" order type. These two order types can be associated with the "TAKE-OUT-TYPE" system order type so that applications can understand that they are both take-out order types.

### HTTP Request 
`***GET*** /v3/merchants/{mId}/system_order_types` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/TENDERS
## ***GET*** 

**Summary:** Get all tenders for a merchant

### HTTP Request 
`***GET*** /v3/merchants/{mId}/tenders` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| filter | query | Filter fields: [labelKey, label, opensCashDrawer, enabled, visible, instruction, id, merchantId, systemTenderId, deletedTime, modifiedTime] | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Adds a new tender

**Description:** Returns an object representing newly added merchant tender, with a generated ID.

### HTTP Request 
`***POST*** /v3/merchants/{mId}/tenders` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/TENDERS/{TENDERID}
## ***DELETE*** 

**Summary:** Deletes an existing tender

### HTTP Request 
`***DELETE*** /v3/merchants/{mId}/tenders/{tenderId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| tenderId | path | Tender Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***GET*** 

**Summary:** Get a single merchant tender

### HTTP Request 
`***GET*** /v3/merchants/{mId}/tenders/{tenderId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| tenderId | path | Tender Id | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Updates an existing tender

**Description:** Returns an object representing updated merchant tender.

### HTTP Request 
`***POST*** /v3/merchants/{mId}/tenders/{tenderId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| tenderId | path | Tender Id | Yes | string |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/TIP_SUGGESTIONS
## ***GET*** 

**Summary:** Get all tip suggestions for a merchant

### HTTP Request 
`***GET*** /v3/merchants/{mId}/tip_suggestions` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| filter | query | Filter fields: [id, name, percentage, enabled] | No | array |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

# /V3/MERCHANTS/{MID}/TIP_SUGGESTIONS/{TID}
## ***GET*** 

**Summary:** Get a single tip suggestion

### HTTP Request 
`***GET*** /v3/merchants/{mId}/tip_suggestions/{tId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| tId | path |  | Yes | string |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

## ***POST*** 

**Summary:** Update a single tip suggestion

### HTTP Request 
`***POST*** /v3/merchants/{mId}/tip_suggestions/{tId}` 

**Parameters**

| Name | Located in | Description | Required | Type |
| ---- | ---------- | ----------- | -------- | ---- |
| mId | path | Merchant Id | Yes | string |
| tId | path |  | Yes | string |
| body | body |  | No |  |

**Responses**

| Code | Description |
| ---- | ----------- |
| 200 | No response was specified |

<!-- Converted with the swagger-to-slate https://github.com/lavkumarv/swagger-to-slate -->
