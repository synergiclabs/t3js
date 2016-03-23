---
layout: documentation
title: API - Test Service Provider
permalink: /docs/api/test-service-provider/
---

# TestServiceProvider
The TestServiceProvider is meant to be a substitute for the traditional `context` and `application` that T3 Modules/Behaviors/Services usually have access to.
The object allows for easy stubbing of T3 services and can enable unit tests to use the real service, if necessary.

### Usage
<table class="table table-striped">
    <thead>
        <tr>
            <th>Parameter</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="required">serviceStubs</td>
            <td>Object</td>
            <td>A map of service names to stubs.</td>
        </tr>
    </tbody>
    <tbody>
        <tr>
            <td class="optional">allowedServices</td>
            <td>string[]</td>
            <td>List of real services to use. You must include the service in your test script.</td>
        </tr>
    </tbody>
</table>

### Service Stub Example
{% highlight javascript %}
var context = new Box.TestServiceProvider({
    logger: {
        warn: function() {}
    }
});

var module = Box.Application.getModuleForTest('foo', context);
{% endhighlight %}


### Real Service Usage Example
{% highlight javascript %}
var context = new Box.TestServiceProvider({}, ['logger'] );

var module = Box.Application.getModuleForTest('bar', context);
{% endhighlight %}

<div class="anchor" id="getService"></div>

## getService

### Description
Retrieves either a service stub or the real service.

### Returns
A service object or throws an error if service does not exist.

### Example
{% highlight javascript %}
var context = new Box.TestServiceProvider({
    logger: {
        warn: function() {}
    }
});

var loggerService = context.getService('logger');
{% endhighlight %}

<hr class="separator">

<div class="anchor" id="hasService"></div>

## hasService

### Description
Checks if a service stub or the real service exists

### Returns
True if the service exists. False otherwise.

### Example
{% highlight javascript %}
var context = new Box.TestServiceProvider({
    logger: {
        warn: function() {}
    }
});

// True
context.hasService('logger');

// False
context.hasService('notifications');
{% endhighlight %}

<hr class="separator">

<div class="anchor" id="getGlobal"></div>

## getGlobal

### Description
Returns a global variable.

### Returns
A global variable or null.

### Example
{% highlight javascript %}

var context = new Box.TestServiceProvider({});

// Returns the window object
context.getGlobal('window');
{% endhighlight %}
