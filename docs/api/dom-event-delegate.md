---
layout: documentation
title: API - DOMEventDelegate
permalink: /docs/api/dom-event-delegate/
---

# DOMEventDelegate

The object type that handles events for modules and behaviors. Exposed publicly to allow developers to use in their own code. To create a new instance, specify the DOM element to handle events for and an object containing event handlers (`onclick`, `onmousedown`, etc., the same as for modules and behaviors):

{% highlight javascript %}
var delegate = new Box.DOMEventDelegate(element, {
    onclick: function(event) {
        console.log(event.type);
    }
});
{% endhighlight %}

You may also pass a custom list of events to handle as a third parameter (*v2.4.0+*):
{% highlight javascript %}
var delegate = new Box.DOMEventDelegate(element, {
    ontouchstart: function(event) {
        console.log(event.type);
    }
}, ['touchstart']);
{% endhighlight %}


<div class="anchor" id="defaultEventTypes"></div>

## Default Event Types Handled

{% highlight javascript %}
var eventTypes = [
    'click', 'mouseover', 'mouseout', 'mousedown',
    'mouseup', 'mouseenter', 'mouseleave', 'mousemove',
    'keydown', 'keyup', 'submit', 'change', 'contextmenu',
    'dblclick', 'input', 'focusin', 'focusout'
];
{% endhighlight %}

<div class="anchor" id="attachEvents"></div>

## attachEvents

### Description
Attaches all events for the delegate.

### Example
{% highlight javascript %}
var delegate = new Box.DOMEventDelegate(element, {
    onclick: function(event) {
        console.log(event.type);
    }
});

delegate.attachEvents();
{% endhighlight %}

<hr class="separator">

<div class="anchor" id="detachEvents"></div>

## detachEvents

### Description
Detaches all events for the delegate.

### Example
{% highlight javascript %}
var delegate = new Box.DOMEventDelegate(element, {
    onclick: function(event) {
        console.log(event.type);
    }
});

delegate.detachEvents();
{% endhighlight %}

