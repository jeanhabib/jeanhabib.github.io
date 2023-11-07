---
layout: post
title: 'Using Postman to Test the GitHub User Search API'
date: 2023-11-07 11:48:00 -0300
categories: backend api testing
---

Postman is a popular API testing tool that can be used to test any API (including the GitHub User Search API). Postman provides a variety of features that make it easy to test APIs, including a user-friendly interface, support for a variety of request methods and headers, the ability to save requests and collections of requests, the ability to run collections of requests in sequence, and the ability to generate reports.

Postman also provides a number of features that can be used to make API testing more efficient and effective, such as pre-request scripts, environment variables, assertions, test collections, and the collection runner.

**Benefits of Using Postman for API Testing**

There are a number of benefits to using Postman for API testing, including:

- Improved quality: Postman can help to improve the quality of APIs by detecting and fixing defects early in the development process.
- Reduced risk: Postman can help to reduce the risk of failures in production by identifying potential problems before they occur.
- Increased confidence: Postman can help to increase confidence in releases by ensuring that APIs are ready for production.
- Improved efficiency: Postman can help to improve the efficiency of API testing by providing a variety of features that make testing easier and faster.

**Authenticating Your Requests**

To authenticate your requests to the GitHub User Search API, you can use a fine-grained personal access token (PAT). A fine-grained PAT is a token that can be used to access specific repositories and has specific permissions.

To create a fine-grained PAT, go to your GitHub settings and click on the **Developer settings** tab. Then, click on the **Personal access tokens** section and click on the **Generate new token** button.

Give your token a name and description, and select the `user:read` scope. This scope will allow you to search for users and access their profile pages.

Click on the **Generate token** button and copy your PAT. You can now use your PAT to authenticate your requests to the GitHub User Search API.

**Managing Secret Safe Environment Variables**

Postman environments allow you to store and manage environment variables. Environment variables can be used in requests to store configuration data, such as API keys, tokens, and URLs.

To store your GitHub personal access token in a secret safe environment variable in Postman, follow these steps:

![Postman Environment Variables](/assets/postman-variables.png)

1. Create a new Postman environment.
2. Click on the **Edit** button for the environment.
3. In the **Variables** tab, click on the **Add Variable** button.
4. In the **Name** field, enter a name for your environment variable, such as `GITHUB_PAT`.
5. In the **Value** field, enter your GitHub personal access token.
6. Click on the **Set** button.
7. In the **Type** dropdown menu, select **Secret**.
8. Click on the Save button.

Your GitHub personal access token is now stored in a secret safe environment variable in Postman. You can use this environment variable in your requests to authenticate your requests to the GitHub User Search API.

Postman will replace the \{\{GITHUB_PAT\}\} placeholder with the value of the `GITHUB_PAT` environment variable.

**How to Use Postman to Test the GitHub User Search API**

To test the GitHub User Search API using Postman, you will need to create a Postman account and install the Postman app. Once you have installed Postman, you can follow these steps:

![image tooltip here](/assets/postman-get-request-github-search-users-api.png)

1. Create a new Postman collection.
2. Add a GET request to the collection for the following endpoint:
   > `https://api.github.com/users`
3. Select the created enviropnemnt at top right (if you have never changed Environments dropdown will be 'No Environment')
4. In the **Authorization** header, add the following:

   > Authorization: Bearer \{\{GITHUB\*PAT\}\}

5. Click the **Send** button.
6. Postman will display the response from the GitHub User Search API.
7. Inspect the response to verify that it contains the expected data.

For example, you can use assertions to verify that the status code is 200 and that the response body contains a list of users:

```
  pm.test('Status code is 200', () => {
    pm.response.to.have.status(200);
  });
```

You can also use Postman to test other endpoints in the GitHub User Search API, such as the endpoint for getting a user's profile information or the endpoint for getting a user's repositories:

![GitHub User's Profile](/assets/postman-get-request-github-search-user-detail-api.png)

**Conclusion**

Postman is a powerful tool that can be used to test any API, including the GitHub User Search API. By using Postman, you can improve the quality of your code, reduce the risk of failures, increase confidence in releases, and improve the efficiency of API testing.
