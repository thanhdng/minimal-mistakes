---
layout: single
title: "How I added Disqus comment in Minimal Mistakes Jekyll theme"
categories:
    - Blogging
tags:
    - Jekyll
    - Minimal Mistakes
    - Disqus
    - Comments
---
Minimal Mistakes is a nice and beautiful Jekyll theme. It helps you to write, design your personal blog much easier. I followed [this guide](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#comments) to add Disqus comment to the posts but it didn't work. After playing around a while, I decided to folow the guide from Disqus and it worked perfectly. Here's how I did it.

1. Create a Disqus shortname, for example: ```your_disqus_shortname```. You should notice that this is the shortname only, not the link ```your_disqus_shortname.disqus.com```.
2. In ```_config.yml```, modify comment provider to be ```"disqus"```,  disqus shortname to be ```your_disqus_shortname``` and default comments to be ```true```.
3. Modify the content of ```_includes/comments-providers/disqus.html``` to this:

{% highlight javascript linenos %}
{% if site.comments.disqus.shortname %}
<script>
/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
var disqus_shortname = '{{ site.comments.disqus.shortname }}';
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = '//' + disqus_shortname + '.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}
{% endhighlight %}

Now you can start receiving feedbacks from your readers!



