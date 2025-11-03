# Vehicle HUB Platform API Calling Guide

1. The test interface is the passenger flow statistics interface.

2. The testing tool is Postman.

3. The test control card is Y08.

##### I. Control Card Platform Activation Procedure

1. First, log in to the platform and click “Download vehicle access certificate” in the top-right corner. Once the certificate has been downloaded,

![image-20250913085311833](./Images/13.png)

2. Open LEDOK, select the control card, and proceed with configuration operations.

![image-20250913085444142](./Images/14.png)

##### II. Getting the Platform Token

Request Method******

**Request Header Parameters**

| Parameter Name | Example Value                      | Parameter Type | Required | Parameter Description |
| -------------- | ---------------------------------- | -------------- | -------- | --------------------- |
| authorization  | Bearer eyJhbGciOiJIUzI1NiIsInR5cCI | string         | Yes      | -                     |

Upon entering the platform to execute a command, the console will display the Token. This Token is time-sensitive and must be reacquired once it expires.

![image-20250913085719721](./Images/15.png)

##### III. Calling API Commands

1. Next, we shall open the API documentation and use the passenger flow statistics interface as our test case.

![image-20250913090204016](./Images/16.png)

  2.  Subsequently, launch our testing tool and follow the documentation to retrieve passenger flow data for control card Y08 during 9th to 12th November.

 ![image-20250913090614532](./Images/17.png)

3. After completing the access path and request method as per the documentation, click Send to receive the response.

![image-20250913090736939](./Images/18.png)

##### IV. Common Issues When Calling APIs

1. What should I do if I cannot locate the path?

​     You can query the path via the platform console. Follow these steps:

 ![image-20250913091044598](./Images/19.png)

2. By querying the platform command, we can view the request path and request method.