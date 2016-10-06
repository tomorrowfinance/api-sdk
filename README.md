# api-sdk

Tomorrow Finance provides api access to selected organisations for integration with data & functionality that our platform provides

## Request & Response

For version 1 of the api, all current requests are made via posts. Authentication tokens are handled via the request header (not POST data).

All responses are provided back as JSON. There is no other currently supported output at this time.

## Authentication

Before you can begin, you will be provided a api `Client ID` and a `Client Secret` from Tomorrow Finance. This will be used to authenticate any further requests:

```
curl --data "clientId={clientId}&clientSecret={clientSecret}" https://www.tomorrowfinance.com.au/api/v1/token
```

If the client id/secret is INVALID the appropriate `4XX` code will be returned as the response. 

If the request is VALID, a json response will be provided. This will have a `token` key. This key represents an your authenticated api user. This token will expire 5 minutes from when it is created.

## Features

### Single Sign On

![sso process](api single sign on.png)
