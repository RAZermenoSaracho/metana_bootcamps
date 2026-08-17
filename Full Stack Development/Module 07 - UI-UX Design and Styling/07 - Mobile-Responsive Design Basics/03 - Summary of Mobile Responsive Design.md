# Summary of Mobile Responsive Design

Summary of mobile responsive design basics, from [web.dev](http://web.dev) article

*Resource*: <https://web.dev/articles/responsive-web-design-basics>

1. **Set the Viewport**
   - To ensure optimal rendering, include a **meta viewport tag** in your HTML’s **`<head>`** section. This tag instructs the browser on how to control the page’s dimensions and scaling.
   - Use **`width=device-width`** to match the screen’s width in device-independent pixels, allowing content to reflow across different screen sizes.
2. **Ensure an Accessible Viewport**
   - Mobile browsers often render pages at a desktop screen width (around 980px) and then adjust font sizes and content scaling. This can lead to inconsistent font appearances.
   - By setting the viewport correctly, you enhance the user experience across devices.
3. **Size Content to the Viewport**
   - Design your content to fit the available screen real estate.
   - Consider font sizes, images, and layout adjustments based on the device’s capabilities.
4. **Images**
   - Optimize images for different screen sizes. Use responsive image techniques like **`srcset`** and **`sizes`**.
   - Avoid serving large images to small devices, as it impacts performance.
5. **Layout**
   - Can have layouts that adapt dynamically. F:
     - On phones, content appears in a single column.
     - Tablets might display the same content in two columns.
   - Use CSS flexbox, grid, and other layout tools to create flexible designs.
6. **CSS Media Queries for Responsiveness**
   - Employ media queries to apply specific styles based on viewport size.
   - Adjust typography, spacing, and other design elements as needed.
7. **Media Queries Based on Device Capability**
   - Consider device features (e.g., touchscreens) when designing interactions.
   - Modern responsive design caters to diverse user needs
