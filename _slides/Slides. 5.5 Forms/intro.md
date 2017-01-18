# Forms

---
### Agenda

* Forms in HTML5
* Iron-Forms
* Gold-Elements
* Custom validators

---
### Forms in HTML5
HTML5 added a lot of new features to Forms
- new input types (number, email, color, datetime,...)
- new attributes (minlength, maxlength, required, pattern, autofocus, placeholder, novalidate,...)
- new JavaScript API (checkValidity(), willValidate, validity object,...)
- new pseudo classes for validation (:valid, :invalid,...)

* these features can be used in Polymer 

Example code here:
https://www.html5rocks.com/en/tutorials/forms/html5forms/


---
### Example form HTML5
```
<form role="form" novalidate>
  <label for="inpEmail">Email address</label>
  <input type="email" id="inpEmail" placeholder="Enter email">
</form>
```



---
### Iron-Forms
Polymer has a form type extension
* iron-form

From the docs
> IronForm is an HTML Form element that can validate and submit any custom elements 
that implement Polymer.IronFormElementBehavior, as well as any native HTML elements 

* Polymer.IronFormElementBehavior exposes properties for name and value

---
### Iron-Forms
Iron-Forms
- supports both get and post methods
- uses iron-ajax element to submit the form data to action URL

---
### Iron-Forms
```js
<form is="iron-form" id="form" method="post" action="/form/handler">
  <input is="iron-input" prevent-invalid-input required allowed-pattern="[0-9]"> 
  <paper-input name="name" label="name"></paper-input>
  <input name="address">
  <paper-button raised onclick="submitForm()">Submit</paper-button>
</form>

function submitForm() {
  document.getElementById('form').submit();
}
```

---
<!-- .slide: data-background="url('images/demo.jpg')" --> 
<!-- .slide: class="lab" -->
## Demo time!
Iron-Form

---
### Gold Elements
Elements built for e-commerce use-cases
* gold-cc-cvc-input - Input field for a credit card cvc number
* gold-cc-expiration - Validating input for credit card expiration date
* gold-cc-input - Credit card input field
* gold-email-input - Email input field
* gold-phone-input - Validating input for phone number
* gold-zip-input -Input field for zip code


---
### Gold Elements
Example phone input

```
 <gold-phone-input
          label="France phone number"
          country-code="33"
          phone-number-pattern="X-XX-XX-XX-XX"
          auto-validate>
      </gold-phone-input>
```


---
<!-- .slide: data-background="url('images/demo.jpg')" --> 
<!-- .slide: class="lab" -->
## Demo time!
Gold phone input

---
## Custom Validators
Validation consist of
* Polymer.IronValidatableBehavior
    * implemented by the control that wants custom validation
    * has validator property
* Polymer.IronValidatorBehavior
    * implements the custom validation logic
    * has validatorName property


---
### Using custom validators
imperatively
```html
  <link rel="import" href="../../iron-meta/iron-meta.html">
  <link rel="import" href="cats-only.html">

  var validator = new Polymer.IronMeta({type: 'validator'}).byKey('cats-only');
  ...
  this.valid = validator.validate(event.target.value);
  ...
```

---
### Using custom validators
declaratively
```html
  <link rel="import" href="../../iron-meta/iron-meta.html">
  <link rel="import" href="custom-validator.html">

  <custom-validator id="valid1" validator-name="validator1"></custom-validator>
  <paper-input auto-validate id='input_1' label='Label_1' validator='validator1'></paper-input>
```

---
### Create custom validator
To create a custom validator, you need to
* implement the Polymer.IronValidatorBehavior
* override the validate() method

---
### Example custom validator
```js
Polymer({
    ...
    behaviors: [ Polymer.IronValidatorBehavior],
    validate: function(values) {
        var value = Array.isArray(values) ? values.join('') : values;
        return value.match(/^(c|ca|cat|cats)?$/) !== null; 
    }
  });
```

---
<!-- .slide: data-background="url('images/demo.jpg')" --> 
<!-- .slide: class="lab" -->
## Demo time!
Custom Validation

---
<!-- .slide: data-background="url('images/lab2.jpg')" --> 
<!-- .slide: class="lab" -->
## Lab time!
Create a nicer layout




