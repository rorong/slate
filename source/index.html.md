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

`POST https://engine.pirkx.com//api/v1/users/sign_in`

````json
{
  "email": "test@pirkx.com",
  "password": "Welcome@123"
}
````

### Query Parameters

Parameter | Type | Description
--------- | ------- | -----------
email | String | (required)
password | String | (required)

> JSON response format:

```json
// Example of success response
{
    "status": 200,
    "success": true,
    "message": "User sign in successfully",
    "user": {
        "id": 23,
        "email": "test@pirkx.com",
        "created_at": "2023-01-05T13:01:54.299Z",
        "updated_at": "2023-01-05T13:04:06.285Z",
        "invitation_token": null,
        "invitation_created_at": null,
        "invitation_sent_at": null,
        "invitation_accepted_at": "2023-01-05T13:04:06.279Z",
        "invitation_limit": null,
        "invited_by_type": "Patron",
        "invited_by_id": 20,
        "invitations_count": 0,
        "first_name": "test-1",
        "last_name": "admin",
        "phone_number": "1234567890",
        "company_id": null,
        "terms_agreed": false,
        "news_subscribed": false,
        "stripe_customer": null,
        "go_cardless_customer": null,
        "go_cardless_mandate": null,
        "auto_renew_subscription": true,
        "is_deleted": false,
        "deleted_at": null,
        "stripe_paid_amount": null,
        "stripe_paid_date": null,
        "stripe_charge_id": null,
        "unsubscribed_emails": false,
        "manual_billing": false,
        "go_cardless_mandate_status": 0,
        "go_cardless_failure_reason": null,
        "auth_token": null,
        "unique_token": null,
        "otp": null,
        "payment_intent_id": null,
        "in_app": false,
        "source_of_sign_up": 0,
        "connection_id": null,
        "sso_user_id": null,
        "sso_auth_token": null,
        "auth_token_updated_at": null,
        "app_sign_in_count": 0,
        "annual_subscription_agreement": false,
        "mandate_updated_at": null,
        "mandate_failed_count": 0,
        "forward_pay": false,
        "clicked_on_inviation_btn": false,
        "using_app": false,
        "device_type": null,
        "profile_pic": null,
        "kudos_on": true,
        "notification_enabled": true,
        "is_suspend": false,
        "gift_card_on": true,
        "go_cardless_scheme": 0,
        "parent_version_id": 3
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

`DELETE https://engine.pirkx.com/api/v1/users/sign_out`

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
  "status": 401,
  "success": false,
  "message": "User not found"
}
```

This endpoint allows patron to sign out.

# Patrons

## Invite Other Patron
### HTTP Request
> JSON request format:

`POST https://engine.pirkx.com/api/v1/users/invite`

````json
{
  "detail": {
    "auth_token": "eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
  },
 "account": "473995949136",
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
invitation[first_name] | String | Sets first name of patron
invitation[last_name] | String | Sets last name of patron
invitation[email] | String | Sets email of patron (required)
invitation[invitation_for] | String | Type of invitee (required)<br> Available options: 'master_admin', 'parent_admin'
invitation[phone_number] | Number | Sets phone number of patron
invitation[parent_version_id] | Number | Sets parent version for the parent_admin patron<br> (required if invitation_for parent_admin)

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
  "status": 400,
  "success": false,
  "message": "Invitee type is not correct for this user"
}
```

This endpoint allows patron to invite other users. <br>
(Currently MasterAdmin can invite either MasterAdmin or ParentAdmin)

## User Invitation Confirmation
### HTTP Request
> JSON request format:

`POST https://engine.pirkx.com/api/v1/users/confirmations`

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
user[email] | String | Email of patron (required)
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
  "status": 400,
  "success": false,
  "message": "Invalid verification token passed!"
}
```

This endpoint allows patron to confirm his account.
## User Forgot Password
### HTTP Request
> JSON request format:

`POST https://engine.pirkx.com/api/v1/users/passwords`

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
  "status": 401,
  "success": false,
  "message": "Email address not found."
}
```

This endpoint allows patron to send reset password mail.
## User Reset Password
### HTTP Request
> JSON request format:

`PATCH https://engine.pirkx.com/api/v1/users/passwords`

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

This endpoint allows patron to reset his password.

# Parent Versions
## Create Parent Versions
### HTTP Request
> JSON request format:

`POST https://engine.pirkx.com//api/v1/users/parent_versions`

````json
{
  "detail": {
    "auth_token": "eyJhbGciOiJSUzI1NiJ9.eyJkYXRhIjoiZVgwNWxobW12cVRZSVhsS1UtXzFXQSIsImV4cCI6MTY3Mjk3ODExMn0.fOD6xzxLfqEOPBGE4m4VV_C0z1ypudOS4sTgILVwiT-gfia9pBYWAsKo6DuiekMUDMLl8c5wHUk0i2Xpp76clR0WImE0hm7e1cr2f1eS9XbtCcudUqtTsjSPbSDWyh8VuQ3Sw7aZCoziT71WErZDd02hHQngdvehhE3jgoNag-JbnHrdQmhl76HdpMq3FLWqXVWwBLBtXANjMUPRl4FLLwD3_MdaZfCe55_nwGQqJdveFCoRmrBmJfkUpLGW45lebeZOsyx27O96ffIySUQK3kDvp3F0ncuYOgMjZ8ggEzUhggrlu3Coc2Eg_9byLEdIcERD-0hTI7Q74WcgNlLZjQ"
  },
   "account": "473995949136",
   "parent_version": {
     "parent_name": "UK",
     "country": "United Kingdom",
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
parent_version[country] | String | Sets country for the parent version (required)
parent_version[currency] | String | Sets currency for the parent version (required)
parent_version[tax_rate_in_percentage] | Decimal Number | Sets tax rate (in percentage) for the parent version (required)
parent_version[domain_extension] | String | Sets subdomain for the parent version (required) <br> Maximum - 10 characters, must not contain spaces
parent_version[parent_abbreviation] | String | Sets parent abbreviation for the parent version (required) <br> Maximum - 10 characters

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
  "status": 400,
  "success": false,
  "message": "Unauthorized"
}
```

This endpoint allows MasterAdmin to create parent versions.
