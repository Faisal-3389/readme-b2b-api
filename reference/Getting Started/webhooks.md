---
title: Webhooks
excerpt: >-
  Moon offers webhook notifications to keep you informed of important events
  related to your card transactions, declined transactions, and credit fund
  updates. Each webhook payload provides detailed information about the event,
  allowing you to take specific actions or update your records.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Available Webhooks

Below are the possible webhook events you can subscribe to:

### 1. Card Transaction Event

Triggered when a new card transaction is made. This webhook provides details about the transaction, including card information and merchant data.

**Event Name**: `CARD_TRANSACTION`

#### Example Payload

```json
{
   data: { 
    "id": "txn_123456789",
    "card": {
      "public_id": "card_pub_987654321",
      "name": "Card name",
      "type": "Moon 1X Card"
    },
    "transaction_id": "500539aa-d323-4fe7-9162-8d6123515ec5",
    "transaction_status": "SETTLED",
    "datetime": "2024-11-12T08:45:23Z",
    "merchant": "Starbucks",
    "amount": 150.00,
    "ledger_currency": 840,
    "amount_fees_in_ledger_currency": 1,
    "amount_in_transaction_currency": 10,
    "transaction_currency": 540,
    "amount_fees_in_transaction_currency": 1,
    "fees": [{
      "type": "TRANSACTION_FEE",
      "amount": 1,
      "fee_amount_in_transaction_currency": 1,
      "fee_description": "A 1% fee",
      
      "feeAmountInTransactionCurrency": 1,
      "feeDescription": "A 1% fee",
      
      "deprecated_fields": ["feeAmountInTransactionCurrency", "feeDescription"]
    }],

    "amountFeesInLedgerCurrency": 1,
    "ledgerCurrency": 840,
    "amountInTransactionCurrency": 10,
    "transactionCurrency": 540,
    "amountFeesInTransactionCurrency": 1,
    "transactionStatus": "SETTLED",
    "transactionId": "500539aa-d323-4fe7-9162-8d6123515ec5",
     
    "deprecated_fields": ["transactionId", "transactionStatus", "ledgerCurrency", "amountFeesInLedgerCurrency", "amountInTransactionCurrency", "transactionCurrency", "amountFeesInTransactionCurrency"]
	},
  type: "CARD_TRANSACTION"
}

 
```

<br />

### 2. Card Authorization Refund Event

Triggered when a new card refund transaction is made. This webhook provides details about the transaction, including card information and merchant data.

**Event Name**: `CARD_AUTHORIZATION_REFUND`

#### Example Payload

```json
{
   "data": { 
    "id": "txn_123456789",
    "card": {
      "public_id": "card_pub_987654321",
      "name": "Card name",
      "type": "Moon 1X Card"
    },
    "transaction_id": "500539aa-d323-4fe7-9162-8d6123515ec5",
    "transaction_status": "SETTLED",
    "datetime": "2024-11-12T08:45:23Z",
    "merchant": "Starbucks",
    "amount": 150.00,
    "ledger_currency": 840,
    "amount_fees_in_ledger_currency": 1,
    "amount_in_transaction_currency": 10,
    "transaction_currency": 540,
    "amount_fees_in_transaction_currency": 1,
    "fees": [],

    "amountFeesInLedgerCurrency": 1,
    "ledgerCurrency": 840,
    "amountInTransactionCurrency": 10,
    "transactionCurrency": 540,
    "amountFeesInTransactionCurrency": 1,
    "transactionStatus": "SETTLED",
    "transactionId": "500539aa-d323-4fe7-9162-8d6123515ec5",
     
    "deprecated_fields": ["transactionId", "transactionStatus", "ledgerCurrency", "amountFeesInLedgerCurrency", "amountInTransactionCurrency", "transactionCurrency", "amountFeesInTransactionCurrency"]
  },
  "type": "CARD_AUTHORIZATION_REFUND"
}

 
```

### 3. Decline Transaction Event

Triggered when a card transaction is declined. This webhook provides details about the declined transaction, including the reason and merchant information.

Event Name: `CARD_DECLINE`

<br />

#### Example Payload

```json
{
   "data": {
    "id": "decline_123456789",
    "created_at": "2024-11-12T09:15:47Z",
    "merchant": "Amazon",
    "amount": 29.99,
    "customer_friendly_description": "Insufficient funds",
    "card_public_id": "card_pub_987654321"
  },
  "type": "CARD_DECLINE"
}

 
```

<br />

### 4. Moon Credit Funds Credited Event

Triggered when funds are credited to a Moon Credit account. This webhook provides details about the credited funds, including the amount and currency.

Event Name: `MOON_CREDIT_FUNDS_CREDITED`

#### Example Payload

<br />

```json
{
   "data": {
    "amount": 100.0,
    "id": "credit_123456789",
    "invoice_id": "b0687bce-7780-4edf-909e-37fefde57cfc",
    "createdAt": "2024-11-12T10:05:12Z",
    "currency": "USD",
    "created_at":"2024-11-12T10:05:12Z", 
     
    "createdAt": "2024-11-12T10:05:12Z",
     
    "deprecated_fields": ["createdAt"]
  },
  "type": "MOON_CREDIT_FUNDS_CREDITED"
}
```

<br />

### 5. Transaction Confirmation Count Update

Triggered when confirmation count of an invoice is updated.

Event Name: `TRANSACTION_CONFIRMATION_COUNT_UPDATED`

#### Example Payload

```json JSO
{
  "data": {
    "payment_id": 1,
    "address": "0x5c45bCe992cd41Ec68F05D0E592Ab39FcA45F28c",
    "transaction_hash": "098f6bcd4621d373cade4e832627b4f6",
    "confirmation_count": 10,
    "amount": "0.01",
    "currency": "USDC",
    "blockchain": "POLYGON",
    "broadcast_time": "2025-01-02 23:56:45",
    "invoice_id": "12c58693-8094-4a2e-982e-a2183ea40dd7"
  },
  "type": "TRANSACTION_CONFIRMATION_COUNT_UPDATED"
}
```

<br />

Each webhook provides real-time information directly to your application, enabling seamless tracking and management of card transactions and credits. Be sure to handle each event according to your business logic to ensure data integrity and a smooth user experience.

These JSON examples should make it easy for developers to understand the structure and data provided by each webhook.