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

-- img-with-caption five-images

![Very long form 1](images/very-long-checkout-form-1.png) ![Very long form 2](images/very-long-checkout-form-2.png) ![Very long form 3](images/very-long-checkout-form-3.png) ![Very long form 4](images/very-long-checkout-form-4.png) ![Very long form 5](images/very-long-checkout-form-5.png)

#### &ldquo;I just want to buy some socks&rdquo; 😱

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

## 1. Our first sock sale

<h3 class="pun">&ldquo;Getting our <strong>foot</strong> in the door&rdquo;</h3>

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
  // NB. To support older format, include networks here 
  supportedMethods: ['basic-card'],
  data: {
    // Examples. Others are available too!
    supportedNetworks: ['visa', 'mastercard', 'amex']
  }
}];

var details = {
  total: {
    label: 'Socks', 
    amount: {currency: 'GBP', value: '12.00'}
  }
};
```
--

```javascript
// Show the payment UI and handle the result

new PaymentRequest(methodData, details)
  .show()
  .then(function(uiResult) {
    myPaymentProcessor(uiResult);
  })
  .catch(function(error) {
    myErrorHandler(error);
  });
```

--

<video src="videos/socks-megastore-simple.mp4" controls/>

--

## 2. Adding customisations

<h3 class="pun">&ldquo;Thinking outside the <strong>socks</strong>&rdquo;</h3>

--

```javascript
var details = {
  displayItems: [
    {
      label: "Socks",
      amount: { currency: "GBP", value : "12.00" },
    },
    {
      label: "Loyalty discount",
      amount: { currency: "GBP", value : "-1.00" },
    }
  ],
  total: {
    label: 'Total', 
    amount: {currency: 'GBP', value: '11.00'}
  },
  ...
```
  
--

```javascript
  ...
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
  requestShipping: true
};

new PaymentRequest(methodData, details, options)
  ...
```

--

<video src="videos/socks-megastore-options.mp4" controls/>

-- browser-support three-images

## Browser support

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

-- img-with-header

![Chrome desktop UI](images/chrome-desktop-socks.png)

<h4 class="pun">Good things are <strong>afoot</strong> on the desktop</h4>

<div class="caption">Currently [behind flags](https://twitter.com/poshaughnessy/status/841425232875286529) in Chrome Canary</div>

-- align-top img-with-caption

![Samsung Internet icon on homescreen](images/samsung-internet-beta-phone-blur.png)

[bit.ly/samsung-internet-open-beta](http://bit.ly/samsung-internet-open-beta)

-- img-with-header

![Polykart](images/polykart.png)

<h3 class="pun">&ldquo;A lock, <strong>sock</strong> and barrel example&rdquo;</h3>

<div class="caption">[polykart-credential-payment.appspot.com](https://polykart-credential-payment.appspot.com/)</div>

--

## Further resources


-- socks

# Thanks!

<h3 class="pun">&ldquo;Shoe wants to ask a question?&rdquo;</h3>

<div class="contact">
  <h3> [@poshaughnessy](https://twitter.com/poshaughnessy) </h3>
  <h3> [@samsunginternet](https://twitter.com/samsunginternet) </h3>
</div>

<div class="credit">By [darkmoon](https://www.flickr.com/photos/darkmoon/3572345244)</div>
