# Developing for Web Accessibility

## Summary

This page introduces some basic considerations to help you get started developing web content that is more accessible to people with disabilities. These tips are good practice to help you meet Web Content Accessibility Guidelines (WCAG) requirements. Follow the links to the related WCAG requirements, detailed background in the “Understanding” document, guidance from Tutorials, user stories, and more.

## Navigation 
- [Home](../)
- [Back](./)


## Associate a label with every form control

Use a for attribute on the `<label>` element linked to the id attribute of the form element, or using WAI-ARIA attributes. In specific situations it may be acceptable to hide `<label>` elements visually, but in most cases labels are needed to help all readers understand the required input.

```html
<label for="username">Username</label>
<input id="username" type="text" name="username">
```

## Include alternative text for images

Ensure that alternative text for images is added to all informational and functional images. Use empty alternative text, alt="" for decorative images, or include them in the CSS instead. Text alternatives are usually provided by those responsible for written content.

## Identify page language and language changes

Indicate the primary language of every page by using the lang attribute in the html tag, for example `<html lang="en">`. Use the lang attribute on specific elements when the language of the element differs from the rest of the page.

## Use mark-up to convey meaning and structure

Use appropriate mark-up for headings, lists, tables, etc. HTML5 provides additional elements, such as `<nav>` and `<aside>`, to better structure your content. WAI-ARIA roles can provide additional meaning, for example, using role="search" to identify search functionality. Work with designers and content writers to agree on meanings and then use them consistently.

### Example: Using HTML to provide structure and meaning
```html
<section>
  <article>
    <h2>Superbear saves the day</h2>
    <time datetime="2015-08-07">7 Aug 2015</time>
    <p>The city's favorite bear yet again proves his mettle by rescuing a young cat from a tree. Witnesses say that Superbear's efforts were not appreciated by the feline, who inflicted some minor scratch wounds on his rescuer.</p>
    <aside>
      <h3>Related Articles</h3>
      <ul>
        <li><a href="#">Bear receives key to city</a></li>
        <li><a href="#">Superbear stands for mayor</a></li>
      </ul>
    </aside>
  </article>
</section>
```

### Example: Search field using WAI-ARIA

```html
<form action="#" method="post">
  <div role="search">
    <label for="search">Search for</label>
    <input type="search" id="search" aria-describedby="search-help">
    <div id="search-help">Search records by customer id or name</div>
    <button type="submit">Go</button>
  </div>
</form>
```

## Help users avoid and correct mistakes

Provide clear instructions, error messages, and notifications to help users complete forms on your site. When an error occurs:

- Help users find where the problem is
- Provide specific, understandable explanations
- Suggest corrections

Be as forgiving of format as possible when processing user input. For example, accept phone numbers that include spaces and delete the spaces as needed.

```html
<label for="phone">Phone</label>
<input id="phone" name="phone" type="tel"
       pattern="^(\(?0[1-9]{1}\)?)?[0-9 -]*$"
       aria-describedby="phone-desc">
<p id="phone-desc">For example, (02) 1234 1234</p>
```

## Reflect the reading order in the code order

Ensure that the order of elements in the code matches the logical order of the information presented. One way to check this is to remove CSS styling and review that the order of the content makes sense.

```html
<img src="images/trainer.png" alt="...">
<h3>Space trainers</h3>
<p>Space...</p>
<a href="...">Add to cart</a>
```

## Write code that adapts to the user’s technology

Use responsive design to adapt the display to different zoom states and viewport sizes, such as on mobile devices and tablets. When font size is increased by at least 200%, avoid horizontal scrolling and prevent any clipping of content. Use progressive enhancement to help ensure that core functionality and content is available regardless of technology being used.

```css

/* On narrow viewports, make the navigation full width */
@media screen and (min-width: 25em) {
  #nav {
    float: none;
    width: auto;
  }
  #main {
    margin-left: 0;
  }
}
/* On wider viewports, put the navigation on the left */
@media screen and (min-width: 43em) {
  #nav {
    float: left;
    width: 24%;
  }
  #main {
    margin-left: 27%;
  }
}
```

## Provide meaning for non-standard interactive elements

Use WAI-ARIA to provide information on function and state for custom widgets, such as accordions and custom-made buttons. For example, `role="navigation"` and `aria-expanded="true"`. Additional code is required to implement the behavior of such widgets, such as expanding and collapsing content or how the widget responds to keyboard events.

```html
<nav aria-label="Main Navigation" role="navigation">
  <ul>
    <li><a href="...">Home</a></li>
    <li><a href="...">Shop</a></li>
    <li class="has-submenu">
      <a aria-expanded="false" aria-haspopup="true" href="...">SpaceBears</a>
      <ul>
          <li><a href="...">SpaceBear 6</a></li>
          <li><a href="...">SpaceBear 6 Plus</a></li>
      </ul>
    </li>
    <li><a href="...">MarsCars</a></li>
    <li><a href="...">Contact</a></li>
  </ul>
</nav>
```

## Ensure that all interactive elements are keyboard accessible

Think about keyboard access, especially when developing interactive elements, such as menus, mouseover information, collapsable accordions, or media players. Use `tabindex="0"` to add an element that does not normally receive focus, such as `<div>` or `<span>`, into the navigation order when it is being used for interaction. Use scripting to capture and respond to keyboard events.

```js
var buttonExample = document.getElementById('example-button');

buttonExample.addEventListener('keydown', function(e) {
  // Toggle the menu when RETURN is pressed
  if(e.keyCode && e.keyCode == 13) {
    toggleMenu(document.getElementById('example-button-menu'));
  }
});

buttonExample.addEventListener('click', function(e) {
// Toggle the menu on mouse click
  toggleMenu(document.getElementById('example-button-menu'));
});
```

## Avoid CAPTCHA where possible

CAPTCHAs create problems for many people. There are other means of verifying that user input was generated by a human that are easier to use, such as automatic detection or interface interactions. If CAPTCHA really needs to be included, ensure that it is simple to understand and includes alternatives for users with disabilities, such as:

- Providing more than two ways to solve the CAPTCHAs
- Providing access to a human representative who can bypass CAPTCHA
- Not requiring CAPTCHAs for authorized users.

## <a name="resources"></a> Resources
1. [w3](https://www.w3.org/WAI/tips/developing/)

## Navigation 
- [Home](../)
- [Back](./)
