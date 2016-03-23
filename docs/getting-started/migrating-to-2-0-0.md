---
layout: documentation
title: Migrating from 1.5.1 to 2.0.0
---

# Migrating from 1.5.1 to 2.0.0

The latest version of T3 contains major improvements to robustness and testability. We have listed the breaking changes are listed here:

#### Native DOM is now the default

We've switched the default t3 package to use native by default (IE9+). If you would like to use the jQuery version, please use the t3-jquery-2.x.x.js distribution file.

#### Including duplicate behaviors throw errors

{% highlight js %}
Box.Application.addService('some-module', function(application) {
    return {
        behaviors: ['behavior1', 'behavior2', 'behavior1'] // Error
    };
});
{% endhighlight %}

#### Behaviors `init()` before module `init()`

This should allow the modules to rely on any required setup from the behaviors.

{% highlight js %}
Box.Application.addBehavior('some-behavior', function(context) {
	return {
		init: function() {
			console.log('foo');
		}
	};
});
{% endhighlight %}

{% highlight js %}
Box.Application.addModule('some-module', function(context) {
	return {
		behavior: ['some-behavior'],

		init: function() {
			console.log('bar');
		}
	};
});
{% endhighlight %}

{% highlight js %}
Box.Application.start('[data-module="some-module"]');

Outputs:
foo
bar
{% endhighlight %}

#### `getService()` throws errors when the service does not exist

{% highlight js %}
application.getService('non-existent-service'); // Error
{% endhighlight %}

Previously, this would return `null`. Use `hasService()` to check for optional services.

{% highlight js %}
var service = application.hasService('some-service')
		? application.getService('some-service') : null;
{% endhighlight %}
This change will allow developers to catch issues with missing services before they hit production.

#### Removed `exports` option from `addService()`

{% highlight js %}
Box.Application.addService('foo', function() { ... }, {
	exports: ['bar']
});
Box.Application.bar(); // no longer works
{% endhighlight %}
This option was unused and dangerous since it modified the global `Application` object which could lead to unexpected coupling.

#### `TestServiceProvider` requires explicit pre-registered services

{% highlight js %}
beforeEach(function() {
	var context = new Box.TestServiceProvider({
		service1: {
			foo: function() {}
		}
	}, ['dom', 'promises']); // List of services used but not stubbed
	...
});
{% endhighlight %}
This will prevent accidental leakage of services between unit tests.
