# Postman Newman CI/CD Contact API Automation

Portfolio-ready API test automation project using Postman, Newman, and GitHub Actions for a Contact List REST API.

## Project Highlights

- Postman collection covering `Add Contact` and `Get Contact List`
- Local and CI execution with `npm test`
- Automatic token setup and test data cleanup
- Newman CLI reporting

## Project Structure

```text
.
├── .github/workflows/postman-tests.yml
├── environments/local.postman_environment.json
├── tests/ContactList1.json
├── .env.example
├── .gitignore
├── package-lock.json
├── package.json
└── README.md
```

## Local Setup

Install dependencies:

```bash
npm install
```

Run the API tests:

```bash
npm test
```

## How The Test Runs

The collection keeps two visible portfolio scenarios:

1. `Add Contact` validates contact creation, response status, generated email, and response time.
2. `Get Contact List` validates retrieval and confirms the created contact appears in the list.

The collection creates a temporary user for authentication during the run, then cleans up the created contact and user afterward.

```text
Create temporary user
        ↓
Store bearer token
        ↓
Add contact
        ↓
Get contact list
        ↓
Verify created contact
        ↓
Clean up contact and user
```

## CI

GitHub Actions runs the same command used locally:

```bash
npm test
```

The workflow installs dependencies with `npm ci` and runs the Newman collection. No GitHub secret token is required because the collection generates its own bearer token during the run.

## Latest Validation

Verified with:

```bash
npm ci
npm test
```

```text
Requests: 5
Assertions: 5
Failures: 0
```

## Author

Created by May Ann Besina

QA Automation Engineer focused on API Testing, CI/CD Automation, Playwright, Cypress, and Quality Engineering Practices.
