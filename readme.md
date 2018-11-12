# Point API Docs

Point API is a RESTful Web Service served as communication bridge between clients to central of Kompas Gramedia Point Database whose organized by Corporate IT & IS Kompas Gramedia.

## HTTP(S) Request

Point API can be requested through HTTP(S) Request to Point Base URL endpoint. The HTTP(S) Header has to be used to allow proper authentication.

## API Base URL

Development Environment : <code>https://staging-point.myvalue.com/</code><br/>
Production Environment : <code>https://point.myvalue.com/</code>

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

In Membership API, the input and output parameters of the methods will be in JSON format. To accept JSON input and output parameters, you need to add the following HTTP(S) header:

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
      <td>/members</td>
      <td>GET</td>
      <td>Get members data</td>
    </tr>
    <tr>
      <td>/members/search-point</td>
      <td>GET</td>
      <td>Get members data with total point</td>
    </tr>
    <tr>
      <td>/members</td>
      <td>POST</td>
      <td>Store member data</td>
    </tr>
    <tr>
      <td>/members</td>
      <td>PUT</td>
      <td>Update member data</td>
    </tr>
    <tr>
      <td>/members/mapping</td>
      <td>POST</td>
      <td>Mapping members data</td>
    </tr>
    <tr>
      <td>/members/mappingapproval</td>
      <td>POST</td>
      <td>Mapping members data with token</td>
    </tr>
    <tr>
      <td>/outlets</td>
      <td>GET</td>
      <td>Get outlet data</td>
    </tr>
  </tbody>
</table>

### Get Members

Membership API serve end point API to get data members using <code>valueid</code>, <code>memberno</code>, <code>email</code>, and <code>mobilephone</code>.

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
      <td>/members? <code>valueid</code>=&<code>memberno</code>=&<code>email</code>=&<code>mobilephone</code>=</td>
      <td>GET</td>
      <td>Get members data</td>
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
    <td>The MemberNo or CardNumber of members</td>
  </tr>
  <tr>
    <td><code>email</code></td>
    <td>String</td>
    <td>The Email of members</td>
  </tr>
  <tr>
    <td><code>mobilephone</code></td>
    <td>String</td>
    <td>The Mobile Phone of members</td>
  </tr>
</tbody>
</table>

#### Response

This is the response from API:
<br/><strong>PersonSNO</strong> <code>numeric</code> : Unique ID for a member
<br/><strong>ValueID</strong> <code>string</code> : ValueID of member, it will fill with "" (empty string) if a member have not mapped with his ValueID
<br/><strong>TypeName</strong> <code>string</code> : It will fill by "Membership" (you could ignore this value)
<br/><strong>MemberNo</strong> <code>string</code> : Unique ID for member at their memberships
<br/><strong>Email</strong> <code>string</code> : Member's email (all notifications for member will be send to this email address)
<br/><strong>MobilePhone</strong> <code>string</code> : Member's mobile phone (all notifications for member will be send to this mobile phone)
<br/><strong>FirstName</strong> <code>string</code> : Member first name
<br/><strong>LastName</strong> <code>string</code> : Member last name
<br/><strong>FullName</strong> <code>string</code> : Member full name
<br/><strong>BirthDate</strong> <code>date</code> : Member birth date, format <code>yyyy-mm-dd</code>
<br/><strong>CityName</strong> <code>string</code> : City where member came from
<br/><strong>MaritalStatusName</strong> <code>string</code> : Marital status of member
<br/><strong>CardNumber</strong> <code>string</code> : 16 digit card number and not all members have it
<br/><strong>NameOnCard</strong> <code>string</code> : The name written in the card (for member that hold a card)
<br/><strong>ValidDate</strong> <code>date</code> : The date where member has been registered, format <code>yyyy-mm-dd</code>
<br/><strong>ExpiredDate</strong> <code>date</code> : The date where member will be blocked by system, format <code>yyyy-mm-dd</code>
<br/><strong>MembershipSNO</strong> <code>numeric</code> : Membership unique ID
<br/><strong>MembershipName</strong> <code>string</code> : Membership Name
<br/><strong>HomeAddress</strong> <code>string</code> : Member home address
<br/><strong>HomeAddressCity</strong> <code>string</code> : City of member home address
<br/><strong>HomeAddressPostalCode</strong> <code>string</code> : Postal code of member home address
<br/><strong>Active</strong> <code>boolean</code> : "Active" means that member has been mapped their membership with ValueID
<br/><strong>CreatedAt</strong> <code>datetime</code> : The date where member has been registered, format <code>yyyy-mm-ddThh:ii:ss</code>
<br/><strong>TotalPoint</strong> <code>numeric</code> : It will always contain <code>null</code> value.

