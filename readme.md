# Point API Docs

Point API is a RESTful Web Service served as communication bridge between clients to central of Kompas Gramedia Point Database whose organized by Corporate IT & IS Kompas Gramedia.

## HTTP(S) Request

Point API can be requested through HTTP(S) Request to Point Base URL endpoint. The HTTP(S) Header has to be used to allow proper authentication.

## API Base URL

Development Environment : <code>https://staging-point.myvalue.id/</code><br/>
Production Environment : <code>https://point.myvalue.id/</code>

### HTTP(S) Header

<table class="table">
<thead>
<tr>
  <th>Header</th>
  <th>Value</th>
  <th>Definition</th>
</tr>
</thead>
<tbody>
<tr>
  <td>Content-Type</td>
  <td>application/json</td>
  <td>The Content-Type field indicates that JSON type is acceptable to send to the recipient</td>
</tr>
<tr>
  <td>Accept</td>
  <td>application/json</td>
  <td>The Accept field is used to specify that JSON type is acceptable for the response</td>
</tr>
<tr>
  <td>Authorization</td>
  <td>Bearer <code>TOKEN</code></td>
  <td>The Authorization field credentials can be requested to Administrator</td>
</tr>
</tbody>
</table>

#### Content-Type and Accept Header

In Point API, the input and output parameters of the methods will be in JSON format. To accept JSON input and output parameters, you need to add the following HTTP(S) header:

  <ul>
    <li><code>Content-Type : application/json</code></li>
    <li><code>Accept: application/json</code></li>
  </ul>

#### Authorization Header

The authorization header utilizes Membership Server Key following JWT convention.                

For example, a token value received from administrator is : <code>jfa002nwin98fnw9vh.j89w98nv8hvwkfdjfjh20.9u0hfa0dsbv9v9vd</code>

Then for Authorization Header, you can fill the value with:<br/><code>Bearer jfa002nwin98fnw9vh.j89w98nv8hvwkfdjfjh20.9u0hfa0dsbv9v9vd</code>

## Point API

### API Methods

<table class="table">
  <thead>
    <tr>
      <th>End Point</th>
      <th>HTTP Method</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>/point</td>
      <td>GET</td>
      <td>Get member total point</td>
    </tr>
    <tr>
      <td>/point/transaction</td>
      <td>POST</td>
      <td>Point transaction (Earning/Redeem)</td>
    </tr>
    <tr>
      <td>/point/history</td>
      <td>GET</td>
      <td>Get member history point</td>
    </tr>
    <tr>
      <td>/point/expired</td>
      <td>GET</td>
      <td>Get member expired point</td>
    </tr>
    <tr>
      <td>/point/recap</td>
      <td>GET</td>
      <td>Get point recap per Brand or Merchant</td>
    </tr>
    <tr>
      <td>/point/estimate</td>
      <td>POST</td>
      <td>Calculate estimate earn/redeem point</td>
    </tr>
    <tr>
      <td>/point/revision</td>
      <td>POST</td>
      <td>Transaction point revision</td>
    </tr>
  </tbody>
</table>

### Get Point

Point API serve end point API to get data total point using <code>valueid</code>, <code>memberno</code>, <code>email</code>, and <code>cardnumber</code>.

<table class="table" width="100%">
  <thead>
    <tr>
      <th>End Point</th>
      <th>HTTP Method</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>/point? <code>valueid</code>=&<code>memberno</code>=&<code>email</code>=&<code>cardnumber</code>=</td>
      <td>GET</td>
      <td>Get member total point</td>
    </tr>
  </tbody>
</table>

#### Request Parameters

You don't have to fill out all of these parameters.

<table class="table">
<thead>
  <tr>
    <th>Parameter</th>
    <th>Type</th>
    <th>Definition</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>valueid</code></td>
    <td>String</td>
    <td>The ValueID of members</td>
  </tr>
  <tr>
    <td><code>memberno</code></td>
    <td>String</td>
    <td>The MemberNo of members</td>
  </tr>
  <tr>
    <td><code>email</code></td>
    <td>String</td>
    <td>The Email of members</td>
  </tr>
  <tr>
    <td><code>cardnumber</code></td>
    <td>String</td>
    <td>The Card Number of members</td>
  </tr>
</tbody>
</table>

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from end point
<br/><strong>Data</strong> <code>object</code> : Object of data
<br/><strong>TotalPoint</strong> <code>numeric</code> : Total point of member
<br/><strong>Status</strong> <code>string</code> : Active/Nonactive member

>Success(200)
``` javascript
	{
      "Message": "Success",
      "Data": {
          "TotalPoint": 1331738,
          "Status": "Active"
      }
  }
```

