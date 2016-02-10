---
layout: post
title: Method Chaining
---
Method chaining must be discouraged as a clear sign of bad design and usage of mutable objects.

Many frameworks recommend returning objects from state-modifying methods (especially `$this` from setters) to allow chaining of method calls:

```php
<?php

class Collection
{
  public function addNameFilter($id)
  {
    // ...
    $this->id = $id;
    return $this;
  }
  
  public function addDateFilter($date)
  {
    // ...
    return $this;
  }
  
  public function getItems()
  {
    if (!$this->loaded) {
      $this->load();
    }
    return $this->items;
  }
}

$collection = new Collection();
$items = $collection->addNameFilter('test *')->getItems();

\\ ...

$filteredItems = $collection->addDateFilter(today())->getItems();
```

Example above demonstrates problems with mutable state: second call to `addDateFilter` will not have effect. Client could not know the state of `$collection` at the moment of call to `addDateFilter`. To avoid such situations, all objects must be initialized at creation.
