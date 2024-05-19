## Table of Contents

- [Overview](#overview)
- [BaseFacebook Class](#basefacebook-class)
  - [Properties](#properties)
  - [Methods](#methods)
    - [setAccessToken()](#setaccesstoken)
    - [setFileUploadSupport()](#setfileuploadsupport)
    - [getAccessToken()](#getaccesstoken)
    - [getUser()](#getuser)
    - [getLoginUrl()](#getloginurl)
    - [getLogoutUrl()](#getlogouturl)
    - [getLoginStatusUrl()](#getloginstatusurl)
    - [api()](#api)
    - [getCode()](#getcode)
    - [getUserFromAccessToken()](#getuserfromaccesstoken)
    - [getApplicationAccessToken()](#getapplicationaccesstoken)
    - [establishCSRFTokenState()](#establishcsrftokenstate)
    - [getAccessTokenFromCode()](#getaccesstokenfromcode)
    - [_restserver()](#_restserver)
    - [_graph()](#_graph)
    - [_oauthRequest()](#_oauthrequest)
    - [getAppSecretProof()](#getappsecretproof)
    - [makeRequest()](#makerequest)
    - [parseSignedRequest()](#parsesignedrequest)
    - [makeSignedRequest()](#makesignedrequest)
    - [getApiUrl()](#getapiurl)
    - [getUrl()](#geturl)
    - [getHttpHost()](#gethttphost)
    - [getHttpProtocol()](#gethttpProtocol)
    - [getBaseDomain()](#getbasedomain)
    - [getCurrentUrl()](#getcurrenturl)
    - [shouldRetainParam()](#shouldretainparam)
    - [throwAPIException()](#throwapiexception)
    - [errorLog()](#errorlog)
    - [base64UrlDecode()](#base64urldecode)
    - [base64UrlEncode()](#base64urlencode)
    - [destroySession()](#destroysession)
    - [getMetadataCookie()](#getmetadatacookie)
    - [isAllowedDomain()](#isalloweddomain)
    - [endsWith()](#endswith)
  - [Abstract Methods](#abstract-methods)
    - [setPersistentData()](#setpersistentdata)
    - [getPersistentData()](#getpersistentdata)
    - [clearPersistentData()](#clearpersistentdata)
    - [clearAllPersistentData()](#clearallpersistentdata)

## Overview

The `BaseFacebook` class provides a foundation for interacting with the Facebook platform. It offers a range of functionalities to manage user authentication, API calls, and persistent data storage. Subclasses are expected to implement four abstract methods for persistent data handling. 

The following internal code documentation provides a comprehensive overview of the `BaseFacebook` class, including its properties, methods, and abstract methods. It serves as a valuable reference guide for internal team members.

## BaseFacebook Class

### Properties

| Property | Description |
|---|---|
| `$appId` | Application ID |
| `$appSecret` | Application App Secret |
| `$user` | ID of the connected Facebook user (0 if not connected) |
| `$signedRequest` | Data from the signed_request token |
| `$state` | CSRF state variable |
| `$accessToken` | OAuth access token |
| `$fileUploadSupport` | Indicates if file uploads are enabled |
| `$trustForwarded` | Indicates if we trust HTTP_X_FORWARDED_* headers |

### Methods

#### `setAccessToken($access_token)`

Sets the access token to be used for API calls (optional).

#### `setFileUploadSupport($fileUploadSupport)`

Indicates if the server supports file upload.

#### `getAccessToken()`

Determines and returns the access token to be used for API calls.

#### `getUser()`

Gets the ID of the connected user or 0 if the user is not connected.

#### `getLoginUrl()`

Generates a login URL for redirections.

#### `getLogoutUrl()`

Generates a logout URL for redirections.

#### `getLoginStatusUrl()`

Generates a login status URL for use with AJAX.

#### `api(/* polymorphic */)`

Generic API caller. Accepts polymorphic parameters for REST or Graph API calls.

#### `getCode()`

Retrieves the authorization code from request parameters, if it exists.

#### `getUserFromAccessToken()`

Retrieves the user ID from the access token.

#### `getApplicationAccessToken()`

Returns the application access token.

#### `establishCSRFTokenState()`

Lays down a CSRF state token for the current process.

#### `getAccessTokenFromCode($code, $redirect_uri = null)`

Retrieves an access token for the given authorization code.

#### `_restserver($params)`

Invokes the old restserver.php endpoint.

#### `_graph($path, $method = 'GET', $params = array())`

Invokes the Graph API.

#### `_oauthRequest($url, $params)`

Makes an OAuth Request.

#### `getAppSecretProof($access_token)`

Generates a proof of App Secret.

#### `makeRequest($url, $params, $ch=null)`

Makes an HTTP request.

#### `parseSignedRequest($signed_request)`

Parses a signed_request and validates the signature.

#### `makeSignedRequest($data)`

Makes a signed_request blob using the given data.

#### `getApiUrl($method)`

Builds the URL for api given parameters.

#### `getUrl($name, $path='', $params=array())`

Builds the URL for given domain alias, path and parameters.

#### `getHttpHost()`

Gets the HTTP host.

#### `getHttpProtocol()`

Gets the HTTP protocol.

#### `getBaseDomain()`

Gets the base domain used for the cookie.

#### `getCurrentUrl()`

Returns the current URL, stripping it of known FB parameters that should not persist.

#### `shouldRetainParam($param)`

Returns true if and only if the key or key/value pair should be retained as part of the query string.

#### `throwAPIException($result)`

Analyzes the supplied result to determine if it was thrown because the access token is no longer valid.

#### `errorLog($msg)`

Prints to the error log if not in command line mode.

#### `base64UrlDecode($input)`

Base64 decoding that doesn't need to be urlencode()ed.

#### `base64UrlEncode($input)`

Base64 encoding that doesn't need to be urlencode()ed.

#### `destroySession()`

Destroys the current session.

#### `getMetadataCookie()`

Parses the metadata cookie that Javascript sets.

#### `isAllowedDomain($big, $small)`

Checks if $big domain is allowed by $small domain.

#### `endsWith($big, $small)`

Checks if $big string ends with $small string.

### Abstract Methods

These methods must be implemented in concrete subclasses for persistent data handling.

#### `setPersistentData($key, $value)`

Stores the given ($key, $value) pair for future retrieval.

#### `getPersistentData($key, $default = false)`

Gets the data for the given $key.

#### `clearPersistentData($key)`

Clears the data with $key from the persistent storage.

#### `clearAllPersistentData()`

Clears all data from the persistent storage.