### Get Expired Point

Point API serve end point API to get data expired point using <code>valueid</code>, <code>memberno</code>, <code>email</code>, and <code>cardnumber</code>.

<table class="table" width="100%">
  <thead>
    <tr>
      <th>End Point</th>
      <th>HTTP Method</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>/point/expired? <code>valueid</code>=&<code>memberno</code>=&<code>email</code>=&<code>cardnumber</code>=</td>
      <td>GET</td>
      <td>Get member expired point</td>
    </tr>
  </tbody>
</table>

#### Request Parameters

You don't have to fill out all of these parameters.

<table class="table">
<thead>
  <tr>
    <th>Parameter</th>
    <th>Type</th>
    <th>Definition</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>valueid</code></td>
    <td>String</td>
    <td>The ValueID of members</td>
  </tr>
  <tr>
    <td><code>memberno</code></td>
    <td>String</td>
    <td>The MemberNo of members</td>
  </tr>
  <tr>
    <td><code>email</code></td>
    <td>String</td>
    <td>The Email of members</td>
  </tr>
  <tr>
    <td><code>cardnumber</code></td>
    <td>String</td>
    <td>The Card Number of members</td>
  </tr>
</tbody>
</table>

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from end point
<br/><strong>Data</strong> <code>object</code> : Object of data
<br/><strong>TotalPoint</strong> <code>numeric</code> : Total expired point of member
<br/><strong>Status</strong> <code>string</code> : Active/Nonactive member

>Success(200)
``` javascript
  {
      "Message": "Success",
      "Data": {
          "TotalPoint": 50000,
          "Status": "Active"
      }
  }
```

### Transaction

Point API serve end point API to earn or redeem for members.

<table class="table" width="100%">
  <thead>
    <tr>
      <th>End Point</th>
      <th>HTTP Method</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>/point/transaction</td>
      <td>POST</td>
      <td>Point transaction (Earning/Redeem)</td>
    </tr>
  </tbody>
</table>

#### Request Body

<strong>MutasiTypeName</strong> <code>string(10)</code> : Required, "EARNING" or "REDEEM"
<br/><strong>Searchby</strong> <code>string(15)</code> : Required, Paramater to search member would do transaction. The value are "KG_ID" for search using ValueID, "MEMBERNO" for search using MemberNo, "EMAIL" for search using Email, and "CARDNUMBER" for search using Cardnumber
<br/><strong>Id</strong> <code>string(50)</code> : Required, the value to be searched
<br/><strong>IdOutlet</strong> <code>string(10)</code> : Required, The ID of outlet where a member do transaction
<br/><strong>ReferenceNo</strong> <code>string(30)</code> : Required and Unique, The reference no of member transaction
<br/><strong>CreatedDate</strong> <code>datetime</code> : Required,The date and time of member transaction, format <code>yyyy-mm-dd hh:ii:ss</code>
<br/><strong>Amount</strong> <code>numeric</code> : Required, Total amount of member transaction, if <code>J_Point</code> is "0", the point earned/redeem will be calculated using this <code>Amount</code>
<br/><strong>J_Point</strong> <code>numeric</code> : Required, Total point earned/redeem will using this value if it's not filled by "0", the <code>Amount</code> parameter will be ignored
<br/><strong>ExchangeRate</strong> <code>numeric</code> : Required, Exchange conversion for calculating point earn/redeem, if it's not filled by "0", the Exchange Rate from <code>IdOutlet</code> will be ignored
<br/><strong>AmountPoint</strong> <code>numeric</code> : Required, Keep it filled by "0"

>Request body example
``` javascript
  {
    "MutasiTypeName" : "EARNING",
    "Searchby" : "KG_ID", 
    "Id" : "VX1112",
    "IdOutlet" : "MVAPP00001",
    "ReferenceNo" : "12000001818271", 
    "CreatedDate" : "2018-11-11 09:30:00",
    "Amount" : 120000,
    "J_Point" :0,
    "ExchangeRate" : 0,
    "AmountPoint" : 0
  }
```

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from end point
<br/><strong>Data</strong> <code>object</code> : Object of data
<br/>Possible status code:
<br/><code>200</code> : Transaction success
<br/><code>400</code> : Request body doesn't meet specification
<br/><code>422</code> : Transaction failed

>Success(200)
``` javascript
  {
      "Message": "Earning Transaction Success",
      "Data": null
  }
```

### History Transaction

Point API serve end point API to get history transaction

