# stripepayments_

This TypeScript class is designed to handle payment processing using the Stripe API, specifically focusing on creating checkout sessions. 

**Key Technologies:**

- Stripe
- TypeScript

**Class Structure:**

**Constructor:**

- Stripe Initialization: The constructor initializes the stripeAPI object with a secret key, configuring it with a specific API version.

- Domain URL Configuration: It sets up the domainUrl, which is derived from the baseUrl provided during instantiation. This URL is used to construct return URLs after payment actions are completed (successful or canceled).

**Method:**

- **createCheckoutSession**: interacts with the Stripe API to create a payment checkout session. 
    
**Parameter Verification:** Before proceeding with the session creation,  checks if the necessary parameters (lineItems and customerEmail) are provided. If not, it throws a BadRequestError.

**Session Creation**: Uses Stripe's checkout.sessions.create() method to set up a payment session. The session configuration includes:

- Payment Method Types: Specifies the types of payment methods accepted, in this case, 'card'.

- Mode: Defines the checkout session mode as 'payment', which means the session is used to directly make a payment.
  
- Line Items: The items the customer is purchasing, which include details like price and quantity.
  
- Customer Email: The email address of the customer making the purchase.
  
- Success URL: The URL to which customers are redirected upon successful payment. It includes a session ID placeholder that Stripe replaces dynamically.
  
- Cancel URL: The URL for redirecting if the payment process is canceled.
  
- Shipping Address Collection: Specifies the countries allowed for shipping addresses.
  
- Error Handling: If there's an error during the session creation (such as a network issue or misconfiguration), it logs the error and throws a BadRequestError with a message indicating the inability to create the session. 

**Key Concepts Illustrated:**

- Independent Configuration**: Separating the configuration of the Stripe API and the domain URL from the main business logic helps isolate dependencies and makes the component easier to manage and test.

- Error Management.
