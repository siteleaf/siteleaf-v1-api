
# API Authentication
## API Endpoints
### POST /api/v1/auth.json
Authenticates user and returns user API keys

##### Request
```shell
curl -X POST \
  -u username:password \
  https://api.siteleaf.com/v1/auth.json
```

##### Response
```json
{
  "api_key": "e4f5b6acae2c39079c07e35d90d87b1c",
  "api_secret": "106afa1abf96767774bbcc4dd766d419"
}
