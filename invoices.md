Invoices API
============

The Invoices API allows you to get detailed information about your Bugsnag invoices.


Contents
--------

- [List your Account's Invoices](#list-your-account-s-invoices)
- [Get Invoice details](#get-invoice-details)


List your Account's Invoices
----------------------------

Get a list of all Invoices for the currently authenticated Bugsnag [Account](accounts.md).

```http
GET /account/invoices
```

### Parameters

- **sort** - `created_at`. Default: `created_at`.
- **direction** - `asc`, `desc`. Default `desc`.
- **per_page** - how many results to return per page. Default 30.

### Response

```http
Status: 200 OK
Link: <https://api.bugsnag.com/account/invoices?offset=50baee27a43ccdf778000002>; rel="next"
```
```json
TODO
```


Get Invoice details
-------------------

Get the details of a the given Bugsnag Invoice.

```http
GET /invoices/:invoice_id
```

### Response

```http
Status: 200 OK
```
```json
TODO
```