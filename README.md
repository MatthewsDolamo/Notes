# Laravel 8 Routing: Important Change You Need to Know

> Before the new release of Laravel 8, you could just write your route with Controller and method like the below

```route::get('/', 'TestController@index');```

Now if you have your code like the above on Laravel 8, you will get below error

```Target class [TestController] does not exist.```

To Fix this and use the old way, you can add the below code on your App/Providers/RouteServiceProvide.php
```
/**
     * The controller namespace for the application.
     *
     * When present, controller route declarations will automatically be prefixed with this namespace.
     *
     * @var string|null
     */

protected $namespace = 'App\\Http\\Controllers';
```
And to activate it you need to add the namespace to our routes method, e.g defaults usually web and api

```->namespace($this->namespace)```

Now it will work like Laravel 7



Laravel 7- | Laravel 8+
------------ | -------------
[Old way](https://laravel.com/docs/7.x/controllers#basic-controllers) | [New way](https://laravel.com/docs/8.x/controllers#basic-controllers)
route::get('/', 'TestController@index'); | route::get('/', [TestController::class, 'index']);




