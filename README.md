# api-sdk

Tomorrow Finance provides api access to selected organisations for integration with data & functionality that our platform provides

## Request & Response

For V1 of the api, all current requests are made via posts. Authentication tokens are handled via the request header (not POST data).

All requests should be made to `https://www.tomorrowfinance.com.au/api/v1/{endpoint}`.

All responses are provided back as JSON, if the request is valid. Invalid responses will throw back the relevant HTTP status code.
There is no other currently supported output at this time.

## Authentication

Before you can begin, you will be provided a `API` `Client ID` and a `Client Secret` from Tomorrow Finance. This will be used to authenticate any further requests:

```
curl --data "clientId={api.clientId}&clientSecret={api.clientSecret}" https://www.tomorrowfinance.com.au/api/v1/token
```

If the client id/secret is INVALID the appropriate `4XX` code will be returned as the response. 

If the request is VALID, a json response will be provided. This will have a `token` key. This key represents an your authenticated api user. This token will expire 5 minutes from when it is created.

All subsequent requests to the API will need to have this token passed to it within the header of the request

```
curl --header "X-API-Token: {token}" --data "param=value" https://www.tomorrowfinance.com.au/api/v1/{endpoint}
```

## Features

### Single Sign On

![sso process](api single sign on.png)

This will generate a tempoary SSO token that will be valid for 5 minutes.

ENDPOINT: user/authenticate
PARAMS: 
- clientId: the client id of the USER (not the `API` client id)
- clientSecret: the client id of the USER (not the `API` client secret)

The client id/secret for each user that has SSO will be manually provided to you (for security reasons). You'll need to contact tomorrow finance to gain this information.

```
curl --data "clientId={user.clientId}&clientSecret={user.clientSecret}" https://www.tomorrowfinance.com.au/api/v1/token
```

Once you have generated the specific users token, you can then generate a link to our platform:

```
<a href="https://www.tomorrowfinance.com.au/sso/{token}">Tomorrow Finance</a>
```
