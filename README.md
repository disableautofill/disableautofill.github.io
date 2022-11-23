# Disable Chrome autofill, autocomplete

It has been a long issue about autofill and autocomplete functions caused by Web browsers such as Chrome, Firefox, and others when we don't want the login form or sign-up form auto-filled.

The `autocomplete` attribute set to `off` has been not working for many years but it is still mentioned in lofs of outdated documents and discussion threads. The `new-password` value may work with Firefox but not all versions, in other words - it is not a solution at all.

The problems, at heart, are that Web browsers remember what you fill, specifically password, and fill in the form automatically for you - even you don't want it.

## Tips to avoid autofill

These tips you can try:

### CSS 

Use `text` instead of `password` in `type` attribute of the input, and them add `-webkit-text-security: disc` CSS syntax in the `style` attribute. 

HTML: [JSFiddle](https://jsfiddle.net/terrylinooo/92daLrhz/)
```html
<input type="text" style="-webkit-text-security: disc" />
```

#### Pros
- Simple.

#### Cons
- Not cross-browsers solution.

### JavaScript

Remove the `name` attribute for the visible password field, and copy the value to the hidden value when user is typing.

```html
<input id="hide-password" name="password" type="hidden" />
<input id="display-password" type="password" />
```
JavaScript: [JSFiddle](https://jsfiddle.net/terrylinooo/cLthqfdj/)
```javascript
  const displayInput = document.querySelector('#display-password');
  const hiddenInput = document.querySelector('#hide-password');
  displayInput.addEventListener('keyup', (e) => {
    hiddenInput.value = e.target.value;
  });
```

#### Pros
- Works.

#### Cons
- Need to write JavaScript code yourself.
- Chrome might ask you confirm saving password in browser for further use.
- Chorme still ask you to auto complete the password field.

### JavaScript Library

Checkout disableautofill.js
GitHub: https://github.com/terrylinooo/disableautofill.js

#### Pros
- Easy to use.
- Provide callback for validating the form submission.

#### Cons
- Need to write JavaScript code yourself.
