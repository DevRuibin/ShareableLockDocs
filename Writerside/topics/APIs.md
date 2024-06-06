# API Documentation

## Overview

This document provides a detailed description of the APIs used by the mobile app and within the microservices. For security reasons, all requests must include a **token** in the **header**. A request is approved if the token is valid and the request only modifies data that belongs to the user who sends the request. For example, a user can change their own profile information but not that of other users. Fine-grained control is specified in each API description.
To see the API in more detail, check the [page](APIs-in-OpenAPI.md)

## Main Services API

### User API

#### POST /users
**Description:** Create a new user.

#### POST /users/login
**Description:** Login a user.

#### GET /users/:id
**Description:** Retrieve user information.

#### PATCH /users/:id
**Description:** Update user information.
- Change the profile picture
- Change the password
- Change the email
- Change the username

#### DELETE /users/:id
**Description:** Delete a user.
> **Warning:** To be implemented in the future, as it affects many logic processes.

### Notification API (Message API)

#### POST /messages
**Description:** Send a message to a user.

#### PATCH /messages/:id
**Description:** Mark a message as read.

#### DELETE /messages/:id
**Description:** Delete a message.

#### GET /messages/:userId
**Description:** Get all messages of a user.

### Lock API

#### POST /locks
**Description:** Create a lock.

#### GET /locks/:userId
**Description:** Get all locks of a user, either the user is the owner or the lock is shared with the user.

#### GET /locks/:id
**Description:** Get detailed lock information.

#### PATCH /locks/:id
**Description:** Update lock information.
- Change the name
- Change the picture
- Change the lock/unlock status (only used between the microservices, not for the user)
- Change the battery status (only used between the microservices, not for the user)
- Change the location (only used between the microservices, not for the user)
- Change the shared users
    - Add a user
    - Remove a user
- Change the GPS report interval (only the owner can change this)

#### DELETE /locks/:id
**Description:** Delete a lock (only the owner can delete the lock).

### Static File API

#### POST /files/upload
**Description:** Upload a file.

#### POST /files/upload-secrets
**Description:** Only used between the microservices, not for the user. It can control the file name.

#### GET /files/:filename
**Description:** Retrieve a file.

## API for Microservices Only

### Log API

#### POST /logs
**Description:** Create a log message.

### Auth API

**Description:** This API is responsible for authentication and authorization.

#### POST /auth/authorize
**Description:** Authorize a user based on the URL, request method, token, and request body.
> **Note:** The request body is considered because, for example, if the user wants to change lock information, it must be checked if the lock belongs to the user, which is included in the request body.

#### POST /auth
**Description:** Assign a token to a user.