# PostmarkBundle
Symfony2 bundle for [Postmark](http://postmarkapp.com) API
## Setup

**Using Composer**
Add PostmarkBundle in your composer.json:

```js
{
    "require": {
        "mlpz/postmark-bundle": "*"
    }
}
```

``` bash
$ php composer.phar update mlpz/postmark-bundle
```

**Using Submodule**

    git submodule add https://github.com/miguel250/PostmarkBundle.git vendor/bundles/MZ/PostmarkBundle
    git submodule add https://github.com/kriswallsmith/Buzz.git  vendor/buzz

**Add the MZ namespace to autoloader**

``` php
<?php
   // app/autoload.php
   $loader->registerNamespaces(array(
    // ...
    'MZ'               => __DIR__.'/../vendor/bundles',
    'Buzz'             => __DIR__.'/../vendor/buzz/lib',
  ));
```
**Add PostmarkBundle to your application kernel**

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new MZ\PostmarkBundle\MZPostmarkBundle(),
    );
}
```

## Usage

**Message Service**
``` php
<?php
  $message  = $this->get('postmark.message');
  $message->addTo('test@gmail.com', 'Test Test');
  $message->setSubject('subject');
  $message->setHTMLMessage('<b>email body</b>');
```