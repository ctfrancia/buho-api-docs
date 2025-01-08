+++
date = '2025-01-08T12:45:16+01:00'
draft = true
title = 'Authentication'
weight = 2 # Order that this section will appear in.
+++

# Authentication
This section will define everything you need to know about authentication within the Búho API.

## How to Create a Consumer
A "Comsumer" is the person that is using the API. This terminanology is used to differentiate a "user".

A user is someone that is using the front end of the application.

A consumer is someone that is using the API. e.g. a consumer is you, that is reading this documentation and consuming the API to server to your users.

### Request
> Example Request:
```json
{
    "first_name": "foo",
    "last_name": "bar",
    "email": "f@f.com",
    "website": "foo.com"
}
```
**Method**: `POST`

**Endpoint**: `/v1/auth/new/consumer`

**Fields**:
- `first_name` (string) - the first name of the consumer
- `last_name` (string) - the last name of the consumer
- `email` (string) - the email of the consumer
- `website` (string) - the website of the consumer

`website` is important as this will be used for your uploads and resources

### Response
> Example Response
```json
{
    "consumer": {
        "ID": 11,
        "CreatedAt": "2025-01-08T13:49:30.210429+01:00",
        "UpdatedAt": "2025-01-08T13:49:30.210429+01:00",
        "DeletedAt": null,
        "first_name": "foo",
        "last_name": "bar",
        "email": "f@f.com",
        "password": "0M;<Vb2+|fUhU+CW",
        "website": "foo.com"
    }
}
```
**Status Code**: `201`

**Fields**:
- `ID` (int) - the ID of the consumer
- `CreatedAt` (string) - the time the consumer was created
- `UpdatedAt` (string) - the time the consumer was updated
- `DeletedAt` (string) - the time the consumer was deleted
- `first_name` (string) - the first name of the consumer
- `last_name` (string) - the last name of the consumer
- `email` (string) - the email of the consumer
- `password` (string) - the password of the consumer
- `website` (string) - the website of the consumer

the `password` field is the password that you will use to authenticate with the API.

this password is what you will send in for the next stage of authentication, which is to get a token.
you can see how this password is generated [here](https://github.com/ctfrancia/buho/blob/37b2b685f875135b224f897591d0a26f3862d6df/internal/auth/auth.go#L86)

## How to Authenticate
Once you have created a consumer you can now authenticate with the API and get a token used for future requests.

### Request

> Example Request:
```json
{
    "email": "",
    "password": ""
}
```

**Method**: `POST`

**Endpoint**: `/v1/auth/login`

**NOTE**: The password is the password that was generated when you created the consumer.

**Fields**:
- `email` (string) - the email of the consumer
- `password` (string) - the password of the consumer

### Response
> Example Response
```json
{
    "token": "your_token_here"
}
```

**Status Code**: `200`

**Fields**:
- `token` (string) - the token that you will use for future requests

