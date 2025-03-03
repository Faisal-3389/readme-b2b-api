---
title: Adding a Balance
excerpt: Let's add a balance to a card!
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Add Balance to Moon Reserve

In order to add a balance to a card, first you must add a balance to your account. We call the balance on your account, your "Moon Reserve". Moon Reserve is the balance on your account that is unallocated to a card. 

First, we need to generate an invoice. Let's say we want to add $1000 to our Moon Reserve and want to pay with USDC on Polygon.

```curl cURL Request
curl --request POST \
     --url https://stagingapi.paywithmoon.com/v1/api-gateway/onchain/invoice \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-api-key: YOUR_API_KEY' \
     --data '
{
  "creditPurchaseAmount": 1000,
  "blockchain": "POLY",
  "currency": "USDC"
}
'
```

This will generate an invoice as follows:

```json JSON Response
{
  "invoice": {
    "id": "inv_1GqIC8w4zwW7xX8qQxMdW3H3",
    "address": "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa",
    "usdAmountOwned": "1000.00",
    "cryptoAmountOwed": "1000.00",
    "exchangeRateLockExpiration": 1630000000,
    "currency": "USDC",
    "blockchain": "POLY"
  }
}
```

This invoice contains a Polygon address. Upon sending 1000 USDC to that address and waiting a sufficient number of block confirmations, $1000 of Moon Reserve will be credited to your account. If you've configured a webook endpoint, you will receive a webhook notification when the balance has been added to your account. 

## Add Balance to a Card

Now we can add a balance to a card! Let's add a $100 balance to the card we created in the last section.

```curl cURL Request
curl --request POST \
     --url https://stagingapi.paywithmoon.com/v1/api-gateway/card/550e8400-e29b-41d4-a716-446655440000/add-balance \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'x-api-key: YOUR_API_KEY' \
     --data '{"amount":"100"}'
```

This request will return the card details including the card's new balance:

```json
{
  "card": {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "balance": 100,
    "available_balance": 100,
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

You now have $100 on a card! Don't spend it all in one place :smiley: