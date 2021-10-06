# Laravel 8 Routing: Important Change You Need to Know

Laravel 7- | Laravel 8+
------------ | -------------
Old way | New way
> route::get('/', 'TestController@index'); | route::get('/', [TestController::class, 'index']);
> You could just write your route with Controller and method like the below | Content cell 2


