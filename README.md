# expressJSs

`expressJSs` is an Express.js application that serves static web pages and exposes a versioned Pokémon API backed by MongoDB.

The project demonstrates Express middleware, modular route files, static asset serving, REST-style endpoints, MongoDB connection setup, and ObjectId handling.

## Features

- Runs an Express server on port `3000`.
- Serves static files from the `public` directory.
- Mounts Pokémon API routes under `/api/v1/pokemon`.
- Includes separate static-page routes.
- Connects to MongoDB through a reusable database helper.
- Exposes MongoDB's `ObjectId` for route and database operations.

## Built With

- Node.js
- Express.js
- MongoDB Node.js driver
- JavaScript
- CommonJS modules

## Project Structure

```text
expressJSs/
├── app.js                 # Express application entry point
├── dbconnect.js           # MongoDB connection helper
├── routes/
│   ├── api/v1/pokemon/    # Pokémon API routes
│   └── static/            # Static-page routes
├── public/                # Browser-facing files
├── endpoints.rest         # Example API requests
├── package.json           # Project metadata and dependencies
└── package-lock.json
```

## Getting Started

### Prerequisites

- Node.js installed on your computer.
- npm, included with Node.js.
- A MongoDB connection string.

### Install Dependencies

```bash
npm install
```

### Configure MongoDB

The database helper expects MongoDB connection settings in a local secrets file referenced by `dbconnect.js`:

```text
secrets/mongodb.json
```

The file should contain a `uri` property. Do not commit database credentials or other secrets to the repository.

### Start the Server

```bash
node app.js
```

The application listens on port `3000`:

```text
http://localhost:3000/
```

## API

Pokémon endpoints are mounted under:

```text
/api/v1/pokemon
```

See `endpoints.rest` and the route files for the available operations and request formats.

## Database Connection

`dbconnect.js` creates a MongoDB client and provides a `getCollection` helper. The helper connects to the configured MongoDB instance and returns a collection for the requested database and collection names.

## Current Limitations

- MongoDB credentials must be configured locally before database-backed routes can work.
- No automated test suite is currently documented.
- Database connection lifecycle and error handling may need additional production hardening.
- API behavior depends on the route implementations and available MongoDB data.

## Security Notes

Keep `secrets/mongodb.json` out of source control. Use environment variables or a secrets manager for production deployments.

## License

No license has been specified for this repository yet.
