# E-Commerce API Automation

A Postman-based API automation project for testing the [DummyJSON](https://dummyjson.com/) E-Commerce API. The collection contains automated API tests for authentication and user management and can be executed both in Postman and from the command line using Newman.

## Project Overview

This project demonstrates API automation using:

- Postman
- Newman
- JavaScript-based Postman test scripts
- Environment variables
- Automated assertions
- HTML test reporting
- Git and GitHub

The goal is to validate important E-Commerce API functionality through automated API requests and assertions.

## API Used

**DummyJSON API**

Base URL:

```text
https://dummyjson.com
```

## Test Coverage

### Authentication

#### Login - Valid User

**Method:** `POST`

**Endpoint:**

```text
/user/login
```

Validates:

- HTTP status code is `200`
- Access token is present
- Username is correct

#### Get Current User

**Method:** `GET`

**Endpoint:**

```text
/user/me
```

Validates:

- HTTP status code is `200`
- User ID is present
- Username is `Emily`

### Users

#### Get All Users

**Method:** `GET`

**Endpoint:**

```text
/users
```

Validates:

- HTTP status code is `200`
- Users array is present
- Users list is not empty
- First user has an ID
- First user has a username

#### Get User By ID - User 1

**Method:** `GET`

**Endpoint:**

```text
/users/1
```

Validates:

- HTTP status code is `200`
- Returned user ID matches test data
- User has a valid email

#### Get User By ID - User 2

**Method:** `GET`

**Endpoint:**

```text
/users/2
```

Validates:

- HTTP status code is `200`
- Returned user ID matches test data
- User has a valid email

## Test Results

The current Newman execution contains:

| Metric | Result |
|---|---:|
| Iterations | 1 |
| Requests | 5 |
| Failed Requests | 0 |
| Test Scripts | 10 |
| Failed Test Scripts | 0 |
| Assertions | 19 |
| Failed Assertions | 0 |

### Result

**19 / 19 assertions passed — 0 failures**

## Project Structure

```text
E-Commerce-API-Automation/
│
├── Collections/
│   └── E-Commerce-API-Automation.postman_collection.json
│
├── Environments/
│   └── E-Commerce-QA.postman_environment.json
│
├── Reports/
│   └── E-Commerce-API-Report.html
│
├── Screenshots/
│   ├── Screenshot (110).png
│   ├── Screenshot (111).png
│   └── Screenshot (112).png
│
├── .gitignore
└── README.md
```

## Prerequisites

Install the following before running the project:

- Node.js
- npm
- Newman

Verify the installations:

```bash
node --version
npm --version
newman --version
```

## Running the Collection with Newman

### Using the exported environment

The collection can be executed using the exported Postman environment:

```cmd
newman run "Collections\E-Commerce-API-Automation.postman_collection.json" -e "Environments\E-Commerce-QA.postman_environment.json"
```

If the exported environment does not contain the `baseUrl` value, it can be supplied directly from the command line:

```cmd
newman run "Collections\E-Commerce-API-Automation.postman_collection.json" -e "Environments\E-Commerce-QA.postman_environment.json" --env-var "baseUrl=https://dummyjson.com"
```

## Generating the HTML Report

The project uses the Newman HTML Extra reporter.

Install it if necessary:

```cmd
npm install -g newman-reporter-htmlextra
```

Create the reports directory:

```cmd
mkdir Reports
```

Run the collection and generate the report:

```cmd
newman run "Collections\E-Commerce-API-Automation.postman_collection.json" -e "Environments\E-Commerce-QA.postman_environment.json" --env-var "baseUrl=https://dummyjson.com" -r htmlextra --reporter-htmlextra-export "Reports\E-Commerce-API-Report.html"
```

The generated report is available at:

```text
Reports\E-Commerce-API-Report.html
```

## Environment Variables

The project uses Postman environment variables such as:

| Variable | Purpose |
|---|---|
| `baseUrl` | API base URL |
| `token` | Authentication token |
| `userId` | Current user ID |
| `productId` | Product ID |
| `createdProductId` | Created product ID |
| `cartId` | Cart ID |
| `createdCartId` | Created cart ID |

The API base URL used for this project is:

```text
https://dummyjson.com
```

> **Security:** Never commit real passwords, API keys, access tokens, or other sensitive credentials to GitHub. Use environment variables or a local environment file for sensitive values.

## Screenshots

Screenshots demonstrating the Postman collection, test execution, and Newman results are available in the `Screenshots` folder.

## Newman Execution Example

Successful execution:

```text
E-Commerce API Automation

POST https://dummyjson.com/user/login [200 OK]
GET  https://dummyjson.com/user/me [200 OK]
GET  https://dummyjson.com/users [200 OK]
GET  https://dummyjson.com/users/1 [200 OK]
GET  https://dummyjson.com/users/2 [200 OK]

Requests:       5
Failed:         0

Assertions:     19
Failed:         0
```

## Tools & Technologies

- **Postman** — API development and testing
- **Newman** — Command-line collection execution
- **JavaScript** — Postman test and pre-request scripts
- **DummyJSON** — Test API
- **Git** — Version control
- **GitHub** — Source code repository

## Author

**Arjun Sethu**

GitHub:

[https://github.com/arjunsethu604](https://github.com/arjunsethu604)