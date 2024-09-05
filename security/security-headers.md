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

These options are configured in `config/headers.php`:

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

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.