# Laravel: From Apprentice To Artisan

## Dependency Injection

`IoC`: a convenience mechanism for achieving `dependency injection`.

`Separation Of Concerns`: Every class should have a single responsibility, and that responsibility should be entirely encapsulated by the class.

`Respect Boundaries`: Controllers and routes serve as a mediator between HTTP and your application. When writing large applications, don't cluter them up with your domain logic.

## The IoC Container

https://github.com/illuminate/container/blob/master/Container.php

`IoC Container`:
- Manages resolving and injecting a given class or interface throughout your application.
- Binding interface to implementation.
- Being able to change implementations of an interface with a single line.

```php
App::bind('BillerInterface', 'StripeBiller');

App::bind('BillingNotifierInterface', function()
{
return new SmsBillingNotifier;
});
```

`Reflection`: ability to inspect a class and methods.

```php
$reflection = new ReflectionClass('StripeBiller');
var_dump($reflection->getMethods());
var_dump($reflection->getConstants());
```

## Interface As Contract

`Duck Typing`: If the object looks like a duck, and quacks like a duck, it must be a duck.

`Interface`: Interfaces are contracts. Interfaces do not contain any code, but simply define a set of methods that an object must implement.

`Polymorphism`: an interface can have multiple implementations.

## Service Providers

`Service Provider`: a class that register IoC container binding.

## Application Structure

- Always break your application into small componenets, each having a very focused responsibility.
- A key to solid application design is simply separating responsibilities, or creating layers of responsibility.
- Separation of responsibilities is one of the keys to writing maintainable applications.
- Avoid making your transport layer, such as handlers, responsible for knowledge about your application and business logic.

## SOLID

### Single Responsibility Principle

- A class' scope and responsibility should be narrowly focused.
- Make sure that all of the methods in a class are aligned with the overall responsibility of that class.
- Decouple the code to make test easier and change friendlier.

### Open Closed Principle

- Code is open for extension but closed for modification.
- An implementation change in a dependency should not require any changes by its consumer.

### Liskov Subsitution Principle

- You should be able to use any implementation of an abstraction in any place that accepts that abstraction.
- If a class uses an implementation of an interface, it must be able to use any implementation of that interface without requiring any modification.
- Objects should be replacable with instances of their subtypes without altering the conrrectness of that program.
- Limitting class _knowledge_ will be a recurring and important theme.

### Interface Segregation Principle

- No implementation of an interface should be forced to depend on methods it does not use.
- Instead of having a big interface containing methods not needed by all implementations, it is preferable to have several smaller interface that maybe implemented individually as needed.

### Dependency Inversion Principle

- High-level code should not depend on low-level code, and abstractions should not depend upon details.