>Success(200)
``` javascript
	{
	    "Message": "Members Data Found",
	    "Data": [
	        {
	            "PersonSNO": 1,
	            "ValueID": "VX1111",
	            "TypeName": "Membership",
	            "MemberNo": "M0001000001",
	            "Email": "john@doe.com",
	            "MobilePhone": "0812345678",
	            "FirstName": "John",
	            "LastName": "Doe",
	            "FullName": "John Doe",
	            "BirthDate": "1990-08-02",
	            "Gender": "M",
	            "PersonalIdentityNo": "3266123727817898",
	            "BirthPlace": "Bandung",
	            "CityName": "Kota Bandung",
	            "MaritalStatusName": "Single",
	            "CardNumber": "0145000412341234",
	            "NameOnCard": "John Doe",
	            "ValidDate": "2018-01-19",
	            "ExpiredDate": "2070-12-31",
	            "MembershipSNO": 1,
	            "MembershipName": "Santika Important Person",
	            "HomeAddress": "N/A",
	            "HomeAddressCity": "N/A",
	            "HomeAddressPostalCode": "N/A",
	            "Active": true,
	            "CreatedAt": "2018-01-19T11:33:05+07:00",
	            "TotalPoint": null
	        }
	    ]
	}
```

### Get Members with Point

Membership API serve end point API to get data members using <code>cardnumber</code>, <code>memberno</code>, <code>email</code>, and <code>mobilephone</code> with total point.

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
      <td>/members? <code>cardnumber</code>=&<code>memberno</code>=&<code>email</code>=&<code>mobilephone</code>= &<code>showpoint</code>=1&<code>excludemembertype</code>=3</td>
      <td>GET</td>
      <td>Get members data with point</td>
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
    <td><code>cardnumber</code></td>
    <td>String</td>
    <td>The Card Number of members</td>
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
    <td><code>mobilephone</code></td>
    <td>String</td>
    <td>The Mobile Phone of members</td>
  </tr>
  <tr>
    <td><code>showpoint</code></td>
    <td>integer</td>
    <td>"1" to show point, "0" to don't show point, default "1"</td>
  </tr>
  <tr>
    <td><code>excludemembertype</code></td>
    <td>integer</td>
    <td>System would not to find member on this membership. Fill with MembershipSNO</td>
  </tr>
</tbody>
</table>

#### Response

This is the response from API:
<br/><strong>PersonSNO</strong> <code>numeric</code> : Unique ID for a member
<br/><strong>ValueID</strong> <code>string</code> : ValueID of member, it will fill with "" (empty string) if a member have not mapped with his ValueID
<br/><strong>TypeName</strong> <code>string</code> : It will fill by "Membership" (you could ignore this value)
<br/><strong>MemberNo</strong> <code>string</code> : Unique ID for member at their memberships
<br/><strong>Email</strong> <code>string</code> : Member's email (all notifications for member will be send to this email address)
<br/><strong>MobilePhone</strong> <code>string</code> : Member's mobile phone (all notifications for member will be send to this mobile phone)
<br/><strong>FirstName</strong> <code>string</code> : Member first name
<br/><strong>LastName</strong> <code>string</code> : Member last name
<br/><strong>FullName</strong> <code>string</code> : Member full name
<br/><strong>BirthDate</strong> <code>date</code> : Member birth date, format <code>yyyy-mm-dd</code>
<br/><strong>CityName</strong> <code>string</code> : City where member came from
<br/><strong>MaritalStatusName</strong> <code>string</code> : Marital status of member
<br/><strong>CardNumber</strong> <code>string</code> : 16 digit card number and not all members have it
<br/><strong>NameOnCard</strong> <code>string</code> : The name written in the card (for member that hold a card)
<br/><strong>ValidDate</strong> <code>date</code> : The date where member has been registered, format <code>yyyy-mm-dd</code>
<br/><strong>ExpiredDate</strong> <code>date</code> : The date where member will be blocked by system, format <code>yyyy-mm-dd</code>
<br/><strong>MembershipSNO</strong> <code>numeric</code> : Membership unique ID
<br/><strong>MembershipName</strong> <code>string</code> : Membership Name
<br/><strong>HomeAddress</strong> <code>string</code> : Member home address
<br/><strong>HomeAddressCity</strong> <code>string</code> : City of member home address
<br/><strong>HomeAddressPostalCode</strong> <code>string</code> : Postal code of member home address
<br/><strong>Active</strong> <code>boolean</code> : "Active" means that member has been mapped their membership with ValueID
<br/><strong>CreatedAt</strong> <code>datetime</code> : The date where member has been registered, format <code>yyyy-mm-ddThh:ii:ss</code>
<br/><strong>TotalPoint</strong> <code>numeric</code> : Total point of members

