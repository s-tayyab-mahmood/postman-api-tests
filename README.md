# postman-api-tests

![Postman API Tests](https://github.com/YOUR_GITHUB_USERNAME/postman-api-tests/actions/workflows/newman.yml/badge.svg)

Postman collection for the [Swagger Petstore](https://petstore.swagger.io) API, run in CI with Newman.

## Folders

- **Store**: inventory endpoint
- **Pet lifecycle**: create, get, update, check the update saved, search by status, delete, check it's gone.
  These requests depend on each other, so run them in order.
- **Negative**: unknown ids, bad ids, broken JSON, unknown user
- **User**: create, log in, get, delete

Ids are generated in pre-request scripts and passed between requests as collection variables. There's also a
response time check at collection level, so it runs on every request.

`data/pets.csv` runs the pet lifecycle 5 times with different names (including one with an accent and one with
an apostrophe).

## Running

Postman: import the collection and the environment from `environments/`, then run the collection.

CLI:

```bash
npm install
npm test                  # full run, report in reports/report.html
npm run test:data-driven  # pet lifecycle with pets.csv
```

Petstore is a shared public server, so it can be slow or flaky. Re-run a failure before assuming it's a real bug.
