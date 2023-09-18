Service providers are used to bootstrap your application with the injection of core classes and dependencies.

A service provider will have one or two methods: `register()` and/or `boot()`. The register method should only be used 
to define parameters, define new services or extend services.

The boot method is called after all service providers have been registered.

Here is an example of a service provider that registers a config service:

    use Codefy\Framework\Support\CodefyServiceProvider;
    use Qubus\Config\Collection;
    use Qubus\Config\Configuration;
    
    use function Codefy\Framework\Helpers\env;
    
    final class ConfigServiceProvider extends CodefyServiceProvider
    {
        public function register(): void
        {
            $this->codefy->defineParam(
                paramName: 'config',
                value: new Configuration(
                    [
                        'path' => $this->codefy->configPath(),
                        'dotenv' => $this->codefy->basePath(),
                        'environment' => env(key: 'APP_ENV', default: 'local'),
                    ]
                )
            );
    
            $this->codefy->share(nameOrInstance: Configuration::class);
            $this->codefy->alias(original: 'codefy.config', alias: Collection::class);
            $this->codefy->share(nameOrInstance: 'codefy.config');
        }
    }