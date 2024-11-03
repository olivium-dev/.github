# Welcome to Olivium Github Organization

Welcome to the official GitHub organization of Olivium. This organization hosts the code repositories for various capabilities developed by Olivium. 

## Available Documentations

Currently, we have documentation available for the following capabilities:
- [License Management](https://github.com/olivium-dev/olivium-capabilities-docs/blob/main/liscence/be_liscence.md)
- [Media Consumption Analysis](https://github.com/olivium-dev/olivium-capabilities-docs/blob/main/media_consumption_analysis/be_media_consumption_analysis.md)

## Way of Working

Here at Olivium, we follow a simple yet effective workflow to ensure code quality and consistency:
- No direct pushes to the master or main branches are allowed.
- Every bug or issue must be handled in a specific branch named after the JIRA ticket ID for easy tracking.
- Pull requests must be clean and production-ready, with no commented code allowed.

## Pipelines

Ensure to run the publish pipeline after each merge to the master branch to maintain continuous integration and delivery.

## Contributing to Olivium-Capabilities-Docs

The `olivium-capabilities-docs` repository is vital for keeping all developer-oriented documentation centralized. Each capability (such as backend, mobile, and web) should have its dedicated documentation.

### Contribution Criteria

For anyone looking to contribute, the documentation should include:
- **Endpoint Definitions**: Clearly define what the API endpoint does.
- **Parameters**: List all the parameters required by the API.
- **Request and Response Examples**: Provide clear examples of what the API expects and what it returns.
- **Pseudocode**: Offer a pseudocode or real code snippet that explains the logic behind the endpoint.

### Example Documentation Structure

**API Name**: Create One-Time License

**Endpoint**: `/license/one-time`
**Method**: `POST`
**Description**: Creates a single-use license that does not renew.

#### Parameters
- `productID` (string): Unique identifier for a product.
- `clientID` (string): Unique identifier for a client.
- `licenseType` (string): Specifies the type of license.

#### Request
```json
{
  "productID": "prod-001",
  "clientID": "client-001",
  "licenseType": "standard"
}
```

#### Response
- `201 Created`: License created successfully.
- `400 Bad Request`: Missing required fields.

#### Pseudocode
```csharp
public IActionResult CreateOneTimeLicense(string productID, string clientID, string licenseType)
{
    ValidateRequiredParameters(productID, clientID, licenseType);
    var licenseID = GenerateLicenseID();
    var license = new License(licenseID, productID, clientID, licenseType, DateTime.UtcNow, null);
    Database.Licenses.Add(license);
    Database.SaveChanges();
    return Created($"api/license/{licenseID}", license);
}
```

Feel free to add more sections as required for each capability to help other developers understand and utilize your code.

