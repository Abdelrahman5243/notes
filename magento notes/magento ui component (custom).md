### To push message alert 

![[Pasted image 20250722154649.png]]
```js
var dataPost = $(document).data('mageDataPost');

if (dataPost) {

dataPost.displayMessages([{

type: 'info',

text: 'Button was clicked!'

}]);

}

```

---
### To make messages

![[Pasted image 20250722160322.png]]

```js
<script>

require(['jquery','Magento_Customer/js/customer-data'], function ($,customerData) {

$(document).ready(function () {

setTimeout(() => {

// First ensure the messages section is initialized

var messagesData = customerData.get('messages');

if (typeof messagesData === 'function') {

var existing = messagesData() || {};

existing.messages = existing.messages || [];

existing.messages.push({

type: 'success',

text: 'This is a safe message!'

});

customerData.set('messages', existing);

} else {

console.error('customerData.get("messages") is not a function');

}

}, 6000);

});

});

</script>

```

| `type`                   | Appearance    | Use Case Example                      |
| ------------------------ | ------------- | ------------------------------------- |
| `'success'`              | ✅ Green box   | Operation completed, success feedback |
| `'error'`                | ❌ Red box     | Something failed                      |
| `'warning'` <br>`'info'` | ⚠️ Orange box | Attention needed, but not critical    |

