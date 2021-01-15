---
title: Moeco API

language_tabs:
  - shell: cURL

toc_footers:

includes:
  - masternodeapi
  - logisticapi
  - errors

search: true
---

# Moeco API

The API is built on the basis of the HTTP protocol with the exchange of data in the JSON format. Communication between the server and the client is carried out through the interface end-points.

Each server response to a client request is represented by a set of HTTP status (status code) and a set of data of a specific structure:

The **meta** attribute contains service information and consists of the following attributes:

- total — total number of objects that meet the request criteria;
- count — a number of objects in the current response;
- offset — offset based on the request results in accordance with the total number of results and the current output size;
- error — contains information about the error during the execution of the request:
message — error message;
- details — additional information about the error (e.g., information about unsuccessful validation of request parameters, and etc.).

The **data** attribute directly contains the data obtained from the request and represents an array of objects. The representation of objects in the array may differ both between different interface end-points, and from request to request.

In order for the data to appear in response to requests for transactions, invoices, or payments, you may need to create them in the interface of the gate and the Masternode. How to do it, see the instructions How to check transactions, invoices and payments.
