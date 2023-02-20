---
layout: post
title: Polymorphic Lazy-Loading
---
Proxies are an object-oriented polymorphic way of lazy-loading objects that are expensive to initialize/load. Lazy proxies allow client code not to care if the expensive object they are using has been loaded/initiated or not.

```php
<?php
class Client
{
  private $dependency;
  
  public function __construct(Dependency $dependency)
  {
    $this->dependency = $dependency;
  }
  
  public function doSmth($useDependency)
  {
    if ($useDependency) {
      $this->dependency->doSmthElse();
    }
  }
}
```

Here, the Client class does not need to care if it works with an actual Dependency or its Proxy. The expensive initialization will only happen when the Client calls the Dependency. If the Dependency is never called, the proxy will not initialize it.

Providers are a widespread pattern of lazy loading in some current (2015) web frameworks for lazy loading. But they leak the complexity of lazy loading into the client code.
