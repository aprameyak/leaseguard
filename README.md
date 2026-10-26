# Lease Guard

A simple lease checker for renters. Paste or describe your lease terms and the app flags a couple of common fees worth questioning before you sign.

## Features

- Record a lease with landlord or property name, monthly rent, location, and the lease terms as text
- Keyword checks flag "admin fee" and "renewal fee" in the terms
- Flags for each lease are stored and can be fetched by lease ID
- Entries are saved to a local JSON file

## Getting started

Requires Node.js.

```bash
npm install
npm start
```

Then open http://localhost:3005. `npm run dev` runs the same command.

## How it works

- `index.html` contains the lease form and the list of saved leases. It calls the API at `http://localhost:3005`.
- `server.js` is an Express app that serves the page and exposes:
  - `POST /api/leases` to save a lease, run the keyword checks, and return any flags.
  - `GET /api/leases` to list all leases.
  - `GET /api/leases/:id` to return one lease and its flags.
- The checks are plain, case-sensitive substring matches in `server.js`; there is no AI or legal analysis.
- Data is written to `data.json`, created on first run and ignored by git. `utils.js` holds helpers not yet wired in.

## Status

Prototype. Only two keyword rules exist, and the list view shows a generic warning on every lease rather than the specific flags.

## License

MIT, see [LICENSE](LICENSE).