<table class="table" width="100%">
  <thead>
    <tr>
      <th>End Point</th>
      <th>HTTP Method</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>/point/expired? <code>valueid</code>=&<code>memberno</code>=&<code>email</code>=&<code>cardnumber</code>=</td>
      <td>GET</td>
      <td>Get member history transaction</td>
    </tr>
  </tbody>
</table>

#### Request Parameters

You don't have to fill out all of these parameters.

<table class="table">
<thead>
  <tr>
    <th>Parameter</th>
    <th>Type</th>
    <th>Definition</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>valueid</code></td>
    <td>String</td>
    <td>The ValueID of members</td>
  </tr>
  <tr>
    <td><code>memberno</code></td>
    <td>String</td>
    <td>The MemberNo of members</td>
  </tr>
  <tr>
    <td><code>email</code></td>
    <td>String</td>
    <td>The Email of members</td>
  </tr>
  <tr>
    <td><code>cardnumber</code></td>
    <td>String</td>
    <td>The Card Number of members</td>
  </tr>
  <tr>
    <td><code>limit</code></td>
    <td>String</td>
    <td>Limit of transaction showed per request, default is "10"</td>
  </tr>
  <tr>
    <td><code>page</code></td>
    <td>String</td>
    <td>Sequence of history transaction page, start from "0", default is "0"</td>
  </tr>
</tbody>
</table>

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from end point
<br/><strong>Data</strong> <code>object</code> : List of transaction history
<br/><strong>PointMutationSNO</strong> <code>numeric</code> : Unique ID of transaction
<br/><strong>CreatedDate</strong> <code>datetime</code> : Transaction date
<br/><strong>OutletName</strong> <code>string</code> : Outlet where the transaction made
<br/><strong>MutationTypeName</strong> <code>string</code> : Type of transaction, "EARNING" or "REDEEM"
<br/><strong>ReferenceNo</strong> <code>string</code> : The reference no of transaction
<br/><strong>Point</strong> <code>numeric</code> : Total point earned/redeemed
<br/><strong>MemberNo</strong> <code>string</code> : The member unique id
<br/><strong>MemberName</strong> <code>string</code> : The member name
<br/><strong>ValueID</strong> <code>string</code> : The ValueID of member
<br/><strong>Status</strong> <code>string</code> : It will contain null, just ignored

>Success(201)
``` javascript
  {
      "Message": "Success",
      "Data": [
          {
              "PointMutationSNO": 935052,
              "CreatedDate": "2018-09-13T17:45:29.96",
              "OutletName": "MyValue Apps - MyValue Apps",
              "MutationTypeName": "REDEEM",
              "ReferenceNo": "MYV-VCH-1536835529",
              "Point": 1,
              "MemberNo": "M0001000002",
              "MemberName": "TAN SOEN HUI",
              "ValueID": "VX1111",
              "Status": null
          },
          {
              "PointMutationSNO": 935044,
              "CreatedDate": "2018-09-13T16:10:03.033",
              "OutletName": "MyValue Apps - MyValue Apps",
              "MutationTypeName": "EARNING",
              "ReferenceNo": "MYV-VCH-1536829803",
              "Point": 1,
              "MemberNo": "M0001000002",
              "MemberName": "TAN SOEN HUI",
              "ValueID": "VX1111",
              "Status": null
          }
      ]
  }
```

### Recap Transaction

Point API serve end point API to get recap of transactions

<table class="table" width="100%">
  <thead>
    <tr>
      <th>End Point</th>
      <th>HTTP Method</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>/point/recap? <code>param</code>=&<code>value</code>=&<code>startdate</code>=&<code>enddate</code>= &<code>limit</code>=10&<code>page</code>=0</td>
      <td>GET</td>
      <td>Get merchant recap point transaction</td>
    </tr>
  </tbody>
</table>

#### Request Parameters

You don't have to fill out all of these parameters.

<table class="table">
<thead>
  <tr>
    <th>Parameter</th>
    <th>Type</th>
    <th>Definition</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td><code>param</code></td>
    <td>String</td>
    <td>The parameter of recap, "BRAND" or "MERCHANT"</td>
  </tr>
  <tr>
    <td><code>value</code></td>
    <td>String</td>
    <td>Value of paramaters to be search</td>
  </tr>
  <tr>
    <td><code>startdate</code></td>
    <td>date</td>
    <td>Format yyyy-mm-dd</td>
  </tr>
  <tr>
    <td><code>enddate</code></td>
    <td>date</td>
    <td>Format yyyy-mm-dd</td>
  </tr>
  <tr>
    <td><code>limit</code></td>
    <td>String</td>
    <td>Limit of transaction showed per request, default is "10"</td>
  </tr>
  <tr>
    <td><code>page</code></td>
    <td>String</td>
    <td>Sequence of transaction page, start from "0", default is "0"</td>
  </tr>
