---
title: Simulate a Card Transaction
excerpt: |
  This endpoint only works in sandbox.

   This endpoint enables you to simulate a transaction for the specified card. You can set the transaction amount, currency, merchant name and merchant country code.
   
   The transaction type must be one of the following:
   AUTHORIZATION,
   REVERSAL,
   CLEARING,
   REFUND. 
   
   Example:
   
   AUTHORIZATION 10 USD. => this will trigger an authorization webhook that contains a transaction ID that must be used in the following simulation requests.
   
   REVERSAL 2 USD. => this will simulate reversing $2 of the authorization.
   
   CLEARING 8 USD. => this will simulate setting the remaining $8.
   
   REFUND 8 USD. => this will simulate refunding the $8.
api:
  file: moon-card-issuing-api-22.json
  operationId: post_v1-api-gateway-card-card-id-transactions
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---