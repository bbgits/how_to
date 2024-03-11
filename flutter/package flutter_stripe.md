# flutter_stripe package

## implementation using firebase functions

##### get tools:

`flutter pub add flutter_stripe`  / adds flutter_stripe to dependencies

`flutter pub add flutter_stripe_web` / adds flutter_stripe_web to dependencies

`flutter pub get` / installs and resolves dependencies

##### set up cloud function

1. From terminal, login to firebase: `firebase login`

2. Initiatialize:
   
   1. run `firebase init`, 
   
   2. select 'Functions: 
   
   3. select JavaScript as language
   
   4. choose 'no' for ESLint
   
   5. choose 'Y' to install NPM dependencies now

3. Navigate into the 'functions' folder that was created: `cd functions`

4. Install the stripe NPM package here: `npm install stripe -save`

### Trying wit Web Flow..

#### Steps:

1. Set up Stripe CLI in terminal,

2. Create Stripe starter project using CLI

3. Create Stripe Payment element using starter project

4. Create Stripe Google Cloud Function that works as backend (steps 1-3)

5. Verify backend functionality using Postman

6. Connect Flutter Frontent to Cloud Function

7. Clean Up Payment Sheep and Add Togles for Variable Pricing

8. Connect to current "Build a Report" flow

#### 1. Stripe CLI

Set up Stripe CLI using terminal (instructions [here](https://stripe.com/docs/stripe-cli) for Linux using APT):

1. **Add Stripe CLI's GPG key to the apt sources keyring:** `curl -s https://packages.stripe.dev/api/security/keypair/stripe-cli-gpg/public | gpg --dearmor | sudo tee /usr/share/keyrings/stripe.gpg`

2. **Add apt repository to apt sources list:** `echo "deb [signed-by=/usr/share/keyrings/stripe.gpg] https://packages.stripe.dev/stripe-cli-debian-local stable main" | sudo tee -a /etc/apt/sources.list.d/stripe.list`

3. **Update package list:** `sudo apt update`

4. **Instal CLI**`sudo apt install stripe`

5. **Log in to CLI:** `stripe login` and follow prompts

6. 

#### 2. Create starter project (to practice client/server/payment element)

Followed [this youtube video]([How to integrate Stripe&#39;s Payment Element - YouTube](https://www.youtube.com/watch?v=MfFCg7kYCa4)[How to integrate Stripe&#39;s Payment Element - YouTube](https://www.youtube.com/watch?v=MfFCg7kYCa4)).

*Set up Starter Project*

1. First, create 'developer-officer-hours' starter project: `stripe samples create starter` After running script, follow prompts to select node as language.

2. Navigate into new project folder `cd starter`

3. Navigate into server folder `cd server`

4. Install npm packages `npm install`

*Create Route Handler to retrieve publishable key*

Add to server.js so that publishable key is returned:

```
app.get("/publishable-key"), (req,res) => {
  res.json({
    publishableKey: process.env.STRIPE_PUBLISHABLE_KEY
  })
}
```

*Create a Payment Intent, and retur$n$ its Client Secret*

Add to server.js:

```
app.post("/secret", async (req,res) => {
  const paymentIntent = await stripe.paymentIntents.create({
    amount:2999,
    currency: "eur",
    payment_method_types: ["card"],
  });
  res.json({clientSecret: paymentIntent.client_secret})
});
```

*In Front end, "HTML"*

Needed to add several functions in a script tag:

<script>

// Run this script when button is pressed:

document.addEventListener("DOMContentLoaded", async() => {

// 1. Fetch the Publishable Key

const { publishableKey } = await fetch("/publishable-key").then(r => r.json())



// 2. Initialize Sripe.js

console.log("initializing stripe...");

const stripe = Stripe(publishableKey);



// 3. Fetch the client secret

console.log("fetching client secret...")

const { clientSecret } = await fetch("/secret",{ method:"POST" }).then(

(r) =>r.json()

);

console.log("PRINTING JSON:");

console.log(clientSecret);

// 4. Create and Mount Payment Element

console.log("Creating payment element...");

const element = await stripe.elements({ clientSecret }); // ** NEEDED UPDATE **

const paymentElement = await element.create("payment", { clientSecret }); // create payment element

await paymentElement.mount("#payment-element"); // mount to front-end using html ID tag



// 5. Add an Event Listener and Submit Payment

const form = document.querySelector("#payment-form"); // select form

// const form_bool = document.getElementByID("#payment-form");

if (form) {

await form.addEventListener("submit", async (event) => { // add listener

event.preventDefault();

await stripe.confirmPayment({

element: paymentElement,

confirmParams: {

return_url: `localhost:4242/complete`,

}

})})}

})



</script>

### Stripe Cloud Function with Payment Element...

Next, 

1. creat starter p
