# Guide for Integrating Immutable Passport into Your Application

**Table of Contents**

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Step 1: Creating a simple application or git cloning a repository of the simple application](#step-1-create-or-clone-your-application)
- [Step 2: Registering the application on Immutable Developer Hub](#step-2-register-your-application-on-immutable-developer-hub)
- [Step 3: Installing and Initializing the Passport Client](#step-3-installing-and-initializing-the-passport-client)
- [Step 4: Logging in a User with Passport](#step-4-logging-in-a-user-with-passport)
- [Step 5: Displaying User Information](#step-5-displaying-user-information)
- [Step 6: Logging out a User](#step-6-logging-out-a-user)
- [Step 7: Initiating a Transaction](#step-7-initiating-a-transaction)
- [Conclusion](#conclusion)
- [Additional Resources](#additional-resources)

## Introduction

Integrating Immutable Passport into your application is a pivotal step towards enhancing both security and functionality. Immutable Passport is a powerful solution that simplifies user authentication and enables blockchain transactions. Let's delve into the core concepts of Immutable Passport:

Immutable Passport streamlines user identity verification, creating a seamless experience for registration and login within your application. The process is user-friendly, ensuring that authorized individuals gain access to exclusive features.

The integration empowers your application to initiate blockchain transactions effortlessly. This opens doors to a wide array of blockchain-based functionalities, from asset trading to NFT minting and more.

By adopting Immutable Passport, your application gains the trust and security associated with the Immutable X blockchain. Users can be confident that their assets and data are safeguarded, making it a preferred choice for blockchain applications.

This guide is your key to a successful integration journey. We will cover prerequisites, registration on the Immutable Developer Hub, and the step-by-step implementation of Immutable Passport into your application.

With this, you'll be well-equipped to ensure secure user authentication and unlock the potential of blockchain transactions within your application.

Let's embark on this exciting integration journey!

## Prerequisites

Before you begin, make sure you have the following:

- A simple web application or a repository of a simple application that you want to integrate Immutable Passport into.
- An account on the Immutable Developer Hub (https://developers.immutable.com/).
- Node.js and npm (Node Package Manager) installed on your machine.

## Step 1: Creating a simple application or git cloning a repository of the simple application

You can either create a new simple application or clone a repository of an existing one. For this guide, let's assume you already have a basic application in place.

## Step 2: Registering the application on Immutable Developer Hub

Registering your application on the Immutable Developer Hub is a crucial step to obtain the Client ID, which is required for integrating Immutable Passport. Follow these steps to register your application and obtain the Client ID:

1. Visit the [Immutable Developer Hub](https://developers.immutable.com/).

2. If you already have an account, log in. If not, create an account by clicking the "Sign Up" or "Log In" button and following the registration process.

3. Once you are logged in, navigate to the "My Apps" section in your dashboard. This is where you'll manage your applications.

4. Click on the "Create New App" button to initiate the application registration process. You will be prompted to provide essential information about your application, including its name, description, and website.

5. After providing the necessary information, you'll be presented with a Client ID and Client Secret. These are unique identifiers for your application that you'll use for integration with Immutable Passport.

   **Note**: Keep your Client Secret confidential and do not expose it in your application's front-end code. It should be securely stored on your server.

6. To display the Client ID in your application, you can use the following code:

   ```javascript
   // Display the Client ID in your application
   const clientId = 'YOUR_CLIENT_ID'; // Replace with your actual Client ID
   console.log('Client ID:', clientId);
   ```

   Take note of your Client ID as it is required for initializing the Immutable Passport client in your application.

With the Client ID obtained, you're ready to move on to the next steps for integrating Immutable Passport into your application. This Client ID will be used to configure your Immutable Passport client when you initialize it in your application.

## Step 3: Installing and Initializing the Passport Client

To install Immutable Passport in your application, you can use npm or yarn:

```bash
npm install immutable-passport
# OR
yarn add immutable-passport
```

Now, initialize the Passport client with your Client ID:

```javascript
const { Passport } = require('immutable-passport');

const passport = new Passport({
  clientId: 'YOUR_CLIENT_ID',
  // Other configuration options here
});
```

## Step 4: Logging in a User with Passport

To log in a user using Immutable Passport, you can create a login button in your application that initiates the login process:

```javascript
// In your application code
const loginButton = document.getElementById('login-button');

loginButton.addEventListener('click', () => {
  passport.login()
    .then((response) => {
      // Handle the successful login here
    })
    .catch((error) => {
      // Handle login error here
    });
});
```

## Step 5: Displaying User Information

After a successful login, you can access the ID token, access token, and user's nickname:

```javascript
// Inside the login success handler
const idToken = passport.getIdToken();
const accessToken = passport.getAccessToken();
const nickname = passport.getUser().nickname;

console.log('ID Token:', idToken);
console.log('Access Token:', accessToken);
console.log('Nickname:', nickname);
```

## Step 6: Logging out a User

To log out a user, you can create a logout button and handle the logout action:

```javascript
// In your application code
const logoutButton = document.getElementById('logout-button');

logoutButton.addEventListener('click', () => {
  passport.logout();
  // Redirect the user to a logged-out state in your app
});
```

## Step 7: Initiating a Transaction

You can use Immutable Passport to initiate transactions on the Immutable X blockchain. To send a placeholder string and obtain the transaction hash:

```javascript
passport.initiateTransaction('Your placeholder string here')
  .then((transactionHash) => {
    console.log('Transaction initiated. Transaction Hash:', transactionHash);
  })
  .catch((error) => {
    // Handle transaction initiation error
  });
```

## Conclusion

Congratulations! You've successfully integrated Immutable Passport into your application, empowering users to log in securely and interact with the Immutable X blockchain. This integration enhances the security and functionality of your application, opening up new possibilities for blockchain transactions.

## Additional Resources

For more information and advanced features of Immutable Passport, you can refer to the following resources:

- [Immutable Passport Documentation](https://docs.immutable.com/)
- [Immutable Developer Hub](https://developers.immutable.com/)
- [Immutable X Community](https://community.immutable.com/)

These resources will help you dive deeper into the capabilities of Immutable Passport and address any specific requirements for your application.