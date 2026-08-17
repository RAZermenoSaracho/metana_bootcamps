# Alternatives to Google Fonts for Custom Fonts

When Google Fonts doesn't meet your needs or preferences, there are several alternative methods for integrating custom fonts into your website.

- **Use native font stacks**: This involves specifying a list of font families in your CSS code, allowing the browser to use the first available font on the user's device. However, this approach may result in inconsistent font rendering across different devices and operating systems, as not all fonts are universally supported.
- **Adding custom fonts locally**: You can download the font files and include them directly in your project's CSS files. This ensures that the fonts are always available, regardless of internet connectivity. Tools like Webpack can help automate this process during the build stage of your project, ensuring that the fonts are properly included and optimized.
  - *See*: [Adding images, fonts, and files with Webpack](https://create-react-app.dev/docs/adding-images-fonts-and-files/)
- **Using an NPM package**: There are NPM packages available that provide a convenient way to install and manage custom fonts in your project.
  - **Typefaces**: Although deprecated, Typefaces was a popular option for installing fonts via NPM. However, it's no longer actively maintained.
    - *GitHub repository*: [Typefaces](https://github.com/KyleAMathews/typefaces)
  - **Fontsource**: Fontsource is a modern alternative that offers a wide selection of fonts and is actively maintained. It provides a straightforward method for installing fonts via NPM and integrating them into your project.
    - *Website*: [Fontsource](https://fontsource.org/)
    - *GitHub repository*: [Fontsource](https://github.com/fontsource/fontsource)
  - **Locally hosted/installed**: You can also host the font files on your own server and reference them in your project's CSS files. This gives you full control over the fonts and ensures that they are always available, even if external services are unavailable.