</tbody>
</table>

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from end point
<br/><strong>Data</strong> <code>object</code> : List of transaction history
<br/><strong>PointMutationSNO</strong> <code>numeric</code> : Unique ID of transaction
<br/><strong>CreatedDate</strong> <code>datetime</code> : Transaction date
<br/><strong>OutletName</strong> <code>string</code> : Outlet where the transaction made
<br/><strong>MutationTypeName</strong> <code>string</code> : Type of transaction, "EARNING" or "REDEEM"
<br/><strong>ReferenceNo</strong> <code>string</code> : The reference no of transaction
<br/><strong>Point</strong> <code>numeric</code> : Total point earned/redeemed
<br/><strong>MemberNo</strong> <code>string</code> : The member unique id
<br/><strong>MemberName</strong> <code>string</code> : The member name
<br/><strong>ValueID</strong> <code>string</code> : The ValueID of member
<br/><strong>Status</strong> <code>string</code> : It will contain null, just ignored

>Success(201)
``` javascript
  {
      "Message": "Success",
      "Data": [
          {
              "PointMutationSNO": 940516,
              "CreatedDate": "2018-10-05T00:00:00",
              "OutletName": "HOTEL ROOM - Hotel Santika Bandung",
              "MutationTypeName": "EARNING",
              "ReferenceNo": "999  /11023",
              "Point": 36364,
              "MemberNo": "M0001000083",
              "MemberName": "Skali ",
              "ValueID": "VSMMYR",
              "Status": null
          },
          {
              "PointMutationSNO": 935368,
              "CreatedDate": "2018-10-02T00:00:00",
              "OutletName": "HOTEL ROOM - Hotel Santika Bandung",
              "MutationTypeName": "EARNING",
              "ReferenceNo": "999  /11020",
              "Point": 26446,
              "MemberNo": "M0001000050",
              "MemberName": "Sony Shahril Sandi",
              "ValueID": "VX1112",
              "Status": null
          }
      ]
  }
```

### Estimate Transaction

Point API serve end point API to earn or redeem for members.

<table class="table" width="100%">
  <thead>
    <tr>
      <th>End Point</th>
      <th>HTTP Method</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>/point/estimate</td>
      <td>POST</td>
      <td>Estimate how much will be earned/redeemed</td>
    </tr>
  </tbody>
</table>

#### Request Body

<strong>MutasiTypeName</strong> <code>string(10)</code> : Required, "EARNING" or "REDEEM"
<br/><strong>Searchby</strong> <code>string(15)</code> : Required, Paramater to search member would do transaction. The value are "KG_ID" for search using ValueID, "MEMBERNO" for search using MemberNo, "EMAIL" for search using Email, and "CARDNUMBER" for search using Cardnumber
<br/><strong>Id</strong> <code>string(50)</code> : Required, the value to be searched
<br/><strong>IdOutlet</strong> <code>string(10)</code> : Required, The ID of outlet where a member do transaction
<br/><strong>ReferenceNo</strong> <code>string(30)</code> : Required and Unique, The reference no of member transaction
<br/><strong>CreatedDate</strong> <code>datetime</code> : Required,The date and time of member transaction, format <code>yyyy-mm-dd hh:ii:ss</code>
<br/><strong>Amount</strong> <code>numeric</code> : Required, Total amount of member transaction, if <code>J_Point</code> is "0", the point earned/redeem will be calculated using this <code>Amount</code>
<br/><strong>J_Point</strong> <code>numeric</code> : Required, Total point earned/redeem will using this value if it's not filled by "0", the <code>Amount</code> parameter will be ignored
<br/><strong>ExchangeRate</strong> <code>numeric</code> : Required, Exchange conversion for calculating point earn/redeem, if it's not filled by "0", the Exchange Rate from <code>IdOutlet</code> will be ignored
<br/><strong>AmountPoint</strong> <code>numeric</code> : Required, Keep it filled by "0"

