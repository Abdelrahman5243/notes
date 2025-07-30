
### jQuery Basics

```js
// DOM Ready
$(document).ready(function () {
  console.log('Page loaded');
});

// Select Elements
$('.class'), $('#id'), $('div')

// Add class, remove class
$('.btn').addClass('active');
$('.btn').removeClass('disabled');

// Hide, Show, Toggle
$('.popup').hide();
$('.popup').show();
$('.popup').toggle();

// Event Handlers
$('#submit').on('click', function () {
  alert('Submitted!');
});

// CSS Manipulation
$('div.box').css('background', 'blue');

// Traversing
$('.product').find('img');
$('.item').parent();

// Loop
$('.product').each(function (index, el) {
  console.log($(el).text());
});


```

---
### Using jQuery in Magento 2 with RequireJS

- in js file
  
```js
define(['jquery'], function ($) {
  'use strict';

  return function (config, element) {
    $(element).on('click', function () {
      console.log('Clicked!', config);
    });
  };
});

```

- in phtml file

```phtml js
<script type="text/javascript">
	require(['jquery'], function ($) {
	  $('.tocart').on('click', function (e) {
	    e.preventDefault();
	    let productId = $(this).data('product-id');
	    console.log('Adding product:', productId);
	  });
	});
</script>
```

---
### Handle AJAX Response

```js
require(['jquery'], function ($) {
  $.ajax({
    url: '/rest/V1/custom-endpoint',
    type: 'GET',
    success: function (data) {
      console.log(data);
    }
  });
});

```

---

### Animations

- Showing/hiding dropdowns
    
- Sliding filter panels
    
- Fading banners or messages
    
- Animating mini-cart or sidebars
---
##  1. Basic jQuery Animation Methods

|Method|Description|
|---|---|
|`.hide()`|Instantly hides the element|
|`.show()`|Instantly shows the element|
|`.fadeIn()`|Fades in the element|
|`.fadeOut()`|Fades out the element|
|`.slideDown()`|Slides element down (show)|
|`.slideUp()`|Slides element up (hide)|
|`.slideToggle()`|Toggles slide|
|`.animate()`|Custom animation (CSS properties)|

---

##  2. Using jQuery Animations in Magento with RequireJS

Wrap your animations inside `require(['jquery'], function ($) { ... })`.

### Toggle Filter Sidebar

```js
require(['jquery'], function ($) {
  $('.filter-toggle').on('click', function () {
    $('.filter-sidebar').slideToggle(300);
  });
});
```

---

## Fade In/Out Example: Success Message

```js
require(['jquery'], function ($) {
  $('.success-msg').fadeIn(400).delay(3000).fadeOut(400);
});
```

---

## 🎯 4. Custom `.animate()` Example

You can animate CSS properties like width, opacity, height:

```js
require(['jquery'], function ($) {
  $('#box').animate({
    width: '300px',
    opacity: 0.5
  }, 600);
});
```

---

##  5. Real Magento Example: Animate Mini Cart Panel

```js
require(['jquery'], function ($) {
  $('.action.showcart').on('click', function () {
    $('.block-minicart').stop(true, true).slideToggle(200);
  });
});
```

---

##  6. Hover Animations

```js
require(['jquery'], function ($) {
  $('.product-item').hover(
    function () {
      $(this).find('.hover-box').fadeIn(200);
    },
    function () {
      $(this).find('.hover-box').fadeOut(200);
    }
  );
});
```

---
##  7. Animation Tips

 - Keep durations short: 200–600ms  
 - Use `.stop()` to prevent animation queueing  
 - Use `slideToggle` or `fadeToggle` for quick UX  
 - Use class-based transitions (for Tailwind/CSS) when possible for better performance
---
###  Animations

```js
define(['jquery'], function ($) {
	'use strict';
	return function () {
	    $('.toggle-panel').on('click', function () {
	      $('.panel-content').slideToggle(300);
	    });
	};
});
```

---
### ajax

```js
$.ajax({
url: '/rest/V1/productlist/update-request/status',
type: 'POST',
contentType: 'application/json',
data: JSON.stringify({
'requestEtlalaManaged': 1
}),
dataType: 'json',
success: function(response) {
console.log(response)
},
error: function() {
console.log('An error occurred while processing your request.');
}
});
```
##  Summary

- Use `.slideToggle()`, `.fadeIn()`, `.animate()` for dynamic `UX`
    
- Always load `jQuery` via `require`
    
- Keep animations short and responsive
    
- Combine with `data-mage-init` if needed