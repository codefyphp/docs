---
title: Content Security Policy
sidebar_title: Content Security Policy
summary: Configure CodefyPHP Content Security Policy middleware and defensive HTTP headers to reduce XSS, framing, content-type, and cross-origin risks.
keywords: content-security-policy,security-headers,xss-protection
weight: 19
---

A Content Security Policy ([CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)) is an added layer of security that can be added to your application to detect and 
mitigate certain types of attacks, such as, Cross-Site Scripting ([XSS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-XSS-Protection)). 
To learn more about the different policies you can set, check out the 
[Content-Security-Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy).

The `ContentSecurityPolicyMiddleware` makes it easy to add Content-Security-Policy headers and other [security related 
headers](#security-headers) in your application. The config can be found 
at `config/headers.php`. `hsts`, `expect-ct`, and some permission policies are not enabled by default. You can edit the 
configuration to your liking or make it even more simple by adding a `custom-csp` setting to the `config/headers.php` 
config: 

    <?php
        
    'custom-csp' => "'base-uri 'none'; default-src 'none'; child-src 'none'; connect-src 'none'; font-src 'none'";

When you add the above line to the configuration, it will override any other security policies and output:

    Content-Security-Policy: base-uri 'none'; default-src 'none'; child-src 'none'; connect-src 'none'; font-src 'none'

## Security Headers

When using the `ContentSecurityPolicyMiddleware`, it will output a Content-Security-Policy header as well as other
security related headers. The middleware can apply the following headers to responses:

- `Server`
- `X-Content-Type-Options`
- `X-Download-Options`
- `X-Frame-Options`
- `X-Permitted-Cross-Domain-Policies`
- `X-Powered-By`
- `X-Xss-Protection`
- `Referrer-Policy`
- `Cross-Origin-Embedder-Policy`
- `Cross-Origin-Opener-Policy`
- `Cross-Origin-Resource-Policy`

These options and more can be configured in `config/headers.php`:

    <?php
    
    return [
        /*
        |--------------------------------------------------------------------------
        | Server
        |
        | Note: when server is empty string, it will not add to the response
        | header.
        |--------------------------------------------------------------------------
        */
        'server' => '',
    
        /*
        |--------------------------------------------------------------------------
        | X-Content-Type-Options
        |
        | Available Value: 'nosniff'
        |--------------------------------------------------------------------------
        */
        'x-content-type-options' => 'nosniff',
    
        /*
        |--------------------------------------------------------------------------
        | X-Download-Options
        |
        | Available Value: 'noopen'
        |--------------------------------------------------------------------------
        */
        'x-download-options' => 'noopen',
    
        /*
        |--------------------------------------------------------------------------
        | X-Frame-Options
        |
        | Available Value: 'deny', 'sameorigin', 'allow-from <uri>'
        |--------------------------------------------------------------------------
        */
        'x-frame-options' => 'sameorigin',
    
        /*
        |--------------------------------------------------------------------------
        | X-Permitted-Cross-Domain-Policies
        |
        | Available Value: 'all', 'none', 'master-only', 'by-content-type',
        | 'by-ftp-filename'
        |--------------------------------------------------------------------------
        */
        'x-permitted-cross-domain-policies' => 'none',
    
        /*
        |--------------------------------------------------------------------------
        | X-Powered-By
        |
        | Note: it will not add to response header if the value is empty string.
        |
        | Also, verify that expose_php is turned Off in php.ini.
        | Otherwise the header will still be included in the response.
        |--------------------------------------------------------------------------
        */
        'x-powered-by' => sprintf('CodefyPHP-%s', \Codefy\Framework\Application::APP_VERSION),
    
        /*
        |--------------------------------------------------------------------------
        | X-XSS-Protection
        |
        | Available Value: '1', '0', '1; mode=block'
        |--------------------------------------------------------------------------
        */
        'x-xss-protection' => '0',
    
        /*
        |--------------------------------------------------------------------------
        | Referrer-Policy
        |
        | Available Value: 'no-referrer', 'no-referrer-when-downgrade', 'origin',
        |                  'origin-when-cross-origin', 'same-origin', 'strict-origin',
        |                  'strict-origin-when-cross-origin', 'unsafe-url'
        |--------------------------------------------------------------------------
        */
        'referrer-policy' => 'no-referrer',
    
        /*
        |--------------------------------------------------------------------------
        | Cross-Origin-Embedder-Policy
        |
        | Available Value: 'unsafe-none', 'require-corp'
        |--------------------------------------------------------------------------
        */
        'cross-origin-embedder-policy' => 'unsafe-none',
    
        /*
        |--------------------------------------------------------------------------
        | Cross-Origin-Opener-Policy
        |
        | Available Value: 'unsafe-none', 'same-origin-allow-popups', 'same-origin'
        |--------------------------------------------------------------------------
        */
        'cross-origin-opener-policy' => 'unsafe-none',
    
        /*
        |--------------------------------------------------------------------------
        | Cross-Origin-Resource-Policy
        |
        | Available Value: 'same-site', 'same-origin', 'cross-origin'
        |--------------------------------------------------------------------------
        */
        'cross-origin-resource-policy' => 'cross-origin',
    
        ///////
    ];

Here’s a list of [common HTTP headers](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields), and the Mozilla
[recommended settings](https://infosec.mozilla.org/guidelines/web_security.html) for securing web applications.
