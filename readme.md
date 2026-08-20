# Bruno Mock Server Examples

A sample Bruno collection for learning and experimenting with **[Mock Servers in Bruno](https://docs.usebruno.com/mock-servers/overview)**.

This collection includes examples for creating mock servers from:

- Bruno collections and saved response examples
- OpenAPI specifications
- Mock response rules
- Request body matching
- Headers and query parameter matching
- Multiple responses for the same endpoint

> Mock Servers are currently in Beta. Enable them from **Preferences → Beta → Mock Server** before getting started.

## Getting Started

Clone this repository:

```bash
git clone https://github.com/bruno-collections/mock-examples.git
```

Open Bruno and import the repository as a **collection**.

> **Important:** Import this collection in Bruno directly by providing the GitHub URL in the import modal.

Once imported, you'll find sample collections, API specifications, and response examples ready to explore.

## What's Included

### Echo API Mock Example

The Echo API example demonstrates how to create a mock server from an existing Bruno collection.

The basic workflow is:

```text
Echo API Request
      ↓
Save Response as Example
      ↓
Create Mock Server
      ↓
Sync with Examples
      ↓
Start Server
      ↓
Call the API locally
```

After syncing the saved examples, you can edit the generated mock responses and add **Rules** to simulate different API behaviors.

For example, you can return different responses based on:

```text
Header → x-api-key → equals → secret123

Query → type → equals → admin

Body → user.type → equals → admin
```

This is useful for testing scenarios that the original Echo API may not provide.

### Petstore OpenAPI Mock Example

The Petstore example demonstrates an API-first workflow using an **OpenAPI specification**.

Instead of requiring a working backend, Bruno can generate mock responses directly from the API specification.

```text
Petstore OpenAPI Spec
        ↓
Create Mock Server
        ↓
Generate from API Spec
        ↓
Start Server
        ↓
Test the API locally
```

You can then customize the generated responses or add rules to simulate different scenarios.

## Using Rules

Rules determine **when a specific mock response should be returned**.

For example, suppose you have multiple responses for:

```http
POST /users
```

You can configure one response with:

```text
Target: Body
Key: user.type
Operator: equals
Value: admin
```

Incoming request:

```json
{
  "user": {
    "type": "admin"
  }
}
```

Bruno matches the rule and returns the response configured for the `admin` scenario.

For nested body fields, you can use dotted paths such as:

```text
user.type
$.user.type
```

Both formats are supported. Array indexing and advanced JSONPath filters are currently not supported.

## Why Use Mock Servers?

Mock servers are useful when you want to:

- Develop a frontend before the backend is ready
- Test APIs without calling the real service
- Simulate success and error responses
- Test different request values and scenarios
- Prototype an API from an OpenAPI specification
- Work with predictable API responses during development
- Let frontend, backend, and QA teams work in parallel

## Example Workflow

Try modifying one of the included mock responses:

1. Start the mock server.
2. Open a mock response.
3. Edit the expected status, headers, or body.
4. Add a Header, Query, or Body rule.
5. Send a matching request.
6. Check the returned response.
7. Use **Request Log** if the request doesn't match the expected response.

This helps demonstrate the core Mock Server flow:

```text
Incoming Request
       ↓
Method + Path
       ↓
Evaluate Rules
       ↓
Select Mock Response
       ↓
Return Status + Headers + Body
```

## Learn More

- [Bruno Documentation](https://docs.usebruno.com/mock-servers/overview)
- [Bruno GitHub](https://github.com/usebruno/bruno)
- [Bruno Public Collections](https://github.com/bruno-collections)

