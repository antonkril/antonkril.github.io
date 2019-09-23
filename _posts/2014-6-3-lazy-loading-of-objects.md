---
layout: post
title: Lazy Loading of Objects
---
Objects should be lazy-loaded with Proxies. It allows client code to be agnostic of whether original object is already loaded, or not.

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

Here Client class does not care if a real Dependency is provided, or its Proxy. 

Providers are popular for lazy loading, but they make client code know about lazy-loading.
