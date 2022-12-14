---
layout: default
title: Custom View
nav_order: 3
has_children: true
permalink: /docs/custom-view
---
# Custom View
KDRS Innsyn can be extended for advanced data manipulation and presentation. Some basic XML config is need to activate the view. We encourage the use of XML where possible, and then use custom views for the advanced stuff. This allows for readability in the community.
{: .fs-6 .fw-300 }

# Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Make a new file for the view
In your hosts `view` directory, create a new file for your view. It must start with underscore. Use lowercase. The html.erb extention will make sure that the ruby server will process the file first, then the html engine.

{% highlight bash %}
/var/kdrs/innsyn/views/schoolsys/_diploma.html.erb
{% endhighlight %}

# Reference the view from xml
The program flow will be redirected to this view. You will be in control of the presentation.

{% highlight html %}
    <table>
        <customview>diploma</customview>
{% endhighlight %}

# Minimum template

{% highlight erb %}
<!-- diploma 1.0.0 -->
<!-- DATA PREPARATION -->
<% adjust the @docs or other data if needed, in Ruby %>

<!-- DATA PRESENTATION -->
<%= render 'table', vi: @vi, ti: @ti %>
{% endhighlight %}

This view template will generate the same view as the internal template.
The difference is that you can manipulate the data as needed, and change the presentation with new styling, headings, extra text, tables etc. Maybe you want some different layout on print. This you can change from here.

# Data
The data from xml will be available to the view in the `@docs` variable. If you need more data from other tables, you can fetch those here. See the examples for how this is done.

# Html
You can write plain html in this file
{% highlight html %}
    <h1>Hello, there!</h1>
{% endhighlight %}

# ERB - Embedded Ruby
You can write plain Ruby in this file
{% highlight erb %}
    <% Ruby here %>
{% endhighlight %}


You can manipulate data in the background, or do some fancy things with the html code.

{% highlight erb %}
<% 5.times do %>
    <h1>Hello, there!</h1>
<% end %>
{% endhighlight %}


# Javascript
You can use Javascript for advanced presentation. However - we encourage the use of Ruby whenever possible for human readability and community sharing.
{% highlight html %}
<script>
    // Javascript here, if needed.
</script>
{% endhighlight %}


