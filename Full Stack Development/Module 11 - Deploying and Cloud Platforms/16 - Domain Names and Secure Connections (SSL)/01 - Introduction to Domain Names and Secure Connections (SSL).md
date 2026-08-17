# Introduction to Domain Names and Secure Connections (SSL)

A domain name is a unique and human-readable identifier that represents a specific location on the internet. A domain name serves as a custom URL you can use for a website, web application, or network.

- This does not include anything from a “dot” section preceding the domain name.
- Domains are divided into **domain**, **subdomain**, and **TLD** (top-level domain)

**Example**

- Consider the domain name `example.foo.com`
  - `foo.com` is the domain name.
  - `.com` is the TLD.
  - `example` is the subdomain.

[YouTube video player](https://www.youtube.com/watch?v=Y4cRx19nhJk)

### **Subdomains**

Subdomains are subdivisions of a domain that allow for further organization or differentiation of content.

- Characteristics
  - Example: [example.foo.com](http://example.foo.com/) is a subdomain of `foo.com`
  - Flexibility
    - Subdomains may direct to separate servers or be managed by the same server as the root domain.
    - They are typically provided at no extra cost, allowing for the creation of multiple subdomains under a single domain name.

### **Path and Query Parameters**

Path and query parameters are components of a URL that provide additional context or instructions.

- **Path**
  - Description: Anything following the TLD with a `/`
  - Example: In `example.foo.com/profile`, `/profile` constitutes the path.
- **Query Parameters**
  - Description: Parameters following a `?` in the URL.
  - Example: In `example.foo.com/profile?user=bob&view=1`, `user=bob&view=1` represents the query parameters.

### Domain Name Registrars

- Domain name registrars are the entities where individuals or organizations go to purchase domain names for their websites or online ventures.
- These registrars are subject to strict control and regulation by organizations like ICANN (Internet Corporation for Assigned Names and Numbers).
- **Services Offered**
  - Domain name registrars often provide additional services to complement domain registration.
  - Examples include
    - **Domain Privacy Protection**: Offers privacy features to shield personal information associated with the domain.
    - **Email Hosting**: Provision of email services associated with the domain.

### **Registering a Domain Name**

- Process
  - Custom domain names can be registered through any commercial registrar.
  - Popular registrars include [porkbun.com](http://porkbun.com/), [Godaddy.com](https://www.godaddy.com/), [Domain.com](http://domain.com/), and [Name.com](http://name.com/).
  - Recommendation: [porkbun.com](http://porkbun.com/).
- Duration and Renewals
  - Domain registration grants ownership for a specific period.
  - Registration periods typically range from 1 year to 10 years.
  - Renewals often incur additional costs, which may be higher than the original registration fee.
- **Costs**
  - Domain registration costs vary widely depending on factors such as the domain extension and registrar.
  - Prices range from as low as $2-3 USD to hundreds of dollars per year.
  - Domain owners can set their own prices if they wish to sell a domain name, with bids accepted if the domain is open for sale.
- **Registering Subdomains**
  - Once a domain name is registered, users can set up subdomains and configure DNS records as needed.
  - Configuration of an MX record allows for the handling of email services with a custom email provider.

## Links

- [YouTube video player](https://www.youtube.com/watch?v=Y4cRx19nhJk)
