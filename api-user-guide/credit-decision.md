---
title: Credit Decision
nav_order: 1
has_children: true
---

# Credit Decision API

The Credit Decision API automates the decision-making process for credit-approval based on customer data. The data could include the following:

- FICO score
- Debt-to-income ratio
- Length of credit history
- Number of late payments/delinquent accounts

Whether a customer is approved for the credit depends on your specific use case. 

The following page details the paths and parameters of the Credit Decision API.

The Credit Decision API is meant for customer data collection and not to set the criteria for credit approval. To set the requirements for credit approval based on your accounts, see the [Credit Requirements] API.
{: .warning}

## Path and HTTP methods

The Credit Decision API uses the following Path and HTTP method:

```json
POST <baseURL>/credit-decision
```
{% include copy-curl.html %}

For the `baseURL`, you can access two servers to use the API:

- Production: https://api.fintechbank.com/v1
- Sandbox: https://sandbox.fintechbank.com/v1

Before using the production server, we recommend testing the Credit Decision API using the Sandbox URL.

## Authentication

The Credit Decision API uses API keys to authenticate with HTTP Basic Auth. To see a list of your API keys, log into to the Fintech Bank dashboard, go to your profile and select **keys**.

## Request body fields

The Credit Decision API requires the following request body fields:

| Field | Type | Description | 
|:---|:---|:---| 
| `account_id` | string | The unique identifier for the customer's account, for example `15151`. | 
| `order_id` | string | The unique identifier for the credit application order, for example, `32131231231241`. | 
| `customer_ip` | string | The IPv4 address of the customer making the credit request, for example, "1.1.1.1". Only IPv4 is supported. | 
| `card_holder_name` | string | The full name of the credit card holder. | 
| `ssn` | string | The Social Security number of the customer. | 
| `dob` | string | The date of birth of the customer in a `YYYY-MM-DD` format .| 
| `card_holder_email` | string | The email address of the cardholder. |










