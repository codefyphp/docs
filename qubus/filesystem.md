The filesystem is a wrapper for [PHP League’s Flysystem](https://github.com/thephpleague/Flysystem) by Frank de Jonge. 
The filesystem includes adapters for working with a local filesystems, SFTP, and Amazon S3.

Configuration
-------------

The filesystem configuration file can be found in at `config/filesystem.php`. The configuration file is only set up for 
one local filesystem and Amazon S3.

Disks
-----

Here is a look at the filesystem config showing the path for each disk: local, public, cache, media, sessions, cookies, 
view, logs, and S3.

    <?php
    
    declare(strict_types=1);
    
    use function Codefy\Framework\Helpers\storage_path;
    use function Qubus\Config\Helpers\env;
    
    return [
        /*
        |--------------------------------------------------------------------------
        | Filesystem disks. You may add as many filesystem disks as you need.
        |
        | Supported Drivers: "local", "ftp", "sftp", "s3"
        |--------------------------------------------------------------------------
        */
        'disks' => [
            /*
            |--------------------------------------------------------------------------
            | Default local disk.
            |--------------------------------------------------------------------------
            */
            'local' => [
                'root' => storage_path(),
                'visibility' => [
                    'file' => [
                        'public'  => (int) 0644,
                        'private' => (int) 0604,
                    ],
                    'dir'  => [
                        'public'  => (int) 0755,
                        'private' => (int) 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Public disk.
            |--------------------------------------------------------------------------
            */
            'public' => [
                'root' => storage_path(path: 'app/public'),
                'visibility' => [
                    'file' => [
                        'public'  => (int) 0644,
                        'private' => (int) 0604,
                    ],
                    'dir'  => [
                        'public'  => (int) 0755,
                        'private' => (int) 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Cache disk.
            |--------------------------------------------------------------------------
            */
            'cache' => [
                'root' => storage_path(path: 'framework/cache'),
                'visibility' => [
                    'file' => [
                        'public'  => (int) 0644,
                        'private' => (int) 0604,
                    ],
                    'dir'  => [
                        'public'  => (int) 0755,
                        'private' => (int) 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Media disk.
            |--------------------------------------------------------------------------
            */
            'media' => [
                'root' => storage_path(path: 'framework/media'),
                'visibility' => [
                    'file' => [
                        'public'  => (int) 0644,
                        'private' => (int) 0604,
                    ],
                    'dir'  => [
                        'public'  => (int) 0755,
                        'private' => (int) 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Session disk.
            |--------------------------------------------------------------------------
            */
            'sessions' => [
                'root' => storage_path(path: 'framework/sessions'),
                'visibility' => [
                    'file' => [
                        'public'  => (int) 0644,
                        'private' => (int) 0604,
                    ],
                    'dir'  => [
                        'public'  => (int) 0755,
                        'private' => (int) 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Session disk.
            |--------------------------------------------------------------------------
            */
            'cookies' => [
                'root' => storage_path(path: 'framework/cookies'),
                'visibility' => [
                    'file' => [
                        'public'  => (int) 0644,
                        'private' => (int) 0604,
                    ],
                    'dir'  => [
                        'public'  => (int) 0755,
                        'private' => (int) 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | View disk.
            |--------------------------------------------------------------------------
            */
            'views' => [
                'root' => storage_path(path: 'framework/views'),
                'visibility' => [
                    'file' => [
                        'public'  => (int) 0644,
                        'private' => (int) 0604,
                    ],
                    'dir'  => [
                        'public'  => (int) 0755,
                        'private' => (int) 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Log disk.
            |--------------------------------------------------------------------------
            */
            'logs' => [
                'root' => storage_path(path: 'logs'),
                'visibility' => [
                    'file' => [
                        'public'  => (int) 0644,
                        'private' => (int) 0604,
                    ],
                    'dir'  => [
                        'public'  => (int) 0755,
                        'private' => (int) 7604,
                    ],
                ],
            ],
    
            /*
            |--------------------------------------------------------------------------
            | Amazon S3
            |--------------------------------------------------------------------------
            */
            's3' => [
                'driver' => 's3',
                'key' => env(key: 'AWS_ACCESS_KEY_ID'),
                'secret' => env(key: 'AWS_SECRET_ACCESS_KEY'),
                'region' => env(key: 'AWS_DEFAULT_REGION'),
                'bucket' => env(key: 'AWS_BUCKET'),
                'url' => env(key: 'AWS_URL'),
                'endpoint' => env(key: 'AWS_ENDPOINT'),
            ],
        ],
        /*
        |--------------------------------------------------------------------------
        | Config for Local FileSystem.
        |--------------------------------------------------------------------------
        */
        'local' => [
            /*
            |--------------------------------------------------------------------------
            | Set the root directory.
            |--------------------------------------------------------------------------
            */
            'root' => storage_path(),
            /*
            |--------------------------------------------------------------------------
            | Set the visibility for files and directories.
            |--------------------------------------------------------------------------
            */
            'visibility' => [
                'file' => [
                    'public'  => (int) 0644,
                    'private' => (int) 0604,
                ],
                'dir'  => [
                    'public'  => (int) 0755,
                    'private' => (int) 7604,
                ],
            ],
        ],
    ];