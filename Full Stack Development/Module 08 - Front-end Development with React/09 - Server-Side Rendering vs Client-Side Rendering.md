# Server-Side Rendering vs Client-Side Rendering

Rendering refers to the process of generating the final output from a source, typically transforming it into a visual or interactive form that users can perceive and interact with. In the context of web development we have two types of rendering:

- Server-Side Rendering (SSR)
- Client-Side Rendering (CSR)

### Server-Side Rendering (SSR)

When using SSR, the server generates the entire HTML content for each page of the website beforehand. This pre-rendered HTML is then sent directly to the user's web browser, already filled with content.

#### ***Implications***

- **Data Transfer:** SSR requires sending the entire HTML document over the internet to the user's browser, which can make files larger and take longer to load, especially for pages with lots of content.

#### ***Benefits***

- **Improved Initial Load Time:** Since the browser gets a complete HTML page right away, users can see content quicker. This makes the website feel like it's loading faster, which improves user experience.

### Client-Side Rendering (CSR)

With CSR, the browser first loads a simple HTML structure, then downloads JavaScript files containing the website's code. The browser runs this code, which builds the page dynamically and handles user actions.

#### ***Implications***

- **Quick Feel:** CSR gives the impression that the website reacts instantly to clicks and taps. Once the first page is loaded, moving around the site feels fast because it doesn't reload the whole page each time.

#### ***Drawbacks***

- **SEO Challenges:** Search engines sometimes struggle to understand CSR websites since the content changes using JavaScript. This can hurt the site's visibility in search results.
- **Performance Concerns:** CSR sites might take longer to load initially, especially on slower internet connections or older devices. This is because the browser needs to fetch and process JavaScript files before showing any content.

**First Impressions:** While CSR sites can feel quick once they're up and running, the first load might not be as snappy. Users might see delays or blank screens while the browser gets everything ready.

[YouTube video player](https://www.youtube.com/watch?v=rNVcZklcmqU)

## Links

- [YouTube video player](https://www.youtube.com/watch?v=rNVcZklcmqU)
