---
layout: page
title: Johnathan Mark Smith's Blog
tagline: CONSULTING AND TECHNOLOGIES FOR BUILDING TOMORROW’S WORLD
---


<script src="js/jquery.tipsy.js" type="text/javascript" charset="utf-8">

</script>

<link href="css/tipsy.css" rel="stylesheet" />

<script type='text/javascript'>

$(document).ready(function ()
{
$('#example1').tipsy();
});
</script>

<div class='target' title='The content of this tooltip is provided by the' id='example1'>hover</div>

<p id='manual-example'>
  <a rel='tipsy' title='Well hello there'>My tooltip is manually triggered</a>
  <a href='#' onclick='$("#manual-example a[rel=tipsy]").tipsy("show"); return false;'>Show</a>
  <a href='#' onclick='$("#manual-example a[rel=tipsy]").tipsy("hide"); return false;'>Hide</a>
</p>

<script type='text/javascript'>

  $('#manual-example a[rel=tipsy]').tipsy({trigger: 'manual'});
</script>




After over 25 years specializing in business technology I feel that I have the right to post some information on a blog. The following posts and information are just my views and only my views. If you don't like something that I posted please email me and I will address it.


Here are some of my posts (check out the <a href="archive.html">archive page</a> for more posts):


<ul class="posts">
{% for post in site.posts limit: 20 %}
  <div class="post_info">
    <li>
         <a href="{{ post.url }}">{{ post.title }}</a> 
         <span>({{ post.date | date:"%Y-%m-%d" }})</span>
    </li>
    </div>
  {% endfor %}
</ul>


If you have any questions or comments please email me at <a href="mailto:john@johnathanmarksmith.com">john@johnathanmarksmith.com</a>

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-40973546-1', 'johnathanmarksmith.com');
  ga('send', 'pageview');

</script>







