A Content Security Policy ([CSP](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)) is an added layer of security that can be added to your application to detect and 
mitigate certain types of attacks, such as, Cross-Site Scripting ([XSS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-XSS-Protection)). 
To learn more about the different policies you can set, check out the 
[Content-Security-Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy).

The `ContentSecurityPolicyMiddleware` makes it easy to add Content-Security-Policy headers and other [security related 
headers](https://codefyphp.com/knowledgebase/security-headers/) in your application. The config can be found 
at `config/headers.php`. `hsts`, `expect-ct`, and some permission policies are not enabled by default. You can edit the 
configuration to your liking or make it even more simple by adding a `custom-csp` setting to the `config/headers.php` 
config: 

    <?php
        
    'custom-csp' => "'base-uri 'none'; default-src 'none'; child-src 'none'; connect-src 'none'; font-src 'none'";

When you add the above line to the configuration, it will override any other security policies and output:

    Content-Security-Policy: base-uri 'none'; default-src 'none'; child-src 'none'; connect-src 'none'; font-src 'none'

Forum
-----

If you have any questions or issues, please feel free to post to the [Documentation Forum](https://codefyphp.com/community/documentation/).

SLA Support
-----------

If you are needing more hands on support, needing consultation, or help with setup, support me on [Github](https://github.com/sponsors/nomadicjosh) at $60 or more. Once you've sponsored me, you will receive an email on the best way to contact me to start your support.