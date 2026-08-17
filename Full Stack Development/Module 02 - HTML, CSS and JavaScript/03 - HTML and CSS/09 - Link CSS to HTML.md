# Link CSS to HTML

You have three main ways to add CSS to HTML

### **Inline CSS**

Directly in your HTML elements, using the `style` attribute. Good for quick, one-off styling.

`<p style="color: red;">Red text</p>`

Here we have added a style to the paragraph element.

### **Internal CSS**

Inside a `<style>` tag in the `<head>` section of your HTML file. Suitable for styling a single page.

![](https://resources.metana.co/public/99/e9/99e9f73f15fc47417ac21afe04fdb181d19bd864fe6c259640c846ae5d5be2f6.png)

### **External CSS**

In a separate `.css` file. This is the best practice for larger projects or when you want consistent styling across multiple pages.

- Create a CSS file (e.g., `styles.css`) and link it in your HTML’s `<head>`

![](https://resources.metana.co/public/1e/f5/1ef587608b11096b40f70d44f64ca342930ab70bf552e71f073c49173e9e8b69.png)

In `styles.css`, add your CSS rules ;

![](https://resources.metana.co/public/ca/59/ca599f565a9d439cf258017e0bf140c85598eb7f8d5973590f108b3b87fedb5f.png)

[](http://app.metana.io/wp-content/uploads/2024/01/How-to-link-external-stylesheet-_-CSS-page.mp4)

This is how you can link an external css file to your html file. We recommend sticking to this method as you develop and work on adding more styles your pages maintaining code will become very easy if it is managed by a separate CSS file.

![](https://resources.metana.co/public/df/34/df343a6cc35a1a7ad77876284a8ae9d529682c84d812ad2333538d3a623bdc71.png)

CSS or Cascading Style Sheets... The term "Cascading" in Cascading Style Sheets (CSS) refers to the way styles are applied to HTML elements, and it implies a downward flow.

![](https://resources.metana.co/public/0f/75/0f7530ac03d23bb92c9116292528fd7b1dbcbb5194d749c4ea299c024d5524ef.png)

What do you think will happen? Well as the name implies... CSS has an order that is cascading. It means the downward code (or the selector) takes priority over the ones above it. Voila! Now you learnt the true meaning of the term CSS.

## Inheritance in CSS

Inheritance in CSS refers to the mechanism by which certain properties of a parent element are passed down to its child elements. When a style property is applied to a parent element, child elements within it can inherit and adopt those styles, creating a consistent and organized design. This helps reduce redundancy in style definitions and makes it easier to maintain and update styles across a website or application.

![](https://resources.metana.co/public/0e/da/0edaecd463aa530ec7bedeff91c982d91dc163b3ebd30f08c26440618a9c9a61.png)

In this example, the `font-family` and `color` properties are inherited by the child elements within the `.container`. However, the `font-size` property is not inherited and must be defined separately for the child elements.

1. **Parent Styles:**
   - When you apply styles to a parent element, such as a container or a specific type of element (e.g., `<div>`), some of those styles may be inherited by its child elements.
2. **Inherited Properties:**
   - Not all CSS properties are inherited. Only certain properties, such as `color`, `font-family`, `line-height`, and `text-align`, are inherited by default. Each property has a predefined inheritance behavior.
3. **Specificity of Styles:**
   - If a child element has its own style defined for a property, that style will take precedence over the inherited style. Specificity matters – a directly applied style on an element is more specific than an inherited one.
4. **Cascading Order:**
   - Inheritance is part of the cascade in Cascading Style Sheets (CSS). If a child element doesn't have a specific style defined for a property, it inherits that property from its parent. If the parent has multiple styles defined, the most specific one takes precedence.

## Experiment and Learn

The best way to become an expert in the any field is through experiments and continuous learning

- **Play with Properties:** Try different CSS properties like `margin`, `padding`, `border`, `font-family`, `background`, etc.
- **Developer Tools:** Use browser developer tools to experiment with styles live on your web page.
