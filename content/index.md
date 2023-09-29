---
layout: layouts/base.njk
eleventyNavigation:
  key: Home
  order: 1
numberOfLatestPostsToShow: 10
---  
Welcome! I'm Ahmad Rifai, a Mobile & Game Developer
{% set postsCount = collections.posts | length %}
# Latest Posts
{% set postslist = collections.posts | head(-1 * numberOfLatestPostsToShow) %}
{% include "postslatest.njk" %}

{% set morePosts = postsCount - numberOfLatestPostsToShow %}
{% if morePosts > 0 %}
<p><a href="/blog/">View all</a></p>
{% endif %}