>Success(200)
``` javascript
	{
	    "Message": "Members Data Found",
	    "Data": [
	        {
	            "PersonSNO": 1,
	            "ValueID": "VX1111",
	            "TypeName": "Membership",
	            "MemberNo": "M0001000001",
	            "Email": "john@doe.com",
	            "MobilePhone": "0812345678",
	            "FirstName": "John",
	            "LastName": "Doe",
	            "FullName": "John Doe",
	            "BirthDate": "1990-08-02",
	            "Gender": "M",
	            "PersonalIdentityNo": "3266123727817898",
	            "BirthPlace": "Bandung",
	            "CityName": "Kota Bandung",
	            "MaritalStatusName": "Single",
	            "CardNumber": "0145000412341234",
	            "NameOnCard": "John Doe",
	            "ValidDate": "2018-01-19",
	            "ExpiredDate": "2070-12-31",
	            "MembershipSNO": 1,
	            "MembershipName": "Santika Important Person",
	            "HomeAddress": "N/A",
	            "HomeAddressCity": "N/A",
	            "HomeAddressPostalCode": "N/A",
	            "Active": true,
	            "CreatedAt": "2018-01-19T11:33:05+07:00",
	            "TotalPoint": 150000000
	        }
	    ]
	}
```

### Store Member

Membership API serve end point API to store data member

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
      <td>/members</td>
      <td>POST</td>
      <td>Store data member</td>
    </tr>
  </tbody>
</table>

#### Request Body

<strong>Email</strong> <code>string(50)</code> : Required, Email's member
<br/><strong>MobilePhone</strong> <code>string(15)</code> : Required, Mobile phone's member, begin with <code>62</code> or <code>0</code>
<br/><strong>FirstName</strong> <code>string(50)</code> : Required, Member first name
<br/><strong>LastName</strong> <code>string(50)</code> : Member last name
<br/><strong>BirthDate</strong> <code>date</code> : Required, Member birth date, format <code>yyyy-mm-dd</code>
<br/><strong>CitySNO</strong> <code>numeric</code> : Required, Member city
<br/><strong>MembershipSNO</strong> <code>numeric</code> : Required, Membership unique id
<br/><strong>CardNumber</strong> <code>string(20)</code> : Member card number, 16 digit
<br/><strong>NameOnCard</strong> <code>string(20)</code> : Name on member card number
<br/><strong>IDOutlet</strong> <code>string(10)</code> : Required, ID of outlet registered on MyValue
<br/><strong>Gender</strong> <code>char(1)</code> : Required, "M" for male, "F" for female
<br/><strong>PersonalIdentityNo</strong> <code>string(20)</code> : Personal identity no such as KTP/SIM/KITAS
<br/><strong>BirthPlace</strong> <code>string(20)</code> : Member birth place
<br/><strong>MemberNo</strong> <code>string(20)</code> : Fill with "" (empty string), unless you have your own memberno
<br/><strong>Source</strong> <code>string(10)</code> : "ONLINE" will be generate ValueID automatically or "OFFLINE"

