# Hello, Working Ajax Requests with AngularJS

I had the most insane moments on-boarding with AngularJS from jQuery when I ran into this odd 
issue with the preparation of XHR requests for my AngularJS Projects. Some things to call out 
about this issue here:

* Manifests with use of the `$http` service to make calls other than `GET` calls to a remote API

## So... what was the problem?

When I formated my Ajax requests as a JavaScript struct, and passed it to `$http` thus:

```javascript
$http({
    url: 'http://some-api.com/some/endpoint',
    method: 'POST',
    data: {
        var1: 'val1',
        var2: 'val2'
    }
})
```

I would get the strangest error, and on the server-side, no data would be recieved. It is possible
that using a `Content-Type` header of some sort (perhaps `Content-Type: application/json`, and something 
other than the default encoding type for forms ( `application/x-www-url-form-urlencoded` ) on the server-side
may have solved the issue... I tried everything. What ended up solving the problem was this patch.

## Applying The Patch

Here's a simple implementation of the patch:

```html
<script src="/path/to/cfg.ajaxfix.js"></script>
<script>
    angular.module('HelloWorldApp', [
        'cfg.ajaxfix'
    ]);
</script>
```

That's it! And the patch is applied, and you can now use `$http` the same way you've used other jQuery
XHR helpers.

## Lastly, Can't Take Full Credit...

This was inspired by something else. Not sure where on the interwebs, but some kind developer left me a 
post that saved my life. Just doing this as an easy way to apply as a centralized dependency for my (LarCity)
projects.

Enjoy!

Uch.
  [@uchilaka](https://twitter.com/uchechilaka)