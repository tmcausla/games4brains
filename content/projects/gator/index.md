# Gator RSS Feed Ingestion

[< Back Home](/)

Gator is a command-line RSS feed aggregator built with Go and PostgreSQL. It allows users to register accounts, subscribe to RSS feeds, periodically collect articles, and browse aggregated content from their followed feeds.

The project provided an opportunity to work with Go's concurrency features, external data sources, and relational database management.

You can [view the source on GitHub](https://github.com/tmcausla/gatoraggregator).

## Tech Stack

- Go
- PostgreSQL
- sqlc
- Goose
- RSS / XML
- HTTP

## How It Works

Gator periodically retrieves content from registered RSS feeds and stores new posts in a PostgreSQL database.

Users can register accounts, add feeds to the aggregator, and subscribe to feeds added by other users. A background aggregation process continuously retrieves posts from these feeds at a configurable interval.

The aggregation process follows a straightforward workflow:

1. Retrieve registered RSS feeds from the database.
2. Make HTTP requests to fetch their latest content.
3. Parse the XML responses into structured Go data.
4. Validate and process the retrieved posts.
5. Store new posts in PostgreSQL, avoiding duplicate entries.

Users can then browse recently collected posts from the feeds they follow.

## Database Design

Gator uses PostgreSQL to manage users, RSS feeds, subscriptions, and collected posts.

The database is organized around three primary relationships:

- **Users and Feeds:** Users can follow multiple feeds, and individual feeds can be followed by multiple users. This many-to-many relationship is managed through a junction table.
- **Feeds and Posts:** Each feed can contain multiple posts, with every post associated with its originating feed.
- **Users and Subscriptions:** Users can manage their own feed subscriptions independently of other users.

Database migrations are managed with Goose, while sqlc generates type-safe Go code from SQL queries.

## Key Features

- **Multi-user support:** Users can register accounts and maintain independent feed subscriptions.
- **Feed management:** Add RSS feeds, follow existing feeds, and manage subscriptions.
- **Automated aggregation:** Continuously retrieve content from registered feeds at a configurable interval.
- **XML parsing:** Process RSS responses and convert external content into structured data.
- **Persistent storage:** Store feeds and posts in PostgreSQL, preventing duplicate entries.
- **Post browsing:** Retrieve recently collected posts from feeds followed by the current user.

## What I Learned

Gator gave me practical experience building a backend application that consumes and processes data from external sources.

Some of the concepts I explored include:

- Making HTTP requests and working with external APIs.
- Parsing XML and handling inconsistent external data.
- Using Go's concurrency features to manage background processing.
- Designing relational database schemas and many-to-many relationships.
- Generating type-safe database access code with sqlc.
- Managing database schema changes through migrations.

This project was an important step in developing my backend skills, particularly in working with external data sources and building applications that process information asynchronously.

[< Back Home](/)
