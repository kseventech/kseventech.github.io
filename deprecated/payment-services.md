# Payment services :moneybag: :chart_with_upwards_trend: 
Payment service is a third party provider which assists with managing finances so that the developers that made the app don't need to '*reinvent the wheel*', instead they can implement a working service.

So far we came across two payment services and those are Plaid and Stripe and we will be discussing flows of both of the services.

<br/>


## Plaid flow


 Plaid has a flow that consists of several simple steps which start when the user wants to link their bank acc to an app:
 1. Create a link token endpoint *e.g. /link/token/create* , which will be responsible of sending the temporary token to the client-side
 2. Use the generated link token to open a link for the user. This will provide us with a new public_token in onSuccess callback which lasts for about 30mins.
 3. Create a route for exchanging the token for a permanent access token *e.g. /item/public_token/exchange* and store the token for future use on other requests related to that specific item.

<br />


### 1. Link

When it comes to linking your  Plaid api with your client you will see the term *Link* mentioned a lot. With Link, you connect your user's account to the plaid API. Linking actually represents the client-side of the plaid flow where you can do validation, err handling, and multi-factor auth. Plaid provides us with SDK for all commonly used platforms to handle the creation of our client-side link creation. Refer to this [link](https://plaid.com/docs/link/) for more details.
<br />

### 2. Item

Item as a term in plaid can be a bit misleading so it needs to be a bit clarified. Items represent a login at financial institutions. Here is the quote from the Plaid docs 
*'A single end-user of your application might have accounts at different financial institutions, which means they would have multiple different Items.'*
Access tokens that will be used across the whole flow in the backend are actually linked to the banking institutions or items, meaning that each of the tokens represents a specific institution/item and you can use that token for api calls related to that item.
<br />

### 3. Plaid quickstart

Here is a [link](https://github.com/tylernappy/plaid-quickstart-workshop) to a minimal repo where you can get to know plaid flow a bit more. Below are the credentials you can use to test the sandbox.
```
username:user_good
password:pass_good
```
<br/>

### 4. Postman collection

You can also find the Postman collection on this [repo](https://github.com/plaid/plaid-postman) and set up the required sandbox vars and test out all the required endpoints you can integrate into your app.

<br/>
<br/>
<br/>

## Stripe flow with express accounts 

### 1. Overview

Stripe is a service that provides payment management across multiple different platforms and makes it easy to integrate payment logic into any application. Stripe provides many different approaches to payment services like for example in-person payments using stripe terminal but for the purpose of this small doc, we will be talking about **Stripe connect**.
<br>

### 2. Stripe connect

Connect api makes it possible for marketplaces or businesses to payout their clients or alongside Stripe payments api to accept incoming payments from your customers.

<br/>

#### 2.1 Connect accounts

Before you set up Stripe connects you need to determine what kind of account (aka _connected account_) you want to use for the users that will be receiving funds from your platform.
Depending on your needs you can choose between three types of accounts [standard](https://stripe.com/docs/connect/standard-accounts), [express](https://stripe.com/docs/connect/express-accounts) and [custom](https://stripe.com/docs/connect/custom-accounts).
You can check out all the features each of these accounts provides on this [link](https://stripe.com/docs/connect/accounts#choosing-approach). For the purpose of this documentation, we will be talking a bit more about express accounts which is even recommended by Stripe for easier integration.


Stripe provides a lighter version of the dashboard for Express accounts which allows them to manage their personal info and see their payouts. With an express account, you can manage payout schedules programmatically and customize the flow of funds accordingly.
Rocketrides [repo](https://github.com/stripe/stripe-connect-rocketrides) is a good sample repo that represents how the flow with express accounts look like. You can also try the live web app on this link https://rocketrides.io
<br/>

#### 2.2 Linking first connect account

There are several steps that need to be fulfilled so that the client's express account can be linked to the appropriate business account.

1. Customize connect settings page and form to match your business design instead of the default placeholder page. Connect settings page is the first page that the client sees when he starts the linking process of his express account.
2. Creation of an express account
3. Create an account link. Account link gives a single-use url that the platform can use to redirect the client to go through Connect onboarding flow. Bellow are the properties you will be passing to stripe link function and as a result, you would get the object with a URL for the onboarding flow.

```
account
refresh_url
return_url
type = account_onboarding
```

4. Redirect the user to the generated url to proceed with the onboarding flow, but as mentioned due to security this url can only be used once. Make sure to authenticate the user in the application before accessing the url since it holds sensitive information.
5. Handle user returning to the platform. The properties **refresh_url** and **return_url** should be  valid urls since you will be using them during the onboarding flow.
The return_url is used in all cases where you need to redirect users that have completed the onboarding flow and no problems have occurred during the process. On the other refresh_url is used in these scenarios.
 * The link is expired (a few minutes went by since the link was created).
 * The link was already visited (the user refreshed the page or clicked back or forward in the browser).
 * Your platform can no longer access the account.
 * The account has been rejected.

 6. Handle the users that haven't completed onboarding. In some cases user that has finished the onboarding doesn't actually mean is fully complete so make sure to handle those use cases accordingly as mentioned in [here](https://stripe.com/docs/connect/express-accounts#handle-users-not-completed-onboarding).

<br/>

 ### 3. Transfers and payouts

 In order for a connected account to actually receive the funds, there are two steps that need to be done. First off we need to transfer the actual funds from the business account to the connected express account. Basically, we need to create a new transfer object with a valid amount that can actually be paid otherwise we will get *Insufficient Funds* error. You can check out the endpoint structure and more details of the API call on this [link](https://stripe.com/docs/api/transfers/create).
 
 After that's done the user now holds the funds on his account and can perform a manual payout. The same applies for payouts if provided amount of funds isn't valid we will get *Insufficient Funds* error. Here is a [link](https://stripe.com/docs/api/payouts/create) to the endpoint structure for payouts. If for some reason an account has multiple payment source types you will need to specify from which of them the funds need to be drawn.
Keep in mind that for both transfers and payouts you need to specify the amount and currency as those properties are required to fulfill the result.


