# SwiftRide Mobility Platform

A coursework prototype built by SaiVatsal with Node.js, Express, and a browser interface. This repository is one of a series of domain-specific CRUD demonstrations.

## What is implemented

- List, search, create, update, and delete records through an Express API.
- A browser interface served from `public/`.
- Seed data and local JSON-file storage in `data/db.json`.
- Demonstration login and role-selection endpoints.

## Run locally

Install Node.js and npm, then:

```bash
git clone https://github.com/SaiVatsal/31-ride-sharing-app.git
cd 31-ride-sharing-app
npm install
npm start
```

Open [localhost:3000](http://localhost:3000). Set the `PORT` environment variable to use another port.

## Test

```bash
npm test
```

The smoke tests start a local server on an available port and use a temporary copy of the seed data. They check health, the demo authentication response, and a create/read/update/delete cycle. A failed assertion exits with a nonzero status. Passing these checks does not establish complete coverage or production readiness.

## API routes

| Method | Route |
| --- | --- |
| GET | `/api/health` |
| GET | `/api/stats` |
| GET | `/api/rides` |
| GET | `/api/rides/:id` |
| POST | `/api/rides` |
| PUT | `/api/rides/:id` |
| DELETE | `/api/rides/:id` |
| GET | `/api/activityRecords` |
| POST | `/api/activityRecords` |
| POST | `/api/auth/login` |
| GET | `/api/auth/me` |
| GET | `/api/auth/users` |
| POST | `/api/auth/logout` |

## Project files

| File | Purpose |
| --- | --- |
| `server.js` | Express routes and JSON storage |
| `public/index.html` | Browser interface |
| `data/db.json` | Local seed data |
| `api/index.js` | Serverless entry point |
| `vercel.json` | Deployment configuration |
| `test.js` | API smoke tests |

## Prototype limitations

- **Authentication is simulated.** The login endpoint does not validate a password; its token is a prefixed Base64 payload, not a signed JWT. The displayed roles do not enforce API authorization.
- Request bodies are merged into records without a complete validation schema.
- Local JSON storage does not provide transactions or safe concurrent writes. On Vercel, writes use temporary `/tmp` storage and are not durable.
- A domain-themed interface is not evidence of an integrated payment provider, delivery service, external database, or other live service.
- Use synthetic data for demonstrations. Real deployments need authentication, authorization, validation, durable storage, and additional testing.

