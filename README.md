##**Shopify** - Free Shipping Bar

This is a very simple and quick solution, and great way around having to use an App or adding extra Javascript. We will be adding a custom snippet that will handle all of our logic, free shipping values and support other additonal functions like displaying a Promo Code at checkout based on the items in your cart.

>We do use some custom grid classes for positioning which will most likely need to be replaced on your end, unless your theme uses the Foundation framework and includes FontAwesome icons.

---

####Step 1

Add the *snippet-free-shipping.liquid* file to your **Snippets** folder.

Add the contents of *style.css* to your *custom-styles.css.liquid* file in the **Assets** folder.

####Step 2

Open your *cart.liquid* file and add `{% include 'snippet-free-shipping' %}` where you would like the promo bar to appear. Usually this is done above the cart `<form>` tag and inside the opening `{% if %}` liquid tag that checks if the cart is empty, to avoid any logic errors.

####Step 3

Customize the *snippet-free-shipping.liquid* file by adding your custom free shipping total byt replacing **25** in the line `{% assign free_ship = 25 %} `. 

>Notice that we do **not** include the **$** sign when we assign a value to the *free_ship* variable. The value must be a number, not a string.

#####Notes

The *cart.total_price* variable is in **cents** therefore, if your free shipping is $25, liquid expects the value to be 2500. For the sake of simplicity, we enter the *free_ship* value as *25* and then assign a new variable that takes our *free_ship* variable, multiplies it by 100 and saves it as *updated_free_ship*. Liquid is fairly limited with math functions and flexibility when working with variables. We can't simply declare a variable and then multiply it by 100 next time we call it as you would expect in JS or other similar languages, like so:

```JS
    var a = 25;
    a = a * 100;
    \\ or simply a *= 100;
    console.log(a); \\returns 2500
```

Because of this, we are forced to use a workaround, declaring a brand new variable to convert our value into somethign shopify can more easily use in our case.