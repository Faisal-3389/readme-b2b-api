---
title: Issuing Your First Card
excerpt: This page will help you get started with Moon's Card Issuing API
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Fetch Available Card Products

To issue your first card, first you need to fetch the card products available to issue:

```curl cURL Request
curl --request GET \
     --url 'https://stagingapi.paywithmoon.com/v1/api-gateway/card/card-products?perPage=10' \
     --header 'accept: application/json' \
     --header 'x-api-key: YOUR_API_KEY'
```

This will return a list of card products like this:

```json Response
{
  "pagination": {
    "currentPage": 1,
    "from": 1,
    "lastPage": 30,
    "perPage": 10,
    "total": 100
  },
  "card_products": [
    {
      "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "name": "Card Product 1",
      "minimum_value": 1.5,
      "maximum_value": 1.5,
      "fee_amount": 1.5,
      "fee_type": "string",
      "categories": [
        "string"
      ]
    }
  ]
}
```

In this case, there is one card product available for issue with id 3fa85f64-5717-4562-b3fc-2c963f66afa6. 

## Issue a Card

Let's issue a card with the POST /card endpoint!

```curl cURL Request
curl --request POST \
     --url https://stagingapi.paywithmoon.com/v1/api-gateway/card/3fa85f64-5717-4562-b3fc-2c963f66afa6 \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-api-key: YOUR_API_KEY'
```

This will return the details of your newly issued card.

```json Response
{
  "card": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "balance": 0,
    "available_balance": 0,
    "expiration": "2026-07-20T15:49:04-07:00",
    "display_expiration": "12/26",
    "terminated": false,
    "card_product_id": "beeba3e2-e358-451b-888b-96a51fea0756",
    "pan": "4000123456789010",
    "cvv": "123",
    "support_token": "xX8qQxMdW3H3",
    "frozen": false
  }
}
```

Congrats! You've issued your first card.
