### 9.2. Content Security Policy (CSP)

Content Security Policy (CSP) is a security feature that helps prevent Cross-Site Scripting (XSS) and data injection attacks by controlling which resources can be loaded and executed on a web page. CSP works by specifying the allowed sources for content such as scripts, styles, images, and more.

#### How CSP Works:

CSP allows web developers to declare a set of security policies by using the `Content-Security-Policy` HTTP header or a `<meta>` tag in the HTML. These policies define which resources are trusted and can be executed by the browser. Any violation of these policies triggers a report to the server or a block, depending on the CSP configuration.

#### Examples of CSP Directives:

1. **`default-src`:** Specifies the default policy for loading resources.
   
   ```html
   <meta http-equiv="Content-Security-Policy" content="default-src 'self';">
   ```

   In this example, only resources from the same origin are allowed.

2. **`script-src`:** Specifies the allowed sources for JavaScript.

   ```html
   <meta http-equiv="Content-Security-Policy" content="script-src 'self' 'unsafe-inline' 'unsafe-eval';">
   ```

   This policy allows scripts from the same origin, inline scripts, and scripts that use `eval()`.

3. **`style-src`:** Specifies the allowed sources for styles (CSS).

   ```html
   <meta http-equiv="Content-Security-Policy" content="style-src 'self' 'unsafe-inline';">
   ```

   This policy allows styles from the same origin and inline styles.

4. **`img-src`:** Specifies the allowed sources for images.

   ```html
   <meta http-equiv="Content-Security-Policy" content="img-src 'self' https://example.com;">
   ```

   This policy allows images from the same origin and from `https://example.com`.

5. **`connect-src`:** Specifies the allowed sources for network connections.

   ```html
   <meta http-equiv="Content-Security-Policy" content="connect-src 'self' https://api.example.com;">
   ```

   This policy allows connections to the same origin and to `https://api.example.com`.

#### CSP Reporting:

CSP also allows for violation reporting, which helps developers identify and fix security issues. Violation reports are sent to a specified endpoint when a policy is violated.

Example of reporting:

```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; report-uri /csp-report-endpoint;">
```

In this case, when a CSP policy is violated, a report is sent to `/csp-report-endpoint`.

#### Benefits of CSP:

- Mitigates the risk of XSS attacks by restricting the sources from which scripts can be loaded.
- Helps prevent data injection attacks by controlling which resources can be loaded.
- Provides a defense-in-depth approach to web security.
- Allows for real-time monitoring of policy violations.

#### Practical Use Cases:

CSP is used by web applications, especially those handling sensitive data or user accounts, to enforce security policies. Popular websites, like Google, Twitter, and GitHub, make use of CSP to protect against content injection attacks.

Enforcing a strong CSP can be a critical part of a web security strategy, especially when combined with other security measures like input validation and output encoding.

In summary, Content Security Policy is a crucial security feature that helps protect web applications from various types of attacks, such as XSS and data injection. Developers should implement CSP to safeguard their applications and users' data.
