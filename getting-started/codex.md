Codex is the command line interface for CodefyPHP. It provides a few native commands to get you started building your 
first project.

Controller
----------

This command will create a controller class (i.e. UsersController) in `App/Infrastructure/Http/Controllers`:

    ❯ php codex stub:make Users_controller

Repository
----------

This command will create a repository class (i.e UserViewRepository) in `App/Infrastructure/Persistence/Repository`:

    ❯ php codex stub:make UserView_repository

Service Provider
----------------

This command will create a service provider class (i.e. DbalServiceProvider) in `App/Infrastructure/Providers`:

    ❯ php codex stub:make DbalService_provider

Middleware
----------

This command will create a middleware class (i.e. CsrfMiddleware) in `App/Infrastructure/Http/Middleware`:

    ❯ php codex stub:make Csrf_middleware

Error
-----

This command will create an error class (i.e. UserIdNotFoundError) in `App/Infrastructure/Errors`:

    ❯ php codex stub:make UserIdNotFound_error

Hash A Password
---------------

    ❯ php codex password:hash 'jsx82kjsks9273js'
    Your hashed password is: $2y$10$4A3iA5z.qyi6DZ5bibKXUujbqYdjH.QjpbO/lUDR9dalaN1IbEZtm 

Run the Scheduler
-----------------

The `schedule:run` command starts the scheduler and will execute any schedules/tasks that are due.

    ❯ php codex schedule:run