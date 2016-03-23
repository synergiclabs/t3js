---
layout: documentation
title: API - Application Stub
permalink: /docs/api/application-stub/
---

# Test Application Stub
T3.js provides a test bundle for unit testing. This package contains most of the core components and a stubbed
version of the Application object. We recommend using this package instead of the core T3.js code for testing your
components. Check out the <a href="../../guides/testing-bundle">T3 Testing Bundle Guide</a> for more information.

<div class="anchor" id="boxApplication"></div>

# Box.Application

### Description
This object is a stripped down version of the actual Box.Application that allows better unit testing.

<hr class="separator">

<div class="anchor" id="addService"></div>

## addService

### Description
Register a T3 Service component.

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
            <td class="required">name</td>
            <td>string</td>
            <td>Name of service.</td>
        </tr>
        <tr>
            <td class="required">creator</td>
            <td>Function</td>
            <td>Creator function for the service.</td>
        </tr>
    </tbody>
</table>

### Returns
The `Box.Application` object (for chaining purposes).

### Example
{% highlight javascript %}
Box.Application.addService('some-service', function(application) {
    return {
        foo: function() { ... }
    };
});
{% endhighlight %}

<hr class="separator">

<div class="anchor" id="addModule"></div>

## addModule

### Description
Register a T3 Module component.

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
            <td class="required">name</td>
            <td>string</td>
            <td>Name of module.</td>
        </tr>
        <tr>
            <td class="required">creator</td>
            <td>Function</td>
            <td>Creator function for the module.</td>
        </tr>
    </tbody>
</table>

### Returns
The `Box.Application` object (for chaining purposes).

### Example
{% highlight javascript %}
Box.Application.addModule('some-module', function(context) {
    return {
        init: function() { ... },
        destroy: function() { ... }
    };
});
{% endhighlight %}

<hr class="separator">

<div class="anchor" id="addBehavior"></div>

## addBehavior

### Description
Register a T3 Behavior component.


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
            <td class="required">name</td>
            <td>string</td>
            <td>Name of behavior.</td>
        </tr>
        <tr>
            <td class="required">creator</td>
            <td>Function</td>
            <td>Creator function for the behavior.</td>
        </tr>
    </tbody>
</table>

### Returns
The `Box.Application` object (for chaining purposes).

### Example
{% highlight javascript %}
Box.Application.addBehavior('some-behavior', function(context) {
    return {
        init: function() { ... },
        destroy: function() { ... }
    };
});
{% endhighlight %}

<hr class="separator">

<div class="anchor" id="hasService"></div>

## hasService

### Description
Checks if a service has been registered.

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
            <td class="required">service</td>
            <td>string</td>
            <td>Name of service.</td>
        </tr>
    </tbody>
</table>

