---
title: Simulating Card Transactions
excerpt: Simulate transactions on a card in our sandbox environment.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## The Lifecycle of a Card Transaction

When a purchase is made with a card, a transaction is created. This transaction goes through a number of states and phases. These are the core components you need to understand to successfully simulate transactions:

- Authorization - this is when a transaction is first made on a card. The transaction is authorized and a hold is placed on the card. The transaction is now _pending_.
- Reversal - amounts that have been authorized may also be reversed in whole or in part. If the entire amount of an authorization is reversed, the transaction is effectively cancelled.
- Clearing - for a transaction to complete, it must be _cleared_. If a transaction is entirely cleared, then the transaction is said to be _settled_.
- Refund - after a transaction is cleared, it may then be refunded in whole or in part. All refunds are considered _settled_.

For the purposes of simulating live card transactions, we provide an endpoint that allows you to trigger Authorizations, Reversals, Clearings and Refunds to simulate the full lifecycle of a transaction in our sandbox environment. 

## Example

1. You go on Amazon.com and purchase $100 of goods. This creates a $100 _pending_ transaction.  
   Simulate with a $100 authorization.
2. One of the items you ordered is out of stock. Amazon reduces the authorization by $20. Now your transaction is an $80 _pending_ transaction.  
   Simulate with a $20 reversal.
3. Amazon ships the remaining products you ordered and the payment settles the following day. Now you have an $80 _settled_ transaction.  
   Simulate with an $80 clearing.
4. One of the products you purchased was not acceptable. You return a $30 item and receive a full refund. Now you have a new $30 settled refund transaction on your card.  
   Simulate with a $30 refund.