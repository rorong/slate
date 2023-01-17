---
title: Pirkx Engine API Reference

language_tabs: # must be one of https://git.io/vQNgJ

toc_footers:
  - Documentation Powered by Pirkx

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Pirkx Engine API
---

# Introduction

Welcome to the Pirkx Engine API! You can use our API to access our API endpoints for user authentication, sending invitation to other users, creating parent versions and many more to come.

You can view request/response examples in the dark area to the right.

We give you the benefits and services to improve your health and happiness.

<aside class="success">AFFORDABLE WELLBEING BENEFITS – IMPROVING HEALTH, WEALTH AND HAPPINESS</aside>

# Authentication
## User Sign-in
### HTTP Request
> JSON request format:

`POST https://auth-app-lb-870023433.eu-west-2.elb.amazonaws.com/api/v1/users/sign_in`

````json
{
  "email": "test@pirkx.com",
  "password": "Welcome@123",
  "remember_me": true
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
email | String | (required)
password | String | (required)
remember_me | String/Boolean | values in true, false (required)

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "User sign in successfully",
  "user": {
    "data": {
          "id": "23",
          "type": "patron",
          "attributes": {
              "email": "test@pirkx.com",
              "first_name": "test-1",
              "last_name": "admin",
              "type": "MasterAdmin"
          }
      }
  },
  "services": {
      "global_admin": [
          "create_service",
          "create_feature"
      ]
  },
  "token": "eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoqWlU2dGJ2M1RSWThDNWRXJUQSIsImV4cCI6MTY3MjkyNzQ5OH0.iia28wdprwj-ow0_qoR5GMRGeUkyg-ca6GKzMNXdswehgW2iBYfCLRQU5ll5i9A_qfGsWWXudMROCRMjP-fSzuoy6Nu_G4b0YOyybzHBV3wgUdUJxU5XAiwJoxeYbJmJda_604mSKMs-2XomPt_n6Qo8frqKUYWQvi4b0C9iLJBO_ZxkrZDQSdUME4D0tiQ7kMNJX6j7bpJd7QcZ0iN1wtVPzWVtomsyrrFIVrlFkb2CRGod-ogmYc7oIOK7Zk1xJhC4OWMyKvUA0hAYeMND8n5h3Rl8NPxpjGeyKv0KKx04IfvIq41pYMbhAQB4tG-_oSsOnsh7Sgabzz1FUyt5MbZ7Vbdw",
  "cognito_id_token": "eyJraWQiOiIzRnlnXC9iRm1MNGE1RDdiRjluTzZQY2NEME1DU3czZVNGUElmSW5xbWN1ND0iLCJhbGciOiJSUzI1NiJ9.QyOGUtYWI0OS02ZTE4MmRiZjZlMmIiLCJpc3MiOiJodHRwczpcL1wvY29nbml0by1pZHAuZXUtd2VzdC0yLmFtYXpvbmF3cy5jb21ScL2V1LXdlc3QtMl9pbmxaREZ2UU0iLCJjb2duaXRvOnVzZXJuYW1lIj2oicGFyZW50X2FkbWluX3Rlc3RfMUB5b3BtYWlsLmNvsdbSIsIm9yaWdpbl9qdGkfgiOiI0NzQ1OWVhZC05NjA1LTRkY2EtYjFjMi01MzJjZTQxYjAzOTMiLCJhdWQiOiIxZnZxbm5ka3VzYmdhNWV0YWRlamFpMWxtdCIsImV2ZW50X2lkIjoiZDc0NGNhMj_QtZTJjNy00YmIwLWFiMzctYzBjMTIwNzIwMGY4IiwidG9rZW5fdXNlIjoyhiaWQiLCJhdXRoX3RpbWUiOjE2NzI5MjM4OTgsImV4cCI6MTY3MjkyNzQ5OCwiaWF0IjoxNjcyOTIzODk4LCJqdGkiOiJkZWE5MDA5Mi02ZWRlLTQ4MjctYTg2Ny05MDJhMDIzMmRkYTgiLCJlbWFpbCI6InBhcmVudF9hZG1pbl90ZXN0XzFAeW93wbWFpbC5jb20ifQ.kOhN7HIfQ0NA694zhgYq9oKCu-toC8JrsKdhrrzXBI5RBKwni2dgv9NaaOLrOoPkbAAC07KPtKRlrXV_MOh1_Zxv0gur2XYaCA_YXAxUrylSJIAl19BUYnkuJr1atC1aV3Eube_ED78xbiVkj6qn00ssoY6XGGm_CdMbATX5XTyPrj-eZX9EbXvydtjjLZlwQsuAZnSQtiuG8j42vGG7nTCLKT_svwtASM3f1CzloBIzRnUhyOhRgnIEA5bzv52wQUkvye5r_Zic7hJCZvOqhjyOaV29AimjkeIW7namdMfdjG1BdktLBObiqsJgvSNYxVTNW6VVZddZVuuRWNWbQd7dQ"
}

