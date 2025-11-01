# Account API

## Instructions

##### 1.Download platform confirmation sample file

```
 	URL: `/v1/cms/account/downloadConfirmationFile`
    Method: GET
    Need token or not: Yes, put the token into the query parameters `auth_token=xxx`
    Download success and return the file
```

##### 2.Upload company license and platform confirmation file for company account

```
	URL: `/v1/cms/account/uploadCompanyLicense`
    Method: POST
    Need token or not: Yes
    Request data: submit form, data inside of form as following
      `organization`: string, company name, required
      `licence`: file input, input name="licence" license, required
      `confirmation`: file input, input name="confirmation" confirmation file, required
    Success and return data: 
   {
   		"error_code": 12000, 
   		"msg": "upload success"
   	}

```

##### 3.Upload personal ID card front and back photo for personal account

```
	URL: `/v1/cms/account/uploadPersonalLicence`
    Method: POST
    Need token or not: Yes
    Request data: submit form, data inside of form as following
      `ID_number`: string, name
      `frontOfID`: file input, input name="frontOfID" front of ID card
      `backOfID`: file input, input name="backOfID" back of ID card
    Success and return data: `
    {
    	"error_code": 12001, 
    	"msg": "upload success"
    }

```

##### 4.Get the company account without real name certificate

```
	URL: `/v1/cms/account/getUnAuthoredCompanyAccount`
    Method: GET
    Need token or not: Yes
    Server return data: Server return data for example
```

##### 5.Get the personal account without real name certificate

```
	URL: `/v1/cms/account/getUnAuthoredPersonalAccount`
    Method: GET
    Need token or not: Yes
    Server return data: Server return data for example
```

##### 6.Download enterprise license

```
 	URL: `/v1/cms/account/:id/downAuthLicence`
    Method: GET
    Need token or not: Yes, joint the token `auth_token=xxx` as the query parameters
    Download success and return file
```

##### 7.Download the confirmation file uploaded by the enterprise

```
	URL: `/v1/cms/account/:id/downAuthConfirmation`
    Method: GET
    Need token or not: Yes, joint the token `auth_token=xxx` as the query parameters
    Download success and return file
```

##### 8.Download ID card front photo

```
	URL: `/v1/cms/account/:id/downloadAuthFrontOfID`
    Method: GET
    Need token or not: Yes, joint the token `auth_token=xxx` as the query parameters
    Download success and return file
```

##### 9.Download ID card back photo

```
	URL: `/v1/cms/account/:id/downloadAuthBackOfID`
    Method: GET
    Need token or not: Yes, joint the token `auth_token=xxx` as the query parameters
    Download success and return file
```

##### 10.Do real name certification for the account

```
	URL: `/v1/cms/account/:id/authorizeAccount`
     Method: POST
     Need token or not: Yes
     Server return data: 
    {
    	"error_code": 12001, 
    	"msg": "upload success"
    }

```

