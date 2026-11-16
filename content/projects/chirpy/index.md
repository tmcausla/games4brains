# Chirpy Authentication

[< Back Home](/)

Chirpy is a RESTful API backend for a Twitter-inspired microblogging platform, built with Go and PostgreSQL. Users can register accounts, authenticate, publish short messages (chirps), and manage their content through a JSON API.

This project strengthened my understanding of backend security and the responsibilities involved in building APIs that handle user accounts and protected resources.

You can [view the source on GitHub](https://github.com/tmcausla/chirpy).

## Tech Stack

- Go
- PostgreSQL
- sqlc
- Goose
- JWT
- Argon2id
- HTTP / JSON

## How It Works

Chirpy exposes a REST API that handles user registration, authentication, and chirp management.

Users register with an email address and password. Passwords are hashed using Argon2id before being stored, and successful authentication provides the client with access and refresh tokens.

Protected endpoints require valid authentication credentials. The server validates incoming tokens and uses the authenticated user's identity to determine whether they are authorized to perform a requested action.

The application supports several core workflows:

- **User registration:** Create accounts with securely hashed passwords.
- **Authentication:** Verify credentials and issue JWT access and refresh tokens.
- **Token management:** Refresh expired access tokens and revoke refresh tokens.
- **Chirp management:** Create, retrieve, and delete short messages.
- **User management:** Update account information through authenticated requests.
- **Premium membership:** Process authenticated webhook events to upgrade users to Chirpy Red.

## Authentication and Security

Authentication and authorization are central to Chirpy's design.

The application uses JWTs to manage authenticated sessions, with separate access and refresh tokens serving different purposes.

- **Access tokens:** Short-lived tokens used to authenticate requests to protected endpoints.
- **Refresh tokens:** Longer-lived tokens used to obtain new access tokens without requiring users to log in again.
- **Token revocation:** Refresh tokens can be revoked, preventing them from being used to obtain new access tokens.

Passwords are hashed using Argon2id rather than stored in plaintext.

Authorization checks ensure that authenticated users can only perform permitted operations. For example, users cannot delete chirps belonging to another account.

## Database Design

Chirpy uses PostgreSQL for persistent storage, with Goose managing schema migrations and sqlc generating type-safe Go code from SQL queries.

The database is organized around three primary entities:

- **Users:** Registered accounts containing user information and hashed passwords.
- **Chirps:** Short messages associated with their authors.
- **Refresh Tokens:** Authentication tokens associated with individual users, including their expiration and revocation status.

Users have a one-to-many relationship with both chirps and refresh tokens. Each user can create multiple chirps and maintain multiple refresh tokens.

## Key Features

- **Secure password storage:** Passwords are hashed using Argon2id.
- **JWT authentication:** Access and refresh tokens manage authenticated sessions.
- **Token revocation:** Refresh tokens can be invalidated.
- **Authorization:** Ownership checks prevent users from modifying other users' content.
- **Input validation:** Chirps are limited to 140 characters and undergo profanity filtering.
- **Webhook integration:** Authenticated Polka webhook events support Chirpy Red membership upgrades.
- **HTTP middleware:** Request handling includes logging and server metrics.

## What I Learned

Chirpy gave me practical experience implementing authentication and authorization in a Go application.

Some of the concepts I explored include:

- Designing RESTful APIs and handling HTTP requests.
- Implementing JWT authentication and token lifecycles.
- Secure password hashing with Argon2id.
- Separating authentication from authorization.
- Implementing middleware for shared request-handling functionality.
- Integrating external services through authenticated webhooks.
- Managing relational data with PostgreSQL and sqlc.

[< Back Home](/)