// Example of failure response
{
  "status": 400,
  "success": false,
  "message": "Incorrect username or password."
}

```

This endpoint allows patron to sign in.

## User Sign out
### HTTP Request
> JSON request format:

`DELETE https://auth-app-lb-870023433.eu-west-2.elb.amazonaws.com/api/v1/users/sign_out`

````json
{
  "token": "eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiM0hBZnFWQjgxU1RjQlVLemVjWlUydyIsImV4cCI6MTY3MjkyNDU5Nn0.C0PfgKdBoMshZee_DNJsY2sO6TpHr-06-cK1CvVzyS-Lx2E6z0I2Ax20tmkz9SI4H_5nDvxNBLuWAb6xjkytobM_ulDlV5XsHtUSsuP3tKdQLnD0NMXw5JBUpshZnXULG03wjz_pTXUuNN4gEZdGcvh6jidJGR7UjRQSeKFxjcOodNhTgkqNUo8Qo9sWVefY4em3RCcJiWoyFQjfnhCC94HLsYO0jTP3WAEfCFYOQtKZ6YEpxT4nC9P69dFjwOQ0UDFroJOHvmM7QJDCUzHsYd7tpipGdu9_b1JqZPno31gutQu7Fa0GE1Kn117Z6d5YH_Aq4zqFihaAGeOwb3tXfA"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
token | String | unique token of user (required)

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "User signout successfully"
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "User not found"
}
```

This endpoint allows patron to sign out.


# Patrons
## Show All Patrons
### HTTP Request
> JSON request format:

`GET https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
- | - | -

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Success",
  "data": [
    {
      "id": "1",
      "type": "patrons",
      "attributes": {
          "id": 1,
          "email": "master1@gmail.com",
          "last_sign_in_at": null,
          "sign_in_count": 0,
          "status": "waiting",
          "name": "Master admin",
          "access_level": "Super Admin"
      }
    },
    {
      "id": "2",
      "type": "patrons",
      "attributes": {
          "id": 2,
          "email": "parent1@gmail.com",
          "last_sign_in_at": null,
          "sign_in_count": 0,
          "status": "waiting",
          "name": "Parent-admin-uk",
          "access_level": "Country gb"
      }
    },
    {
      "id": "3",
      "type": "patrons",
      "attributes": {
          "id": 3,
          "email": "parent2@gmail.com",
          "last_sign_in_at": null,
          "sign_in_count": 0,
          "status": "waiting",
          "name": "Parent-admin-uk",
          "access_level": "Country gb"
      }
    }
  ]
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No admin found. Please create a admin user."
}
```

This endpoint shows details of all admin users.

## Show Specific Patron
### HTTP Request
> JSON request format:

`GET https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/:id`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
- | - | -

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
"ex URL -> 'GET https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/2'"
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Success",
  "data": {
    "id": "2",
    "type": "patrons",
    "attributes": {
        "id": 2,
        "email": "parent_1@gmail.com",
        "last_sign_in_at": null,
        "sign_in_count": 0,
        "status": "waiting",
        "name": "parent-admin test",
        "access_level": "Country gb"
    }
  }
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No admin user found with id 2"
}
```

This endpoint shows details of the requested admin user.

## Update Specific Patron
### HTTP Request
> JSON request format:

`PUT https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/:id`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "patron": {
    "id": 2,
    "first_name": "new",
    "last_name": "admin",
    "phone_number": "",
  }
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
patron[id] | Number | Id of Patron to update
patron[first_name] | String | Sets first name for patron
patron[last_name] | String | Sets last name for patron
patron[phone_number] | Number | Sets phone number for patron

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
"ex URL -> 'PUT https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/2'"
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Success",
  "data": {
    "id": "2",
    "type": "patrons",
    "attributes": {
        "id": 2,
        "email": "parent_1@gmail.com",
        "last_sign_in_at": null,
        "sign_in_count": 0,
        "status": "waiting",
        "name": "new admin",
        "access_level": "Country gb"
    }
  }
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No admin user found with id 2"
}
```

This endpoint updates details of the specific admin user.

## Delete Specific Patron
### HTTP Request
> JSON request format:

`DELETE https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/:id`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
- | - | -

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
"ex URL -> 'DELETE https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/1'"
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Admin user deleted successfully"
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No admin user found with id 1"
}
```

This endpoint delete specific admin user.

## Delete Specific Patrons
### HTTP Request
> JSON request format:

`DELETE https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/destroy_all`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "ids": [
    100, 200
  ]
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
ids | Array | IDs of patrons that needs to be deleted

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Admin user deleted successfully"
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No admin user found with ids 100, 200"
}
```

This endpoint delete specific admin users.

## Block Specific Patrons
### HTTP Request
> JSON request format:

`PATCH https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/block`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "ids": [
    100, 200
  ],
  "blocked": true
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
ids | Array | IDs of patrons that needs to be deleted
blocked | String/Boolean | available options - true, false

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Admin users updated successfully"
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No admin user found with ids [100, 200]"
}
```

This endpoint block all specific admin users.

## Search Patrons
### HTTP Request
> JSON request format:

`POST https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/search`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "patron": {
    "query_string": "test",
    "page_no": 2
  }
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
patron[query_string] | String | Search string for patrons (searched in patron email and name)
patron[page_no] | Integer | Page number of the paginated serach results <br> (default - per page is 10)

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Success",
  "user": {
    "data": [
      {
        "id": "1",
        "type": "patrons",
        "attributes": {
          "id": 1,
          "email": "master_1@gmail.com",
          "last_sign_in_at": null,
          "sign_in_count": 0,
          "status": "waiting",
          "name": "master test",
          "access_level": "Super Admin"
        }
      },
      {
        "id": "3",
        "type": "patrons",
        "attributes": {
          "id": 3,
          "email": "parent_test1@gmail.com",
          "last_sign_in_at": null,
          "sign_in_count": 0,
          "status": "waiting",
          "name": "parent admin",
          "access_level": "Country gb"
        }
      }
    ]
  }
}

// Example of failure response
{
  "status": 400,
  "success": false,
  "message": "Search string two small. Search string minimum length 3 char."
}
```

This endpoint allows user to search admin users on the basis of a query string. <br>
The query string searches for the particular string in Patron name and email.

## Export Patrons
### HTTP Request
> JSON request format:

`POST https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/patrons/export`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "patron": {
    "export": {
      "export_ids": ""
    }
  }
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
export[export_ids] | String | Ids of admin patrons that needs to export <br> (ids are seperated by ,) ex: "100, 200"

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"


If no ids (ie, empty string "") are passed in :export_ids param, all admin users are exported.

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "CSV successfully exported",
  "download_url": "https://example.amazonaws.com/export_files/admin_users.csv?Faws4_request&X-Amz-Date=20230110T090431Z&X-Amz-Expires=1500&X-Amz-SignedHeaders=host&X-Amz-Signature=0095aaa4070120d00123ad0add9fb86a5525b3a23sabc8f868"
}

// Example of failure response
{
  "status": 400,
  "success": false,
  "message": "param is missing or the value is empty: export\nDid you mean?  export_all"
}
```

This endpoint allows user to export details of users. <br>
If export_ids does not contain ids, ie pass empty string "", it exports all patrons data.
If export_ids contain ids (muliple ids separated by comma), it exports patrons data of the specified patron ids.
If the ids mentioned does not exist, it shows error.

## Invite Other Patron
### HTTP Request
> JSON request format:

`POST https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/users/invite`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
 "invitation": {
    "first_name": "test",
    "last_name": "test",
    "email": "test.test@ongraph.com",
    "invitation_for": "parent_admin",
    "phone_number": 1234567890,
    "parent_version_id": 1
  }
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
invitation[first_name] | String | Sets first name of patron (required)
invitation[last_name] | String | Sets last name of patron (required)
invitation[email] | String | Sets email of patron (required)
invitation[invitation_for] | String | Type of invitee (required)<br> Available options: 'master_admin', 'parent_admin'
invitation[phone_number] | Number | Sets phone number of patron
invitation[parent_version_id] | Number | Sets parent version for the parent_admin patron<br> (required if invitation_for parent_admin)

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Invitation sent successfully"
}

