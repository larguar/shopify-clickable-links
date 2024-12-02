# Shopify Clickable Mega Menu Links
The Shopify Combine theme[^1] has a really great mega menu feature that I was excited to use for our website, but the functionality wasn't fully what I needed. By default, the mega menu appears when you hover over the designated link in the main menu, but that main menu 'link' doesn't actually function as a link. While the mega menu has additional links for a user to click through to if they so choose, I needed the main 'link' to still function as a link when clicked. This code allows for both the click and hover to occur, bettering the user experience.

![JavaScript Badge](https://img.shields.io/badge/-JavaScript-539436) ![Shopify Liquid Badge](https://img.shields.io/badge/-Shopify%20Liquid-750460)   


## Table of Contents 
* [Code](#code)    
* [Questions](#questions) 
* [Donate](#donate)
* [Notes](#notes)


## Code

:file_folder: **sections/header.liquid**

Search for `{%- when 'mega-menu' -%}` (there should be two in the file) and add to each `{%- render -%}`:
```
id: block.id,
```

:file_folder: **snippets/site-nav-mega.liquid**

Search for `<a class="menu-link {{ links_weight }}"` and add before classes in `<span>`:
```
id="{{ id }}"
```

:file_folder: **assets/script.js.liquid**[^2]

Add this code anywhere in your custom script file. Use browser Inspector to find the new `<a class="menu-link">` ID for each menu menu navigation link (regular and sticky menu) and update ID names and `window.location.href` paths for each `document.getElementById()`:
```
{% comment %} Clickable Mega Menu Links {% endcomment %}
document.getElementById("mega_menu_6t4AGw").onclick = function() {
  window.location.href = "/collections/pins";
};
document.getElementById("mega_menu_7Cnq9A").onclick = function() {
  window.location.href = "/collections/extras";
};
setTimeout(() => {
  document.getElementById("mega_menu_6t4AGw-sticky").onclick = function() {
    window.location.href = "/collections/pins";
  };
  document.getElementById("mega_menu_7Cnq9A-sticky").onclick = function() {
    window.location.href = "/collections/extras";
  };
}, 0.1);
```


## Questions
If you have any questions, feel free to find me at:
* Email: laurenguardala@gmail.com
* Website: [larguar.com](https://larguar.com)
* Github: [@larguar](https://github.com/larguar)


## Donate
Appreciate this code? Say thanks with a coffee:

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/W7W21YVJJ)


## Notes
[^1]: This code is specific to the [Combine](https://themes.shopify.com/themes/combine/styles/objects) theme in Shopify, but should work for other themes with some adjustments. File names will likely be different across themes.
[^2]: This is the file I created for my shop's custom JavaScript. If you have your own file already created, you can add this snippet to that file. If you need to create a new file, just make sure you link to it in your `layout/theme.liquid` file and that it's a `.js.liquid` file (not just `.js`).
