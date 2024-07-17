# Account Management System

This project is an account management system that allows creating accounts for customers, making deposits, withdrawals, and transfers between accounts.

## Features

- Create accounts for existing customers.
- Make deposits into accounts.
- Make withdrawals from accounts.
- Transfer funds between accounts.
- Check the balance of an account.
- Check the transactions of an account.

## Requirements

- Node.js (v14 or higher)
- npm (v6 or higher)

## Installation

1. Clone the repository:

   ```bash
   git clone "github repository path"

Install the dependencies:

BASH
npm install
Make sure the customers.json file is in the data folder and has the following format:

JSON
[
  {
    "id": 1,
    "name": "Arisha Barrón"
  },
  {
    "id": 2,
    "name": "Branden Gibson"
  },
  {
    "id": 3,
    "name": "Rhonda Church"
  },
  {
    "id": 4,
    "name": "Georgina Hazel"
  }
]
Usage
Start the server:

BASH
npm start
The server will be available at <http://localhost:3000>.

Endpoints
Create an Account
URL: /api/accounts

Method: POST

Description: Creates a new account for an existing customer.

Request Body:

JSON
{
  "customerId": 1,
  "initialDeposit": 1000
}
Successful Response:

JSON
{
  "id": 1,
  "customerId": 1,
  "balance": 1000,
  "transactions": []
}
Make a Deposit
URL: /api/accounts/:accountId/deposit

Method: POST

Description: Makes a deposit into an existing account.

Request Body:

JSON
{
  "amount": 500
}
Successful Response:

JSON
{
  "id": 1,
  "customerId": 1,
  "balance": 1500,
  "transactions": [
    {
      "type": "deposit",
      "amount": 500,
      "date": "2023-10-01T12:00:00Z"
    }
  ]
}
Make a Withdrawal
URL: /api/accounts/:accountId/withdraw

Method: POST

Description: Makes a withdrawal from an existing account.

Request Body:

JSON
{
  "amount": 200
}
Successful Response:

JSON
{
  "id": 1,
  "customerId": 1,
  "balance": 1300,
  "transactions": [
    {
      "type": "withdraw",
      "amount": 200,
      "date": "2023-10-01T12:00:00Z"
    }
  ]
}
Transfer Funds
URL: /api/accounts/:accountId/transfer

Method: POST

Description: Transfers funds from one account to another.

Request Body:

JSON
{
  "amount": 300,
  "targetAccountId": 2
}
Successful Response:

JSON
{
  "id": 1,
  "customerId": 1,
  "balance": 1000,
  "transactions": [
    {
      "type": "transfer",
      "amount": 300,
      "date": "2023-10-01T12:00:00Z",
      "to": 2
    }
  ]
}
Check the Balance
URL: /api/accounts/:accountId/balance

Method: GET

Description: Checks the balance of an account.

Successful Response:

JSON
{
  "balance": 1000
}
Check the Transactions
URL: /api/accounts/:accountId/transactions

Method: GET

Description: Checks the transactions of an account.

Successful Response:

JSON
[
  {
    "type": "deposit",
    "amount": 500,
    "date": "2023-10-01T12:00:00Z"
  },
  {
    "type": "withdraw",
    "amount": 200,
    "date": "2023-10-01T12:00:00Z"
  },
  {
    "type": "transfer",
    "amount": 300,
    "date": "2023-10-01T12:00:00Z",
    "to": 2
  }
]
Project Structure
models/account.js: Defines the account model.
services/accountServices.js: Contains the business logic for account management.
controllers/accountControllers.js: Handles HTTP requests and calls the corresponding services.
routes/accountRoutes.js: Defines the API routes.
data/customers.json: JSON file that contains customer data.
