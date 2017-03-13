title: Web Payments
output: public/index.html
theme: peter-theme
controls: false

-- card-closeup

# Web Payments
## and the future of online checkouts

<h2 class="emoji">💳</h2>

### JavaScript London, March 2017

<div class="contact">
  <p>Peter O'Shaughnessy</p>
  <p>[@poshaughnessy](https://twitter.com/poshaughnessy)</p>
</div>

-- align-top img-with-caption

![Samsung Internet icon on homescreen](images/samsung-internet-phone-blur.png)

[@samsunginternet](https://twitter.com/samsunginternet)

-- img-with-caption five-images

![Very long form 1](images/very-long-checkout-form-1.png) ![Very long form 2](images/very-long-checkout-form-2.png) ![Very long form 3](images/very-long-checkout-form-3.png) ![Very long form 4](images/very-long-checkout-form-4.png) ![Very long form 5](images/very-long-checkout-form-5.png)

### 😱

-- img-with-caption

![Cart abandoment reasons](images/cart-abandonment-reasons-trans.png)

<div class="caption">[baymard.com/lists/cart-abandonment-rate](https://baymard.com/lists/cart-abandonment-rate)</div>

-- img-with-caption what-if

## What if your browser could help?

* <strong><em>For users:</em></strong> consistent & secure experience
* <strong><em>For web devs:</em></strong> ready-to-use UI!

<div class="credit">By [Marc Falardeau](https://www.flickr.com/photos/49889874@N05/5645164344)</div>

-- bg-white

[![Payment Request API spec](images/payment-request-api-spec.png)](https://www.w3.org/TR/payment-request/)

--

![Payment Request](images/payment-request.png)

--

```javascript
if (window.PaymentRequest) {
  // We're good to go...
} else {
  // Alas! Use your legacy checkout form...
}
```

--

```javascript
var methodData = var methodData = [{
  supportedMethods: ['basic-card'],
  data: {
    supportedNetworks: ['visa', 'mastercard', 'amex'],
    supportedTypes: ['debit', 'credit']
  }
}];

var details = {
  total: {label: 'Socks', amount: {currency: 'GBP', value: '12.00'}}
};
```
--

```javascript
// Show the payment UI and handle the result

new PaymentRequest(methodData, details)
  .show()
  .then(function(uiResult) {
    processPayment(uiResult);
  })
  .catch(function(error) {
    handlePaymentError(error);
  });
```

--

<!-- TODO replace with live demo and backup image? -->

![Payment Request API demo](images/payment-request-demo-1.gif)

--

### Options

```javascript
var details = {
  total: {label: 'Socks', amount: {currency: 'GBP', value: '12.00'}},
  shippingOptions: [
    {
      id: 'standard',
      label: 'Standard shipping',
      amount: {currency: 'GBP', value: '1.50'},
      selected: true
    }
  ]
};
```

--

```javascript
var options = {
  requestPayerName: true,
  requestPayerEmail: true,
  requestPayerPhone: true,
  requestShipping: true,
  shippingType: 'delivery'
};

var paymentRequest = new PaymentRequest(methodData, details, options);
```

--


<!-- TODO replace with live demo and backup image? -->

![Payment Request API demo](images/payment-request-demo-2.gif)

-- browser-support three-images

<table>
  <tr>
    <td>![Chrome](images/chrome.png)</td>
    <td>![Samsung Internet](images/sbrowser5.0.png)</td>
    <td>![Edge Preview](images/edge.png)</td>
  </tr>
  <tr>
    <td>Chrome for Android v53+</td>
    <td>Samsung Internet v5.0+</td>
    <td>Edge Preview</td>
  </tr>
</table>

<div class="caption">[caniuse.com/#feat=payment-request](http://caniuse.com/#feat=payment-request)</div>

--

### TODO: Mention Apple Pay for the web for comparison?
### TODO: Slide on possible future developments 

--

# Thanks! 🙏

<div class="contact">
  <h3> [@poshaughnessy](https://twitter.com/poshaughnessy) </h3>
  <h3> [@samsunginternet](https://twitter.com/samsunginternet) </h3>
</div>