>Request body example:
``` javascript
	{
		"Email":"john@indonesia.com",
		"MobilePhone": "081212341234",
		"FirstName": "John",
		"LastName": "Indonesia",
		"BirthDate": "1990-01-01",
		"CitySNO": 1,
		"MembershipSNO": 1,
		"CardNumber": "",
		"NameOnCard": "",
		"IDOutlet":"0101001001",
		"Gender": "M",
		"PersonalIdentityNo": "",
		"BirthPlace": "",
		"MemberNo":"",
		"Source":"OFFLINE"
	}
```

#### Response

This is the response from API:
<br/><strong>PersonSNO</strong> <code>numeric</code> : Unique ID for a member
<br/><strong>ValueID</strong> <code>string</code> : ValueID of member, it will fill with "" (empty string) if a member have not mapped with his ValueID
<br/><strong>TypeName</strong> <code>string</code> : It will fill by "Membership" (you could ignore this value)
<br/><strong>MemberNo</strong> <code>string</code> : Unique ID for member at their memberships
<br/><strong>Email</strong> <code>string</code> : Member's email (all notifications for member will be send to this email address)
<br/><strong>MobilePhone</strong> <code>string</code> : Member's mobile phone (all notifications for member will be send to this mobile phone)
<br/><strong>FirstName</strong> <code>string</code> : Member first name
<br/><strong>LastName</strong> <code>string</code> : Member last name
<br/><strong>FullName</strong> <code>string</code> : Member full name
<br/><strong>BirthDate</strong> <code>date</code> : Member birth date, format <code>yyyy-mm-dd</code>
<br/><strong>CityName</strong> <code>string</code> : City where member came from
<br/><strong>MaritalStatusName</strong> <code>string</code> : Marital status of member
<br/><strong>CardNumber</strong> <code>string</code> : 16 digit card number and not all members have it
<br/><strong>NameOnCard</strong> <code>string</code> : The name written in the card (for member that hold a card)
<br/><strong>ValidDate</strong> <code>date</code> : The date where member has been registered, format <code>yyyy-mm-dd</code>
<br/><strong>ExpiredDate</strong> <code>date</code> : The date where member will be blocked by system, format <code>yyyy-mm-dd</code>
<br/><strong>MembershipSNO</strong> <code>numeric</code> : Membership unique ID
<br/><strong>MembershipName</strong> <code>string</code> : Membership Name
<br/><strong>HomeAddress</strong> <code>string</code> : Member home address
<br/><strong>HomeAddressCity</strong> <code>string</code> : City of member home address
<br/><strong>HomeAddressPostalCode</strong> <code>string</code> : Postal code of member home address
<br/><strong>Active</strong> <code>boolean</code> : "Active" means that member has been mapped their membership with ValueID
<br/><strong>CreatedAt</strong> <code>datetime</code> : The date where member has been registered, format <code>yyyy-mm-ddThh:ii:ss</code>
<br/><strong>TotalPoint</strong> <code>numeric</code> : null

>Success(201)
``` javascript
	{
	    "Message": "Saving data success. ",
	    "Data": [
	        {
	            "PersonSNO": 1,
	            "ValueID": "VX1111",
	            "TypeName": "Membership",
	            "MemberNo": "M0001000001",
	            "Email": "john@doe.com",
	            "MobilePhone": "0812345678",
	            "FirstName": "John",
	            "LastName": "Doe",
	            "FullName": "John Doe",
	            "BirthDate": "1990-08-02",
	            "Gender": "M",
	            "PersonalIdentityNo": "3266123727817898",
	            "BirthPlace": "Bandung",
	            "CityName": "Kota Bandung",
	            "MaritalStatusName": "Single",
	            "CardNumber": "0145000412341234",
	            "NameOnCard": "John Doe",
	            "ValidDate": "2018-01-19",
	            "ExpiredDate": "2070-12-31",
	            "MembershipSNO": 1,
	            "MembershipName": "Santika Important Person",
	            "HomeAddress": "N/A",
	            "HomeAddressCity": "N/A",
	            "HomeAddressPostalCode": "N/A",
	            "Active": true,
	            "CreatedAt": "2018-01-19T11:33:05+07:00",
	            "TotalPoint": null
	        }
	    ]
	}
```

