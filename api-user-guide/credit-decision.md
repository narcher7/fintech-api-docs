---
title: Credit Decision
nav_order: 1
---

# Credit Decision API

The Credit Decision API automates the decision-making process for credit-approval based on customer data. The data the customer provides includes:

- Name
- Date of Birth
- Social Security number (SSN)

The following page details how to implement the Credit Decision API.

**NOTE:** The Credit Decision API is meant for customer data collection and not to set the criteria for credit approval. 

## Path and HTTP methods

The Credit Decision API uses the following Path and HTTP method:

```json
POST <baseURL>/credit-decision
```

For the `baseURL`, you can access two servers to use the API:

- Production: https://api.fintechbank.com/v1
- Sandbox: https://sandbox.fintechbank.com/v1

Before using the production server, we recommend testing the Credit Decision API using the Sandbox URL.

## Authentication

The Credit Decision API uses API keys to authenticate with HTTP Basic Auth. To see a list of your API keys, log in to the Fintech Bank dashboard, go to your profile and select **keys**.

## Request body fields

The Credit Decision API requires the following request body fields:

| Field | Type | Description | 
|:---|:---|:---| 
| `account_id` | string | The unique identifier for the customer’s account, for example, `15151`. | 
| `order_id` | string | The unique identifier for the credit application order, for example, `32131231231241`. | 
| `customer_ip` | string | The IPv4 address of the customer making the credit request, for example, “1.1.1.1”. Only IPv4 is supported. | 
| `card_holder_name` | string | The full name of the credit card holder. | 
| `ssn` | string | The SSN of the customer. Note that the string does not use dashes or spaces. | 
| `dob` | string | The date of birth of the customer in a `YYYY-MM-DD` format.| 
| `card_holder_email` | string | The email address of the cardholder. |


## Example request

The following example request is for an applicant named Jane Smith, including all of the required information outlined in the [Request body fields](#request-body-fields) section. 

```json
curl --location ‘https://sandbox.fintechbank.com/v1/credit-decision’ \
--header ‘Content-Type: application/json’ ‘Authorization: Bearer {your_api_key} \
--data-raw ‘{
    “account_id”: “10000”,
    “order_id”: “32131231231241”,
    “customer_ip”: “1.1.1.1”,
    “card_holder_name”: “Jane Smith”,
    “ssn”: “123456789”,
    “dob”: “1979-08-02”,
    “card_holder_email”: “jane-smith@email.com”
}’
```

## Example responses

This section details how the Credit Decision API can respond to a request.

### Credit approval

If the customer is approved for the credit they are applying for, they’ll receive an `approved` response with the card information for their new credit:

```json
{
  “decision”: “approved”,
  “card_number”: “4111111111111111”,
  “card_expire_month”: “12”,
  “card_expire_year”: “2028”,
  “card_security_code”: “000”
}
```

### Credit denial

If the customer is denied, the decision field will show `denied` and not include the other response body fields:

```json
{
  “decision”: “denied”
}
```

## Response body fields

| Field | Type | Description | 
|:---|:---|:---| 
| `decision` | string | The outcome of the request for credit approval, either `approved` or `denied`. |  
| `card_number` | string | The 16-digit credit card number issued if the credit is approved. |  
| `card_expire_month` | string | The expiry month of the credit card. | 
| `card_expire_year` | string | The expiry year of the credit card. | 
| `card_security_code` | string | The security code for the issued credit card. |

With errors (status codes 400, 401, or 500), the response body will contain the following field:

| Field | Type | Description | 
|:---|:---|:---|
| `error` | string | A message describing the error | 

This error response structure is consistent across different error types, with the error message changing based on the specific error encountered.

## Troubleshooting errors

When a request is invalid, the Credit Decision API responds with a message detailing the error. This list outlines common errors and provides steps to resolve them:

- “Invalid API key”: The API key used to authenticate is incorrect. Make sure that your API key for authorization is correct.
- “Invalid SSN format”: The customer’s SSN was not input in the request properly. Make sure the customer has input their social security number with nine digits and no dashes.
- “Internal server error”: The network cannot be accessed because of an internal server error. Consult your system administrator to determine if any steps can be taken to mitigate the issue.

## Best practices

When implementing the Credit Decision API for your financial solution, consider the following best practices:

- **Data protection**: Securely encrypt and protect customer data when stored in databases.
- **Compliance**: Make sure you comply with the relevant financial regulations (for example, GDPR) of your region. For customers providing their data to you, implement consent mechanisms so customers understand how their data is being used.
- **Rate limiting**: To prevent server downtown, implement rate limiting on your cluster. The rate limit you set depends on the expected size of your customer base.







