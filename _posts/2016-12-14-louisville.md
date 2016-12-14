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

I created another .vue file in the components directory and called it TaskList.vue. The code that is there is:

{% highlight ruby %}
<template>
    <div> <task v-for="task in tasks">{{ task.task }}</task> </div>
</template>

<script>
    export default {
        data(){
            return {
                tasks: [
                  { task: 'Go to the barber', complete: true } ,
                  { task: 'Paint the Garage', complete: false } ,
                  { task: 'Vegetables', complete: true } ,
                  { task: 'Go to the barber', complete: false }

                ]

                };

            }
    }

</script>
{% endhighlight %}

In this template, I try to access the earlier template <task>. Note also that I have wrapped the <task></task> template in a <div></div>

Inside the app.js file which is inside */resources/assets/js/* directory I have this code

{% highlight ruby %}

/**
 * First we will load all of this project's JavaScript dependencies which
 * include Vue and Vue Resource. This gives a great starting point for
 * building robust, powerful web applications using Vue and Laravel.
 */

require('./bootstrap');

/**
 * Next, we will create a fresh Vue application instance and attach it to
 * the body of the page. From here, you may begin adding components to
 * the application, or feel free to tweak this setup for your needs.
 */

Vue.component('checkout-form', require('./components/CheckoutForm.vue'));
Vue.component('task', require('./components/Task.vue'));
Vue.component('task-list', require('./components/TaskList.vue'));

const app = new Vue({
    el: '#app'
});

{% endhighlight %}

Here is my blade file which uses the component

{% highlight ruby %}
<div id="app">
    <task-list></task-list>
</div>
{% endhighlight %}

[Final Output](../../img/Screenshot from 2016-12-14 15-04-06.png){:class="img-responsive"}
