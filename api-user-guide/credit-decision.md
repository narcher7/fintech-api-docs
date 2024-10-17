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
POST /credit-decision
```
{% include copy-curl.html %}





