# Reel Time

[< Back Home](/)

_Every film has its place in time._

I built Reel Time to make it easier to compare the release histories of different movie franchises on a shared timeline.

My girlfriend and I were watching through the Halloween franchise before moving on to Friday the 13th. We started wondering how the two franchises' release histories compared, and looking up individual movies was becoming tedious. That gave me the idea for Reel Time.

The application lets users select two movie franchises and explore their release chronology side by side, including crossover films that belong to both franchises.

You can [view the source on GitHub](https://github.com/tmcausla/reel-time).

![Reel Time screenshot](/images/reeltime-image2.png)

![Reel Time screenshot](/images/reeltime-image1.png)


## Tech Stack

- Go
- JavaScript
- PostgreSQL
- HTML / CSS
- Git / GitHub

## How It Works

Reel Time uses a Go backend to serve both the frontend and the API endpoints responsible for retrieving movie and franchise data.

The frontend provides two franchise selectors and a shared timeline that displays the selected movies in chronological order.

The application follows a straightforward request cycle:

1. The user selects two movie franchises.
2. The frontend requests the associated movie data from the Go API.
3. The backend queries PostgreSQL for matching movies.
4. The API returns the results, including each movie's associated franchises.
5. The frontend renders the movies on the shared timeline.

This separation keeps the frontend responsible for presentation while the backend handles data retrieval and database interaction.

## Database Design

One of the more interesting aspects of this project was designing the database to accommodate crossover films.

Movies and franchises have a many-to-many relationship: a franchise contains multiple movies, and a movie can belong to multiple franchises.

Rather than duplicating crossover films, Reel Time uses a junction table (**movie_franchises**) to associate movies with every franchise they belong to.

This allows the API to retrieve movies across multiple franchise selections without introducing duplicate records.

## API

The Go backend exposes two primary endpoints:

```
Method   Endpoint                        Description
 GET     /api/franchises                 Retrieves available movie franchises
 GET     /api/movies?franchises=Alien    Retrieves movies associated with a selected franchise
```

The movies endpoint accepts multiple `franchises` query parameters, allowing the frontend to retrieve movies belonging to either selected franchise, including crossover films.

For example:

```
GET /api/movies?franchises=Alien&franchises=Predator
```

## What I Learned

Reel Time gave me an opportunity to move beyond command-line applications and build something with Go that people could interact with through a browser.

Some of the concepts I explored along the way include:

- Building a REST API with Go.
- Integrating PostgreSQL using **pgx**.
- Designing relational database schemas and many-to-many relationships.
- Separating frontend presentation from backend data access.
- Serving static frontend assets through a Go HTTP server.

More than anything, this project gave me the opportunity to take an idea from conception through database design, backend implementation, and frontend development.

[< Back Home](/)