// Example of failure response
{
  "status": 422,
  "success": false,
  "message": "Admin already exists with the given email"
}
```

This endpoint allows patron to invite other users. <br>
(Currently MasterAdmin can invite either MasterAdmin or ParentAdmin)

## User Invitation Confirmation
### HTTP Request
> JSON request format:

`POST https://auth-app-lb-870023433.eu-west-2.elb.amazonaws.com/api/v1/users/confirmations`

````json
{
  "user": {
    "first_name": "test",
    "last_name": "test",
    "password": "Welcome@123",
    "token": "7809ab05ce1566d115ed10f029dff2sd87a9c5cd274fgf12cccba49591d76d52"
  }
}

````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
user[first_name] | String | Sets first name of patron (required)
user[last_name] | String | Sets last name of patron (required)
user[password] | String | Sets password for patron(required)
user[token] | String | unique verification token of patron (required)

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "User verified successfully!"
}

// Example of failure response
{
  "status": 422,
  "success": false,
  "message": "Invalid token."
}
```

This endpoint allows patron to confirm his account.

## User Forgot Password
### HTTP Request
> JSON request format:

`POST https://auth-app-lb-870023433.eu-west-2.elb.amazonaws.com/api/v1/users/passwords`

````json
{
  "email": "test@pirkx.com"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
email | String | Email of patron (required)

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Password reset instructions sent."
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "User not found."
}
```

This endpoint allows patron to send reset password mail.

## User Reset Password (When User Sets His Password Via Forgot Password Mail)
### HTTP Request
> JSON request format:

`PATCH https://auth-app-lb-870023433.eu-west-2.elb.amazonaws.com/api/v1/users/passwords`

````json
{
  "password": "Welcome@123",
  "confirm_password": "Welcome@123",
  "reset_password_token": "tt6PxNhCv23C8hax6LxD"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
password | String | Sets new password for the patron (required)
confirm_password | String | Confirm password - should match with the value of password (required)
reset_password_token | String | Unique reset password token (required)

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Password successfully updated"
}

// Example of failure response
{
  "status": 400,
  "success": false,
  "message": "Link not valid or expired."
}
```

This endpoint allows patron to reset his password, when user is not logged in.

## User Reset Password (When Admin Sends Reset Password Mail For Other User)
### HTTP Request
> JSON request format:

`POST https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/users/reset_password`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "id": 1
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | Number | Id of the patron to whom reset password mail is to be sent (required)

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Password reset instructions sent."
}

// Example of failure response
{
  "status": 400,
  "success": false,
  "message": "User not found."
}
```

This endpoint allows admin to send reset password mail to other user.

# Parent Versions
## Create Parent Versions
### HTTP Request
> JSON request format:

`POST https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "parent_version": {
    "parent_name": "UK",
    "country_id": 1,
    "currency": "GRB",
    "tax_rate_in_percentage": 2.3,
    "domain_extension": "en-gb",
    "parent_abbreviation": "UK"
  }
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
parent_version[parent_name] | String | Sets parent name for the parent version (required) <br> Maximum - 20 characters
parent_version[country_id] | Number | Sets country id for the parent version (required)
parent_version[currency] | String | Sets currency for the parent version (required)
parent_version[tax_rate_in_percentage] | Decimal Number | Sets tax rate (in percentage) for the parent version (required)
parent_version[domain_extension] | String | Sets subdomain for the parent version (required) <br> Maximum - 10 characters, must not contain spaces
parent_version[parent_abbreviation] | String | Sets parent abbreviation for the parent version (required) <br> Maximum - 10 characters

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Parent Version created successfully"
}

// Example of failure response
{
  "status": 401,
  "success": false,
  "message": "Unauthorized"
}
```

This endpoint allows MasterAdmin to create parent versions.

## Get All Parent Versions
### HTTP Request
> JSON request format:

