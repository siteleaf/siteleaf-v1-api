
# Siteleaf - API Documentation
## API Authentication
Siteleaf uses Basic Auth of the user's API key and secret to authenticate each request. To retrieve a user's API key and secret, use the `POST /v1/auth` endpoint, passing the user's email and password authenticated with Basic Auth.
## API Endpoints
### POST /v1/auth.json
Authenticates user and returns user API keys

#### Request
```shell
curl -X POST -u email:password https://api.siteleaf.com/v1/auth.json
```

#### Response
```json
{
  "api_key": "e4f5b6acae2c39079c07e35d90d87b1c",
  "api_secret": "106afa1abf96767774bbcc4dd766d419"
}
```

-
### GET /v1/ping.json
Pings the server.

#### Response
```json
{
  "ping": "pong"
}
```

-
### GET /v1/users/me.json

Returns the current user.

#### Response
```json
{
  "id": "51afb050ef75acb2e8000001",
  "email": "barry@whitehouse.gov",
  "firstname": "Barack",
  "lastname": "Obama",
  "created_at": "2013-06-05T17:40:32-04:00",
  "updated_at": "2013-06-05T17:40:32-04:00"
}
```

-
### GET /v1/users.json

Returns array of users associated with your sites and the sites you belong to.

#### Response
```json
[
 {
   "id": "51afb050ef75acb2e8000002",
   "email": "barry@whitehouse.gov",
   "firstname": "Barack",
   "lastname": "Obama",
   "created_at": "2013-06-05T17:40:32-04:00",
   "updated_at": "2013-06-05T17:40:32-04:00"
 }
]
```

-
### GET /v1/sites.json

Returns an array of sites that the authenticated user belongs to.

#### Params
* **domain** *(optional)* — Site domain
* **include** *(optional)* — Array of entities to include (`user`, `pages`)


#### Response
```json
[
 {
   "id": "51afb050ef75acb2e8000004",
   "title": "My Site",
   "domain": "mysite.com",
   "cname": "abcdefghijklmnopqrst-abcdefghijklmnopqrstuvwxyz123456.a1.abc.rackcdn.com",
   "timezone": "Eastern Time (US & Canada)",
   "created_at": "2013-06-05T17:40:32-04:00",
   "updated_at": "2013-06-05T17:40:32-04:00",
   "user_id": "51af47a8ef75ac5e8c000001"
 }
]
```

-
### POST /v1/sites.json

Creates a site belonging to the authenticated user.

#### Params
* **title**  — Site title
* **domain**  — Site domain
* **timezone** *(optional)* — Site timezone


#### Response
```json
{
  "id": "51afb050ef75acb2e8000003",
  "title": "My Site",
  "domain": "mysite.com",
  "cname": "abcdefghijklmnopqrst-abcdefghijklmnopqrstuvwxyz123456.a1.abc.rackcdn.com",
  "timezone": "Eastern Time (US & Canada)",
  "created_at": "2013-06-05T17:40:32-04:00",
  "updated_at": "2013-06-05T17:40:32-04:00",
  "user_id": "51af47a8ef75ac5e8c000001"
}
```

-
### GET /v1/sites/:id.json

Returns the given site.

#### Params
* **include** *(optional)* — Array of entities to include (`user`, `pages`)


#### Response
```json
{
  "id": "51afb050ef75acb2e8000003",
  "title": "My Site",
  "domain": "mysite.com",
  "cname": "abcdefghijklmnopqrst-abcdefghijklmnopqrstuvwxyz123456.a1.abc.rackcdn.com",
  "timezone": "Eastern Time (US & Canada)",
  "created_at": "2013-06-05T17:40:32-04:00",
  "updated_at": "2013-06-05T17:40:32-04:00",
  "user_id": "51af47a8ef75ac5e8c000001"
}
```

-
### PUT /v1/sites/:id.json

Updates the given site.

#### Params
* **title** *(optional)* — Site title
* **domain** *(optional)* — Site domain
* **timezone** *(optional)* — Site timezone
* **hosting** *(optional)* — Site hosting (`siteleaf`, `ftp`, `s3`, `cloudfiles`)
* **ftp_settings** *(optional)* — Site FTP settings (see hosting settings)
* **s3_settings** *(optional)* — Site S3 settings (see hosting settings)
* **cloudfiles_settings** *(optional)* — Site Cloudfiles settings (see hosting settings)


#### Response
```json
{
  "id": "51afb050ef75acb2e8000003",
  "title": "My Site",
  "domain": "mysite.com",
  "cname": "abcdefghijklmnopqrst-abcdefghijklmnopqrstuvwxyz123456.a1.abc.rackcdn.com",
  "timezone": "Eastern Time (US & Canada)",
  "created_at": "2013-06-05T17:40:32-04:00",
  "updated_at": "2013-06-05T17:40:32-04:00",
  "user_id": "51af47a8ef75ac5e8c000001"
}
```

-
### DELETE /v1/sites/:id.json