Possibles status code:
<br/><code>201</code> : Member created
<br/><code>404</code> : Outlet not found/City not found/Outlet can't do acquisition
<br/><code>409</code> : Member with email/memberno has been registered before/Creating member failed
<br/><code>422</code> : Request body doesn't meet specification

### Update Member

Membership API serve end point API to update data member

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
      <td>/members</td>
      <td>PUT</td>
      <td>Update data member</td>
    </tr>
  </tbody>
</table>

#### Request Body

<strong>Email</strong> <code>string(50)</code> : Required, Email's member
<br/><strong>MobilePhone</strong> <code>string(15)</code> : Required, Mobile phone's member, begin with <code>62</code> or <code>0</code>
<br/><strong>FirstName</strong> <code>string(50)</code> : Required, Member first name
<br/><strong>LastName</strong> <code>string(50)</code> : Member last name
<br/><strong>BirthDate</strong> <code>date</code> : Required, Member birth date, format <code>yyyy-mm-dd</code>
<br/><strong>CitySNO</strong> <code>numeric</code> : Required, Member city
<br/><strong>MembershipSNO</strong> <code>numeric</code> : Required, Membership unique id
<br/><strong>CardNumber</strong> <code>string(20)</code> : Member card number, 16 digit
<br/><strong>NameOnCard</strong> <code>string(20)</code> : Name on member card number
<br/><strong>IDOutlet</strong> <code>string(10)</code> : Required, ID of outlet registered on MyValue
<br/><strong>Gender</strong> <code>char(1)</code> : Required, "M" for male, "F" for female
<br/><strong>PersonalIdentityNo</strong> <code>string(20)</code> : Personal identity no such as KTP/SIM/KITAS
<br/><strong>BirthPlace</strong> <code>string(20)</code> : Member birth place
<br/><strong>MemberNo</strong> <code>string(20)</code> : Key for updating data

>Request body example:
``` javascript
	{
		"Email":"john@indonesia.com",
		"MobilePhone": "081212341234",
		"FirstName": "John",
		"LastName": "Doe",
		"BirthDate": "1990-01-01",
		"CitySNO": 1,
		"MembershipSNO": 1,
		"CardNumber": "",
		"NameOnCard": "",
		"IDOutlet":"0101001001",
		"Gender": "M",
		"PersonalIdentityNo": "",
		"BirthPlace": "",
		"MemberNo":"M0001000001"
	}
```

#### Response

This is the response from API:
<br/><strong>PersonSNO</strong> <code>numeric</code> : Unique ID for a member
<br/><strong>ValueID</strong> <code>string</code> : ValueID of member, it will fill with "" (empty string) if a member have not mapped with his ValueID
<br/><strong>TypeName</strong> <code>string</code> : It will fill by "Membership" (you could ignore this value)
<br/><strong>MemberNo</strong> <code>string</code> : Unique ID for member at their memberships
<br/><strong>Email</strong> <code>string</code> : Member's email (all notifications for member will be send to this email address)
<br/><strong>MobilePhone</strong> <code>string</code> : Member's mobile phone (all notifications for member will be send to this mobile phone)
<br/><strong>FirstName</strong> <code>string</code> : Member first name
<br/><strong>LastName</strong> <code>string</code> : Member last name
<br/><strong>FullName</strong> <code>string</code> : Member full name
<br/><strong>BirthDate</strong> <code>date</code> : Member birth date, format <code>yyyy-mm-dd</code>
<br/><strong>CityName</strong> <code>string</code> : City where member came from
<br/><strong>MaritalStatusName</strong> <code>string</code> : Marital status of member
<br/><strong>CardNumber</strong> <code>string</code> : 16 digit card number and not all members have it
<br/><strong>NameOnCard</strong> <code>string</code> : The name written in the card (for member that hold a card)
<br/><strong>ValidDate</strong> <code>date</code> : The date where member has been registered, format <code>yyyy-mm-dd</code>
<br/><strong>ExpiredDate</strong> <code>date</code> : The date where member will be blocked by system, format <code>yyyy-mm-dd</code>
<br/><strong>MembershipSNO</strong> <code>numeric</code> : Membership unique ID
<br/><strong>MembershipName</strong> <code>string</code> : Membership Name
<br/><strong>HomeAddress</strong> <code>string</code> : Member home address
<br/><strong>HomeAddressCity</strong> <code>string</code> : City of member home address
<br/><strong>HomeAddressPostalCode</strong> <code>string</code> : Postal code of member home address
<br/><strong>Active</strong> <code>boolean</code> : "Active" means that member has been mapped their membership with ValueID
<br/><strong>CreatedAt</strong> <code>datetime</code> : The date where member has been registered, format <code>yyyy-mm-ddThh:ii:ss</code>
<br/><strong>TotalPoint</strong> <code>numeric</code> : null

