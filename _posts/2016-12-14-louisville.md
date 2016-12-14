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
    <div><task v-for="task in tasks">{{ task.task }}</task></div>
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
