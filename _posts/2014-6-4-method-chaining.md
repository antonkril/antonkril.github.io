---
layout: post
title: Method Chaining
---

Method chaining must be discouraged. It is usually a sign of bad design, mutable objects, temporal coupling, and non-atomic initialization.

Many frameworks recommend returning objects from state-modifying methods (especially `$this` from setters) to allow the chaining of method calls:

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

The example above demonstrates one of the problems with the mutable state highlighted by method chaining API. The second call to `addDateFilter` will not have an effect because the client could not know the state of `$collection` at the moment of the call to `addDateFilter`. Objects must be initialized atomically at creation to avoid situations like this.