>Success(200)
``` javascript
	{
	    "Message": "Updating data success. ",
	    "Data": [
	        {
	            "PersonSNO": 1,
	            "ValueID": "VX1111",
	            "TypeName": "Membership",
	            "MemberNo": "081212341234",
	            "Email": "john@indonesia.com",
	            "MobilePhone": "0812345678",
	            "FirstName": "John",
	            "LastName": "Doe",
	            "FullName": "John Doe",
	            "BirthDate": "1990-08-02",
	            "Gender": "M",
	            "PersonalIdentityNo": "",
	            "BirthPlace": "",
	            "CityName": "Kota Bandung",
	            "MaritalStatusName": "Single",
	            "CardNumber": "",
	            "NameOnCard": "",
	            "ValidDate": "2018-01-19",
	            "ExpiredDate": "2070-12-31",
	            "MembershipSNO": 1,
	            "MembershipName": "Santika Important Person",
	            "HomeAddress": "N/A",
	            "HomeAddressCity": "N/A",
	            "HomeAddressPostalCode": "N/A",
	            "Active": true,
	            "CreatedAt": "2018-01-19T11:33:05+07:00",
	            "TotalPoint": null
	        }
	    ]
	}
```

Possibles status code:
<br/><code>200</code> : Update member success
<br/><code>404</code> : Member not found/Outlet not found/City not found/Outlet can't do acquisition
<br/><code>422</code> : Request body doesn't meet specification

### Mapping Members

Membership API serve end point API to mapping multiple data members with the same email, with MyValue membership.

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
      <td>/members/mapping</td>
      <td>POST</td>
      <td>Mapping members data</td>
    </tr>
  </tbody>
</table>

#### Request Body

<strong>ValueID</strong> <code>string(6)</code> : ValueID where member will be mapped to
<br/><strong>members</strong> <code>array of string(20)</code> : List of all MemberNo/CardNumber will be mapped to ValueID

>Request body example:
``` javascript
{
	"ValueID": "VX1111",
	"members":[
		"0145000412341234"
		]
}
```

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from API response
<br/><strong>Data</strong> <code>object</code> : Object of data
<br/><strong>Code</strong> <code>numeric</code> : Status code of mapping result <code>99</code> for success mapping, <code>50</code> mapping failed and send token
<br/><strong>KGCustId</strong> <code>string</code> : ValueID where member has been mapped to
<br/><strong>persons</strong> <code>array of members</code> : List of members has been mapped with <strong>KGCustId</strong>
<br/><strong>EmailSentToken</strong> <code>string</code> : Token mapping sent to this email address
<br/><strong>MobilePhoneSentToken</strong> <code>string</code> : Token mapping sent to this mobile phone
<br/><strong>MappingId</strong> <code>numeric</code> : Mapping unique id
<br/><br/>Possibles status code:
<br/><code>200</code> : Mapping member success
<br/><code>404</code> : Member not found/ValueID not found
<br/><code>409</code> : Send token to Email/Mobile Phone
<br/><code>422</code> : Mapping failed

