# HappyR BlazeBundle

To easy manage and update your routes.

Installation
------------

### Step 1: Using Composer

Install it with Composer!

```js
// composer.json
{
    // ...
    require: {
        // ...
        "happyr/blaze-bundle": "dev-master",
    }
}
```

Then, you can install the new dependencies by running Composer's ``update``
command from the directory where your ``composer.json`` file is located:

```bash
$ php composer.phar update
```

### Step 2: Register the bundle

 To register the bundles with your kernel:

```php
<?php

// in AppKernel::registerBundles()
$bundles = array(
    // ...
    new HappyR\BlazeBundle\HappyRBlazeBundle(),
    // ...
);
```

### Step 3: Configure the bundle

``` yaml
# app/config/config.yml

happy_r_blaze:
  entities:
    Acme\DemoBundle\Entity\Foo:
      edit:
        route: 'foo_edit'
        parameters: {id:'getId'}
      show:
        route: 'foo_show'
        parameters: {id:'getId'}

    Acme\DemoBundle\Entity\Bar:
      show:
        route: 'bar_show'
        parameters: {id:'getId'}

    Acme\DemoBundle\Entity\Baz:
      anything:
        route: 'baz_show'
        parameters: {id:'getId', foo_id:'getFoo.getId'}
```



Usage
-----
``` html

// Any.html.twig

{# foo is a Foo object #}
<a href="{{ foo|blaze('show') }}">Show Foo</a>

{# bax is a Baz object #}
<a href="{{ foo|blaze('anything') }}">Show Baz</a>


```