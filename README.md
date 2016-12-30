##**Shopify** - Free Shipping Bar

This is a very simple and quick solution, and great way around having to use an App or adding extra Javascript. We will be adding a custom snippet that will handle all of our logic, free shipping values and support other additonal functions like displaying a Promo Code at checkout based on the items in your cart.

>We do use some custom grid classes for positioning which will most likely need to be replaced on your end, unless your theme uses the Foundation framework.

---

####Step 1

Add the *snippet-free-shipping.liquid* file to your **Snippets** folder.

Add the contents of *style.css* to your *custom-styles.css.liquid* file in the **Assets** folder.

####Step 2

Open your *cart.liquid* file and add `{% include 'snippet-free-shipping' %}` where you would like the promo bar to appear. Usually this is done above the cart `<form>` tag and inside the opening `{% if %}` liquid tag that checks if the cart is empty, to avoid any logic errors.

####Step 3

Customize the *snippet-free-shipping.liquid* file by adding your custom free shipping totals. 

#####Notes

Shopify is a bit weird and confusing when it comes to the format of some numbers. The *cart.total_price* variable is in **cents** therefore, if your free shipping is $25 you should enter 2500. For the sake of this tutorial, whenever money is calculated, we will write it out in cents instead of dollars. Since liquid does not support traidional math functions like other languages, we are forced to use filters using the pipe `|`, but using a variable can sometimes have interesting results. This is the main reason why we simply don't assign the free shipping value to a variable, as is convention.