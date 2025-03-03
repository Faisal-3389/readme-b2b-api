---
title: Fetching Card Transactions
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
We provide a simple approach to fetching card transactions in addition to up to date transaction status data.

Let's fetch the list of transactions on a card! 

```curl cURL Request
curl --request GET \
     --url 'https://stagingapi.paywithmoon.com/v1/api-gateway/card/550e8400-e29b-41d4-a716-446655440000/transactions?currentPage=1&perPage=10' \
     --header 'accept: application/json' \
     --header 'x-api-key: YOUR_API_KEY'
```

This will return a paginated list of transactions as follows:

```json JSON Response
{
  "transactions": [
    {
      "type": "CARD_TRANSACTION",
      "data": {
        "card": {
          "public_id": "12345678",
          "name": "MoonX Card",
          "type": "VISA"
        },
        "transactionId": "12345678",
        "transactionStatus": "SETTLED",
        "datetime": "2022-01-01T00:00Z",
        "merchant": "MoonX",
        "amount": 100,
        "ledgerCurrency": "USD",
        "amountFeesInLedgerCurrency": 1,
        "amountInTransactionCurrency": 100,
        "transactionCurrency": "USD",
        "amountFeesInTransactionCurrency": 1,
        "fees": [
          {
            "type": "TRANSACTION_FEE",
            "amount": 1,
            "feeAmountInTransactionCurrency": 1,
            "feeDescription": "A Fee Description"
          }
        ]
      }
    }
  ]
}
```

For cards on our sandbox environment, please first [generate simulated transactions](https://pay-with-moon.readme.io/reference/simulating-card-transactions).
