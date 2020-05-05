# Pinax Stripe

Pinax Stripe is a Pinax package that provides integration with Stripe for payment processing. Pinax Stripe is one of the most popular apps in the Pinax ecosystem.

## Pinax Stripe Signals and Receivers

In addition to including Django User Accounts receivers, the Pinax Stripe starter project ```receivers.py``` file includes an additional ```customers``` action.

```python
from pinax.stripe.actions import customers


@receiver(user_signed_up)
def handle_user_signed_up(sender, **kwargs):
    log(
        user=kwargs.get("user"),
        action="USER_SIGNED_UP",
        extra={}
    )
    customers.create(kwargs.get("user"))
```

## Pinax Stripe JavaScript

### Global ```stripe.js```

<!--
https://github.com/pinax/pinax-starter-projects/blob/<project_name>/static/src/js/apps/pinax-stripe.js
-->

```javascript
/* global Stripe */
// Requires <script src="https://js.stripe.com/v3/"></script> to be included in your page

const loadStripeElements = () => {
  const form = document.querySelector('form[data-stripe-key]');
  if (form === null) {
    return;
  }
  const key = form.getAttribute('data-stripe-key');
  if (key) {
    if (Stripe === undefined) {
      throw Error('pinax-stripe integration requires that https://js.stripe.com/v3/ is loaded in a script tag in your page.');
    }
    const stripe = Stripe(key);
    const elements = stripe.elements();
    const card = elements.create('card');
    const errorElement = document.getElementById(form.getAttribute('data-card-errors-id'));
    card.mount(`#${form.getAttribute('data-card-mount-id')}`);

    card.addEventListener('change', (event) => {
      if (event.error) {
        errorElement.textContent = event.error.message;
      } else {
        errorElement.textContent = '';
      }
    });

    // Handle form submission
    form.addEventListener('submit', (event) => {
      event.preventDefault();

      stripe.createToken(card).then((result) => {
        if (result.error) {
          // Inform the user if there was an error
          errorElement.textContent = result.error.message;
        } else {
          const tokenInput = document.createElement('input');
          tokenInput.setAttribute('type', 'hidden');
          tokenInput.setAttribute('name', 'stripeToken');
          tokenInput.setAttribute('value', result.token.id);
          form.appendChild(tokenInput);
          form.submit();
        }
      });
    });
  }
};

export default loadStripeElements;
```
