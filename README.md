# Serverless API Deployment using AWS Lambda and API Gateway

**Student Name:** Anushka Kolapkar\
**Project:** Serverless Function Deployment\
**Platform:** AWS (Amazon Web Services)

------------------------------------------------------------------------

# 1. Project Objective

The objective of this project is to deploy a **serverless API** using
AWS services.\
The project uses:

-   AWS Lambda (to run backend code)
-   Amazon API Gateway (to create a public API endpoint)

The API returns a **colorful HTML webpage** showing that the serverless
function is working.

------------------------------------------------------------------------

# 2. Technologies Used

-   AWS Lambda
-   Amazon API Gateway
-   Node.js 20 Runtime
-   HTML & CSS

------------------------------------------------------------------------

# 3. Step 1 -- Create Lambda Function

1.  Search **Lambda** in AWS Console.
2.  Click **Create Function**
3.  Choose **Author from Scratch**
4.  Enter details:

Function Name:

    api-function

Runtime:

    Node.js 20.x

Click **Create Function**.

### Screenshot

![Lambda Function Created](Lambda%20function%20creted.png)

------------------------------------------------------------------------

# 5. Step 2 -- Add Lambda Code

Open the code editor and paste the following code.

``` javascript
export const handler = async (event) => {
  const html = `
  <!DOCTYPE html>
  <html>
  <head>
  <title>Serverless API</title>
  <style>
  body{
      background: linear-gradient(135deg,#6a11cb,#2575fc);
      height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      font-family:Arial;
  }

  .card{
      background:white;
      padding:40px;
      border-radius:20px;
      box-shadow:0 20px 40px rgba(0,0,0,0.3);
      text-align:center;
      transform: perspective(1000px) rotateY(0deg);
      transition:0.5s;
  }

  .card:hover{
      transform: perspective(1000px) rotateY(10deg) scale(1.05);
  }

  h1{
      color:#2575fc;
  }

  p{
      font-size:18px;
      color:#333;
  }

  .tag{
      background:#6a11cb;
      color:white;
      padding:10px 20px;
      border-radius:20px;
      display:inline-block;
      margin-top:10px;
  }
  </style>
  </head>

  <body>

  <div class="card">
      <h1>Serverless API Working</h1>
      <p>Hello from AWS Lambda</p>
      <p><b>Name:</b> Anushka Kolapkar</p>
      <div class="tag">Deployed Successfully</div>
  </div>

  </body>
  </html>
  `;

  return {
      statusCode: 200,
      headers: {
        "Content-Type": "text/html"
      },
      body: html
  };
};
```

Click **Deploy**.

------------------------------------------------------------------------

# 6. Step 3 -- Test Lambda Function

1.  Click **Test**
   
If successful, the status will show:

    Status: Succeeded

### Screenshot

![Lambda Test](Lambda%20Test%20Result.png)

------------------------------------------------------------------------

# 7. Step 4 -- Create API Gateway

1.  Open **API Gateway**
2.  Click **Create API**
3.  Select **HTTP API**
4.  Click **Build**
5.  Add Integration → Select **Lambda**
6.  Choose your function `api-function`

### Screenshot

![API Gateway](API%20Gateway.png)

------------------------------------------------------------------------

# 8. Step 5 -- Create Route

Create route:

    GET /hello

Connect it with the Lambda function.

### Screenshot

![API Route](API%20GateWay%20Routes.png)

------------------------------------------------------------------------

# 9. Step 7 -- Deploy API

Create stage name:

    prod

After deployment AWS generates an endpoint like:

    https://0zzc0xshvh.execute-api.ap-south-1.amazonaws.com/prod

### Screenshot

![API Endpoint](API%20stages.png)

------------------------------------------------------------------------

# 10. Final Output

Open the API endpoint in browser.

The output shows a **colorful 3D card webpage** indicating the
serverless API is working successfully.

### Screenshot

![Final Output](API%20endpoint%20result.png)

------------------------------------------------------------------------

# 11. Conclusion

This project demonstrates how serverless computing works using AWS.\
The Lambda function executes code without managing servers, and API
Gateway provides a public endpoint for accessing the function.

Serverless architecture reduces infrastructure management and makes
applications scalable.

------------------------------------------------------------------------