Deletes the given site.

#### Response
```json
{
  "id": "51afb050ef75acb2e8000003",
  "title": "My Site",
  "domain": "mysite.com",
  "cname": "abcdefghijklmnopqrst-abcdefghijklmnopqrstuvwxyz123456.a1.abc.rackcdn.com",
  "timezone": "Eastern Time (US & Canada)",
  "created_at": "2013-06-05T17:40:32-04:00",
  "updated_at": "2013-06-05T17:40:32-04:00",
  "user_id": "51af47a8ef75ac5e8c000001"
}
```

-
### GET /v1/sites/:id/pages.json

Returns an array of all pages for the given site.

#### Params
* **include** *(optional)* — Array of entities to include (`user`, `site`, `parent`, `pages`, `posts`, `assets`, `meta`)


#### Response
```json
{
  "id": "51afb050ef75acb2e8000003",
  "title": "My Site",
  "domain": "mysite.com",
  "cname": "abcdefghijklmnopqrst-abcdefghijklmnopqrstuvwxyz123456.a1.abc.rackcdn.com",
  "timezone": "Eastern Time (US & Canada)",
  "created_at": "2013-06-05T17:40:32-04:00",
  "updated_at": "2013-06-05T17:40:32-04:00",
  "user_id": "51af47a8ef75ac5e8c000001"
}
```

-
### POST /v1/sites/:id/pages.json

Creates a page on the given site.

#### Params
* **title**  — Page title
* **body** *(optional)* — Page body
* **custom_slug** *(optional)* — Page custom slug
* **published_at** *(optional)* — Page published date
* **visibility** *(optional)* — Page visibility (`draft`, `hidden`, `visible`)
* **parent_id** *(optional)* — Page parent ID
* **meta** *(optional)* — Array of Page metadata
* **asset_ids** *(optional)* — Array of existing Asset IDs


#### Response
```json
{
  "id": "51afb050ef75acb2e8000003",
  "title": "My Site",
  "domain": "mysite.com",
  "cname": "abcdefghijklmnopqrst-abcdefghijklmnopqrstuvwxyz123456.a1.abc.rackcdn.com",
  "timezone": "Eastern Time (US & Canada)",
  "created_at": "2013-06-05T17:40:32-04:00",
  "updated_at": "2013-06-05T17:40:32-04:00",
  "user_id": "51af47a8ef75ac5e8c000001"
}
```

-
### PUT /v1/sites/:id/pages.json

Repositions pages on the given site.

#### Params
* **ids**  — Nested JSON array of Page IDs and their children


#### Request

```shell
curl -u API_KEY:API_SECRET \
  -X PUT \
  -d 'ids=[{"id":"51a38..."},{"id":"51a15...","children":[{"id":"51a39..."},{"id":"51a40..."}]}]' \
  https://api.siteleaf.com/v1/sites/51a158a8ef75ac1ada000001/pages
```

#### Response
```json
[
 {
   "id": "51afb050ef75acb2e8000006",
   "title": "My Page",
   "slug": "my-page",
   "url": "/pages/my-page",
   "body": "This is *my* page",
   "visibility": "draft",
   "created_at": "2013-06-05T17:40:32-04:00",
   "updated_at": "2013-06-05T17:40:32-04:00",
   "published_at": "2013-06-05T21:40:32Z",
   "user_id": "51af47a8ef75ac5e8c000001",
   "site_id": "51af47c1ef75acd940000002",
   "parent_id": "51a39a57ef75ac7634000005"
 }
]
```

-
### GET /v1/sites/:id/posts.json

Returns an array of all posts for the given site.

#### Params
* **include** *(optional)* — Array of entities to include (`user`, `site`, `parent`, `assets`, `meta`, `taxonomy`)


#### Response
```json
[
 {
   "id": "51afb050ef75acb2e8000008",
   "title": "My Page",
   "slug": "my-page",
   "url": "/pages/my-page",
   "body": "This is *my* page",
   "visibility": "draft",
   "created_at": "2013-06-05T17:40:32-04:00",
   "updated_at": "2013-06-05T17:40:32-04:00",
   "published_at": "2013-06-05T21:40:32Z",
   "user_id": "51af47a8ef75ac5e8c000001",
   "site_id": "51af47c1ef75acd940000002",
   "parent_id": "51a39a57ef75ac7634000005"
 }
]
```

-
### GET /v1/sites/:id/assets.json

Returns an array of all assets for the given site.

#### Response
```json
[
 {
   "id": "51afb050ef75acb2e800000a",
   "filename": "my-file.gif",
   "url": "/my-page/my-file.gif",
   "file": "51a39a57ef75ac7634000010.gif",
   "content_type": "image/gif",
   "filesize": 23856,
   "checksum": "9187a6775bdce8f1f2143accea89ba6c",
   "created_at": "2013-06-05T17:40:32-04:00",
   "updated_at": "2013-06-05T17:40:32-04:00"
 }
]
```

-
