---
title:  "Using nested Vue components in Laravel 5.3"
---

A blog about how to use Vue components in Laravel 5.3

In the */resources/assets/js/components/* directory, you can create a new .vue file. For example, I created a Task.vue file which has this code:


{% highlight ruby %}
<template>
  <li><slot></slot></li>
</template>
{% endhighlight %}
