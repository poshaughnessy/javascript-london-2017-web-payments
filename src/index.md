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

<div class="credit">By [Yeonsang](https://m.flickr.com/#/photos/mountainbread/2557214784)</div>

-- bg-white

[![Payment Request API spec](images/payment-request-api-spec.png)](https://www.w3.org/TR/payment-request/)

--

<!-- TODO replace with live demo and backup image? -->

![Payment Request API demo](images/payment-request-demo-1.gif)

--

```javascript
if (window.PaymentRequest) {
  // We're good to go...
} else {
  // Alas! Use your legacy checkout form...
}
```

--

### TODO update to newer version

```javascript
// A couple of example payment networks (others exist too!)
var methodData = [{supportedMethods: ['visa', 'mastercard']}];
var details = {total: {label: 'Something that costs money', amount: {currency: 'GBP', value: '9.99'}}};
// Show a native Payment Request UI and handle the result
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

### TODO: shipping details etc.
### TODO: browser support
### TODO: Apple Pay for the web?
### TODO: Slide on possible future developments 

--

# Thanks! 🙏

<div class="contact">
  <h3> [@poshaughnessy](https://twitter.com/poshaughnessy) </h3>
  <h3> [@samsunginternet](https://twitter.com/samsunginternet) </h3>
</div>
