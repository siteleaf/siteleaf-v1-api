
# Siteleaf - API Documentation
## API Authentication
Siteleaf uses Basic Auth of the user's API key and secret to authenticate each request. To retrieve a user's API key and secret, use the `POST /v1/auth` endpoint, passing the user's email and password authenticated with Basic Auth.
## API Endpoints
### POST /v1/auth.json
Authenticates user and returns user API keys

##### Request
```shell
curl -X POST -u email:password https://api.siteleaf.com/v1/auth.json
```

##### Response
```json
{
  "api_key": "e4f5b6acae2c39079c07e35d90d87b1c",
  "api_secret": "106afa1abf96767774bbcc4dd766d419"
}
```

-
### GET /v1/ping.json
Pings the server.

##### Response
```json
{
  "ping": "pong"
}
```

-
### GET /v1/users/me.json

Returns the current user.

##### Response
```json
{
  "id": "51af5e48ef75acc010000001",
  "email": "barry@whitehouse.gov",
  "firstname": "Barack",
  "lastname": "Obama",
  "created_at": "2013-06-05T11:50:32-04:00",
  "updated_at": "2013-06-05T11:50:32-04:00"
}
```

-
### GET /v1/users.json

Returns array of users associated with your sites and the sites you belong to.

##### Response
```json
[
 {
   "id": "51af5e48ef75acc010000002",
   "email": "barry@whitehouse.gov",
   "firstname": "Barack",
   "lastname": "Obama",
   "created_at": "2013-06-05T11:50:32-04:00",
   "updated_at": "2013-06-05T11:50:32-04:00"
 }
]
```

-