>Request body example
``` javascript
  {
    "MutasiTypeName" : "EARNING",
    "Searchby" : "KG_ID", 
    "Id" : "VX1112",
    "IdOutlet" : "MVAPP00001",
    "ReferenceNo" : "12000001818271", 
    "CreatedDate" : "2018-11-11 09:30:00",
    "Amount" : 120000,
    "J_Point" :0,
    "ExchangeRate" : 0,
    "AmountPoint" : 0
  }
```

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from end point
<br/><strong>Data</strong> <code>object</code> : Object of data
<br/><strong>MutationType</strong> <code>string</code> : "EARNING" or "REDEEM"
<br/><strong>TotalPointEstimated</strong> <code>numeric</code> : The total point estimated after transaction
<br/><strong>PointEstimated</strong> <code>numeric</code> : The result of calculated point estimated
<br/><strong>MemberNo</strong> <code>string</code> : The unique id of member
<br/><strong>MemberName</strong> <code>string</code> : The name of member
<br/><strong>ValueID</strong> <code>string</code> : The ValueID of member
<br/><strong>OutletName</strong> <code>string</code> : The Outlet where the transaction made
<br/><strong>ExchangeRate</strong> <code>numeric</code> : The Exchange Rate used to calculated point
<br/>Possible status code:
<br/><code>200</code> : Estimating success
<br/><code>400</code> : Request body doesn't meet specification
<br/><code>422</code> : Estimating failed

>Success(200)
``` javascript
  {
    "Message": "Estimating success",
    "Data": {
        "MutationType": "EARNING",
        "TotalPointEstimated": 1341338,
        "PointEstimated": 4800,
        "TotalTransaction": 120000,
        "MemberNo": "M0001000050",
        "MemberName": "Sony Shahril Sandi",
        "ValueID": "VX1112",
        "OutletName": "MyValue Apps - MyValue Apps",
        "ExchangeRate": 10000,
        "Message": "Estimating success",
        "StatusCode": 1
    }
}
```

### Earning Revision

Point API serve end point API to revise calculated earn point with new calculate point. The API will search ReferenceNo in inputed outlet.

<table class="table" width="100%">
  <thead>
    <tr>
      <th>End Point</th>
      <th>HTTP Method</th>
      <th>Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>/point/revision</td>
      <td>POST</td>
      <td>Earn point revision</td>
    </tr>
  </tbody>
</table>

#### Request Body

<strong>MutasiTypeName</strong> <code>string(10)</code> : Required, "EARNING" or "REDEEM"
<br/><strong>Searchby</strong> <code>string(15)</code> : Required, Paramater to search member would do transaction. The value are "KG_ID" for search using ValueID, "MEMBERNO" for search using MemberNo, "EMAIL" for search using Email, and "CARDNUMBER" for search using Cardnumber
<br/><strong>Id</strong> <code>string(50)</code> : Required, the value to be searched
<br/><strong>IdOutlet</strong> <code>string(10)</code> : Required, The ID of outlet where a member do transaction. key to search transaction
<br/><strong>ReferenceNo</strong> <code>string(30)</code> : Required and Unique, The reference no of member transaction. It will be the key to search transaction
<br/><strong>CreatedDate</strong> <code>datetime</code> : Required,The date and time of member transaction, format <code>yyyy-mm-dd hh:ii:ss</code>
<br/><strong>Amount</strong> <code>numeric</code> : Required, Total amount of member transaction, if <code>J_Point</code> is "0", the point earned/redeem will be calculated using this <code>Amount</code>
<br/><strong>J_Point</strong> <code>numeric</code> : Required, Total point earned/redeem will using this value if it's not filled by "0", the <code>Amount</code> parameter will be ignored
<br/><strong>ExchangeRate</strong> <code>numeric</code> : Required, Exchange conversion for calculating point earn/redeem, if it's not filled by "0", the Exchange Rate from <code>IdOutlet</code> will be ignored
<br/><strong>AmountPoint</strong> <code>numeric</code> : Required, Keep it filled by "0"

>Request body example
``` javascript
  {
    "MutasiTypeName" : "EARNING",
    "Searchby" : "KG_ID", 
    "Id" : "VX1112",
    "IdOutlet" : "MVAPP00001",
    "ReferenceNo" : "12000001818271", 
    "CreatedDate" : "2018-11-11 09:30:00",
    "Amount" : 120000,
    "J_Point" :0,
    "ExchangeRate" : 0,
    "AmountPoint" : 0
  }
```

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from end point
<br/><strong>Data</strong> <code>object</code> : Object of data
<br/>Possible status code:
<br/><code>200</code> : Transaction success
<br/><code>400</code> : Request body doesn't meet specification
<br/><code>422</code> : Transaction failed

>Success(200)
``` javascript
  {
      "Message": "Earning Revision Success",
      "Data": null
  }
```

## API Changelog

### v 1.0.022

- BUG FIX

### v 1.0.021

- Add redeemed history

### v 1.0.020

- Add endpoint point revision

### v 1.0.019

- Change transaction status code while duplicate referenceNo (200/temp)

### v 1.0.018

- Add validation on PointMembership/Post and Point/Post (Transaction)
- Add changelog
- Checking Duplicate Reference No on Transaction
- Add IHub Sentry on Transaction