>Success(200)
``` javascript
{
    "Message": "Mapping members success.",
    "Data": {
        "Code": 99,
        "PersonMapped": {
            "KGCustId": "VX1111",
            "persons": [
                {
                    "PersonSNO": 1,
		            "ValueID": "VX1111",
		            "TypeName": "Membership",
		            "MemberNo": "081212341234",
		            "Email": "john@indonesia.com",
		            "MobilePhone": "0812345678",
		            "FirstName": "John",
		            "LastName": "Doe",
		            "FullName": "John Doe",
		            "BirthDate": "1990-08-02",
		            "Gender": "M",
		            "PersonalIdentityNo": "",
		            "BirthPlace": "",
		            "CityName": "Kota Bandung",
		            "MaritalStatusName": "Single",
		            "CardNumber": "",
		            "NameOnCard": "",
		            "ValidDate": "2018-01-19",
		            "ExpiredDate": "2070-12-31",
		            "MembershipSNO": 1,
		            "MembershipName": "Santika Important Person",
		            "HomeAddress": "N/A",
		            "HomeAddressCity": "N/A",
		            "HomeAddressPostalCode": "N/A",
		            "Active": true,
		            "CreatedAt": "2018-01-19T11:33:05+07:00",
		            "TotalPoint": null
                }
            ]
        },
        "EmailSentToken": null,
        "MobilePhoneSentToken": null,
        "MappingId": 200589
    }
}
```

>Failed mapping (409)
``` javascript
{
    "Message": "Mapping members failed. Mapping token has been sent to your email/mobile phone.",
    "Data": {
        "Code": 50,
        "PersonMapped": null,
        "EmailSentToken": "john@indonesia.com",
        "MobilePhoneSentToken": "081212341234",
        "MappingId": 200588
    }
}
```

### Mapping Member with token

Membership API serve end point API to mapping with token (if mapping member failed, it will send a token)

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
      <td>/members/mappingapproval</td>
      <td>POST</td>
      <td>Mapping members data with token</td>
    </tr>
  </tbody>
</table>

#### Request Body

<strong>ValueID</strong> <code>string(6)</code> : ValueID where member will be mapped to
<br/><strong>MemberNo</strong> <code>string(20)</code> : MemberNo/CardNumber will be mapped to ValueID
<br/><strong>Token</strong> <code>string(6)</code> : Token mapping sent to member's email/mobilephone

>Request body example:
``` javascript
{
	"ValueID": "VX1111",
	"MemberNo": "0145000412341234",
	"Token": "123456"
}
```

#### Response

This is the response from API:
<br/><strong>Message</strong> <code>string</code> : Message from API response
<br/><br/>Possibles status code:
<br/><code>200</code> : Mapping member success
<br/><code>404</code> : Member not found/ValueID not found/Data mapping not found
<br/><code>422</code> : Wrong token/Token expired

>Success (200)
``` javascript
{
	"Message" : "Mapping member success"
}
```

### Get Outlet

Membership API serve end point API to get data outlet using <code>idoutlet</code>

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
      <td>/outlets?<code>idoutlet</code>=</td>
      <td>GET</td>
      <td>Get outlet data</td>
    </tr>
  </tbody>
</table>

#### Request Parameters

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
    <td><code>idoutlet</code></td>
    <td>String</td>
    <td>ID Outlet registered in MyValue</td>
  </tr>
</tbody>
</table>

#### Response

This is the response from API:
<br/><strong>IDOutlet</strong> <code>string</code> : ID Outlet
<br/><strong>MerchantName</strong> <code>string</code> : Merchant Name of Outlet
<br/><strong>OutletName</strong> <code>string</code> : Outlet name
<br/><strong>Address</strong> <code>string</code> : Outlet address
<br/><strong>Telephone</strong> <code>string</code> : Outlet phone
<br/><strong>IsAcquisition</strong> <code>boolean</code> : Status outlet can do acquisition
<br/><strong>IsEarning</strong> <code>boolean</code> : Status outlet can do earning
<br/><strong>IsRedeem</strong> <code>boolean</code> : Status outlet can do redeem

>Success (200)
``` javascript
{
    "Message": "Data Outlet Found",
    "Data": {
        "IDOutlet": "0101001001",
        "MerchantName": "Hotel Santika Bandung",
        "OutletName": "HOTEL ROOM",
        "Address": "HOTEL ROOM",
        "Telephone": "0229000000",
        "IsAcquisition": true,
        "IsEarning": true,
        "IsRedeem": true
    }
}
```

## API Changelog

### v 1.0.015

- Add Transaction method while generating member
- Add validation on Store Member, Update Member, Mapping Member
- Add changelog
- Optimize store member
- BUG FIX - Search member validation

### v 1.0.014

- HOTFIX - Member Generator