`GET https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
- | - | -

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Success",
  "data": [
    {
      "id": "1",
      "type": "parent_version",
      "attributes": {
          "id": 1,
          "parent_name": "United Kingdom",
          "tax_rate_in_percentage": "2.3",
          "currency": "GBP",
          "domain_extension": "en-gb",
          "parent_abbreviation": "UK",
          "country": "United Kingdom"
      }
    },
    {
      "id": "2",
      "type": "parent_version",
      "attributes": {
          "id": 2,
          "parent_name": "Australia",
          "tax_rate_in_percentage": "5.2",
          "currency": "AUD",
          "domain_extension": "aus",
          "parent_abbreviation": "AUS",
          "country": "Australia"
      }
    }
  ]
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No parent versions listed yet"
}
```

This endpoint shows the list of all parent versions.

## Get Specific Parent Version
### HTTP Request
> JSON request format:

`GET https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions/:id`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
- | - | -

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
"ex URL -> 'GET https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions/1'"

// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Success",
  "data": {
    "id": "1",
    "type": "parent_version",
    "attributes": {
        "id": 1,
        "parent_name": "United Kingdom",
        "tax_rate_in_percentage": "2.3",
        "currency": "GBP",
        "domain_extension": "en-gb",
        "parent_abbreviation": "UK",
        "country": "United Kingdom"
    }
  }
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No parent version listed with id 1"
}
```

This endpoint shows the details of the requested parent version.

## Update Specific Parent Version
### HTTP Request
> JSON request format:

`PUT https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions/:id`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "parent_version": {
    "parent_name": "United Kingdom",
    "tax_rate_in_percentage": 5.1,
    "domain_extension": "uk",
    "parent_abbreviation": "UK"
  }
}
````
### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
parent_version[parent_name] | String | Sets parent name for the Parent version (required)
parent_version[tax_rate_in_percentage] | Decimal Number | Sets tax rate (in percentage) for the parent version (required)
parent_version[domain_extension] | String | Sets subdomain for the parent version (required) <br> Maximum - 10 characters, must not contain spaces
parent_version[parent_abbreviation] | String | Sets parent abbreviation for the parent version (required) <br> Maximum - 10 characters

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
"ex URL -> 'PUT https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions/1'"

// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Success",
  "data": {
    "id": "1",
    "type": "parent_version",
    "attributes": {
        "id": 1,
        "parent_name": "United Kingdom",
        "tax_rate_in_percentage": "5.1",
        "currency": "GBP",
        "domain_extension": "uk",
        "parent_abbreviation": "UK",
        "country": "United Kingdom"
    }
  }
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No parent version listed with id 1"
}
```

This endpoint update the specific details of the requested parent version.

## Delete Specific Parent Version
### HTTP Request
> JSON request format:

`DELETE https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions/:id`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}
````
### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
- | - | -

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json
"ex URL -> 'DELETE https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions/1'"

// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Parent Version deleted successfully"
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No parent version listed with id 1"
}
```

This endpoint delete the requested parent version.

## Delete Specific Parent Versions
### HTTP Request
> JSON request format:

`DELETE https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/parent_versions/destroy_all`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}

"-> params"
{
  "ids": [
    100, 200
  ]
}
````
### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
ids | Array | Ids of parent versions

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json

// Example of success response
{
  "status": 200,
  "success": true,
  "message": "Parent Versions deleted successfully"
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No parent version listed with ids 100, 200"
}
```

This endpoint delete the requested parent versions.


# Country
## Show All Countries

### HTTP Request
> JSON request format:

`GET https://users-app-lb-68799060.eu-west-2.elb.amazonaws.com/api/v1/country`

````json
"-> auth token to be sent in headers"
{
  "HTTP_SERVICE_AUTHORIZATION": "Bearer eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
}
````
### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
- | - | -

### Query Headers

Header | Description
--------- | -----------
HTTP_SERVICE_AUTHORIZATION | value like -> "Bearer <i><b>auth_token</b></i>"

> JSON response format:

```json

// Example of success response
{
    "status": 200,
    "success": true,
    "message": "Success",
    "countries": {
        "data": [
            {
                "id": "1",
                "type": "country",
                "attributes": {
                    "id": 1,
                    "name": "United Kingdom",
                    "abbreviation": "GB"
                }
            },
            {
                "id": "2",
                "type": "country",
                "attributes": {
                    "id": 2,
                    "name": "Australia",
                    "abbreviation": "AUS"
                }
            }
        ]
    }
}

// Example of failure response
{
  "status": 404,
  "success": false,
  "message": "No countries listed yet"
}
```

This endpoint shows all country details.
