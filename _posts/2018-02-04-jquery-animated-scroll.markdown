---
layout: post
url: 2018-02-04-js-animated-scroll
date: 2018-02-04
alt: image-alt
client: 
category: 
title: JQuery - Animated Scroll
featured: 
introduction: Both <a href="/libertyhawk" target="_blank">Liberty Hawk</a> and <a href="/wikit" target="_blank">Wikit</a> use an animatd scroll to top button with JQuery for xs and small views. The purpose of this feature is to ease navigation for users on small devices. Both apps have long-scrolling pages, and the scroll to top button make getting back to the top of the page much easier than manually scrolling it.  The implementation of this feature is practically identical between <a href="/libertyhawk" target="_blank">Liberty Hawk</a> and <a href="/wikit" target="_blank">Wikit</a> (the difference being some style elements), so the discussion and code snippets below will just draw from <a href="/libertyhawk" target="_blank">Liberty Hawk</a>. 
---

<div class="row">
    <div class="col-md-12">

    </div>
</div>


<h5>Button - Display</h5>
<div class="page-content-text">
The button element is placed under the footer. It's position is fixed in the lower right-hand corner of the view.
</div>

<div class="row">
    <div class="col-md-5 col-sm-6">
        <div class="pull-left" style="display:table; margin: auto">
            <img src="{{site.baseurl}}/img/blog/scroll-to-top.gif" class="img-responsive img-padded img-marg" alt="">
        </div>
    </div>
    <div class="col-md-7 col-sm-6">
    
<div class="file-path" style="overflow:hidden">app/views/layouts/application.html.erb</div>
{% highlight erb %}
<!-- footer element above -->
<div class="scroll-top visible-xs visible-sm">
    <a class="btn btn-primary page-scroll" href="#">
        <i class="fa fa-chevron-up"></i>
    </a>
</div>
{% endhighlight %}
    
        <div class="file-path">app/assets/stylesheets/application.scss</div>
{% highlight scss %}
.scroll-top .btn {
    z-index: 1049;
    position: fixed;
    right: 2%;
    bottom: 2%;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    font-size: 20px;
    background-color: #5a59a3 !important;
    border:1px solid #5a59a3 !important;
}
{% endhighlight %}
    </div>
</div>
<div>&nbsp;</div>

<h5>JQuery - smooth scroll</h5>
<div class="page-content-text">
Two functions are used in conjunction with the scroll button. First, an event handler to fade the scroll to top button is bound to the JavaScript <span class="terms">scroll</span> event. The function is executed each time the event is triggered on the <span class="terms">window</span> object. Upon landing on the page, the <span class="terms">page-scroll</span> button is visible. After a user starts scrolling the page, the fade conditional is triggered. <span class="terms">page-scroll</span> is faded out until the <span class="terms">scrollTop</span> property returns a value of greater than 100px (the user has scrolled more than 100px). At greater than 100px scroll, <span class="terms">page-scroll</span> is faded in. It is faded out again after the user has returned to the top of the page.
</div>
<div class="page-content-text">
The second function returns the user to the top of the page, by triggering a <span class="terms">click</span> event handler on the <span class="terms">page-scroll</span> button. The <span class="terms">click</span> event uses the JQuery <span class="terms">animate</span> method to gradually change the state of the <span class="terms">body</span> element. The <span class="terms">speed</span> paramter is set to <span class="terms">800</span>. The <span class="terms">scrollTop</span> property is used with a value of <span class="terms">0</span> to return the user to the top of the page without a vertical scrollbar. 
</div>

<div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight javascript %}
$(document).ready(function(){
    //Check to see if the window is top if not then display button
    $(window).scroll(function(){
        if ($(this).scrollTop() > 100) {
            $('.page-scroll').fadeIn();
        } else {
            $('.page-scroll').fadeOut();
        }
    });
    
    // jQuery for page scrolling feature
    $('.page-scroll').click(function() {
        $('html, body').animate({scrollTop : 0},800);
        return false;
    });
});
{% endhighlight %}
<div>&nbsp;</div>

<h5>JQuery - Easing</h5>

Several easing options were tried with <span class="terms">animate</span>, including linear. The JQuery easing plugin for Rails was also installed, but <span class="terms">animate</span> with a slow speed and the default <span class="terms">swing</span> function seemed sufficient for achieving the desired effect.  