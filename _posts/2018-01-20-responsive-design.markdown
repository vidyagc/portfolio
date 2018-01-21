---
layout: post
url: 2018-01-20-responsive-design
date: 2018-01-20
alt: image-alt
client: 
category: 
title: Responsive Design 
featured: 
introduction: This post is an overview of some of the tools / coding used to make <a href="/libertyhawk" target="_blank">Liberty Hawk</a> and <a href="/wikit" target="_blank">Wikit</a> responsive. The discussion of the responsive design elements could have been categorized in a number of ways. The sections below were chosen based on the where and how that design was most prominently relied on. Feel free to inspect the apps in different viewports to to see how the content is adapted on various media screen sizes. 
---

<h5>Navigation: top bar & side panel</h5>
<div class="page-content-text">
Liberty Hawk and Wikit use different nav menu styles, top and side respectively. Liberty Hawk uses a Bootstrap collapsing navigation bar. There was no customization on it and it uses the default breakpoint. Wikit, on the other hand, has a side navigation menu and employs several components whose properties are updated based on viewport size.  
</div>

<div class="row">
    <div class="col-md-12">
        <div class="wikit-resp-img" style="display:table; margin: auto">
        <img src="{{site.baseurl}}/img/blog/wikit-resp-mon.png" style="display:inline; margin-right:15px" class="img-responsive img-centered img-padded" alt="Wikit uncollapsed menu view">
        <img src="{{site.baseurl}}/img/blog/wikit-phone.png" style="display:inline" class="img-responsive img-centered img-padded" alt="Wikit collapsed menu view">
        </div>
    </div>
</div>

<div class="page-content-text">
First, there is a top bootstrap <span class="terms">navbar</span>. It doesn't contain menu items, but rather, contains a brand logo, and a logout link is displayed after a user is signed in. Menu items are displayed in a side navigation panel. Both <span class="terms">navbar-top</span> and the contents of <span class="terms">nav-side-menu</span> are updated at screen width ≤ 767, the portrait browser size for the iPad mini is 768. The mechanisms to hide each of the bars is as follows. For <span class="terms">navbar-top</span>, a CSS media query sets <span class="terms">display:none</span> at screens ≤ 767. 
</div>

<div class="file-path">app/assets/stylesheets/application.scss</div>
{% highlight scss %}
@media (max-width: 767px) {
...
    .navbar-top {
        display: none;
    }
...
}
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
<span class="terms">nav-side-menu</span> employs two divs with updating visibility based on screen width. These are <span class="terms">menu-list</span> and <span class="terms">brand</span>. It also contains an icon element that toggles the display of the <span class="terms">menu-list</span> content in screens ≤ 767 width. 
</div>

<div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight html %}
<div class="nav-side-menu">
    <div class="brand"><%= link_to "<u><h3 style='font-weight: bold; color:#80668a;'>Wikit <i class='fa fa-pencil' aria-hidden='true'></i></h3></u>".html_safe, welcome_index_path, class: "nav-logo" %></div>
    <i class="fa fa-bars fa-2x toggle-btn" data-toggle="collapse" data-target="#menu-content" ></i>
                  
    <div class="menu-list">
        <ul id="menu-content" class="menu-content collapse list-group">
        ...
    </div>
</div>
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
The content of <span class="terms">menu-list</span>, <span class="terms">menu-content</span>, is shown in screens size small and above. It is hidden in xs screens. The <span class="terms">menu-content</span> list is assigned the Bootstrap <span class="terms">collapse</span> class. By default, this content is hidden. A CSS media query, however, sets <span class="terms">display:block</span> for small and larger screens. Thus, <span class="terms">menu-content</span> is collapsed by default in xs screens. Correspondingly, <span class="terms">brand</span> and the icon element (used to toggle <span class="terms">menu-content</span> visibility) have <span class="terms">display:none</span> in small to larger screens, but this is set to <span class="terms">display:block</span> for xs screens. The toggle element has <span class="terms">data-target="#menu-content"</span>, and once, visible in the xs view, this toggle icon can be used to hide and show the <span class="terms">menu=content</span> for navigation. Because the value of the toggle is maintained when the screen is expanded beyond an xs width (e.g. you are in a large screen, and you reduce it to xs, then resize to small or larger), <span class="terms">menu-content</span> remains hidden when you resize to a larger screen. To ensure that the content is visible in the larger view in this scenario, <span class="terms">min-height</span> is set in a media query for width ≥ 768.   
</div>

<div class="row">
    <div class="col-md-6">
        <div class="file-path">app/assets/stylesheets/application.scss</div>
{% highlight scss %}
@media (min-width: 768px) {
...
    .nav-side-menu .menu-list .menu-content {
        display: block;
    }
}

...

.nav-side-menu .brand {
    display: none;
}

.nav-side-menu .toggle-btn {
    display: none;
}
{% endhighlight %}
    </div>
    
    <div class="col-md-6">
        <div class="file-path">app/assets/stylesheets/application.scss</div>
{% highlight scss %}
@media (max-width: 767px) {
...
    .nav-side-menu .toggle-btn {
        display: block;
    ...
    }
    .brand {
    ...    
        display: block;
    ...
    }
}

@media (min-width: 768px) {
    .nav-side-menu {
        min-height: 275;
    }
}
{% endhighlight %}
    </div>
</div>

<div style="margin-bottom:.75cm"></div>

<h5>Footer - <span style="color:#ec8013;">Wikit</span></h5>
<div class="page-content-text">
Because the footers for Wikit and Liberty Hawk contained little content (just a copyright line), the responsive design was based on changing their style or position as opposed to collapsing elements within them. In Wikit, a <span class="terms">navbar</span> was used in the place of a footer. By default, in xs views, there is no gutter padding, so the footer goes to the edge of the view. The <span class="terms">brand</span> div (with menu toggle), however, is contained in a column and does have gutters around it. To make the footer match the <span class="terms">brand</span> navigation bar, 15px left and right padding is added in xs viewports. 
</div>
<div class="page-content-text">
Although not a responsive design element, in order to keep the <span class="terms">footer</span> near the bottom of the view (with spacing below it being similar to the spacing about the top <span class="terms">navbar</span>), I used a <span class="terms">wrapper</span> with <span class="terms">min-height: 75vh;</span> to push the <span class="terms">footer</span> to the correct position.
</div>

<div class="row">
    <div class="col-md-6">
        <div class="file-path">app/assets/stylesheets/application.scss</div>
{% highlight scss %}
@media (max-width: 767px) {
..
    .navbar-bottom {
        margin-right:15px;
        margin-left:15px;
    }
}
{% endhighlight %}
    </div>

    <div class="col-md-6">
        <div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight erb %}
<div class="wrapper">
    <div class="col-md-10">
...
    <%= yield %>
    </div>
</div>
{% endhighlight %}
    </div>
</div>

<div style="margin-bottom:.75cm"></div>

<h5>Footer - <span style="color:#ec8013;">Liberty Hawk</span> - Responding to Scroll & Viewport</h5>
<div class="page-content-text">
Liberty Hawk's <span class="terms">footer</span> didn't require style updates based on view size, but the <span class="terms">position</span> is updated based on viewport and the scroll status of the window. Because some pages do not have content that covers 100% the height of the view, the footer (having a relative position by default), would sit at 60% (or wherever the content ended) view height. I wanted the footer to be at the bottom of the view in these cases, so <span class="terms">position: fixed;</span> is set in the stylesheet. Many of the views, however, do contain content that exceeds the view height and results in a scrollable window. In these cases, I did not want the footer, with <span class="terms">position: fixed;</span>, taking up real estate in the view. JavaScript was used to detect a scrollbar and update the <span class="terms">position</span> of the <span class="terms">footer</span>. 
</div>

<div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight javascript %}
var hasScrollbar = window.innerWidth > document.documentElement.clientWidth;
if (hasScrollbar) {
    var f = document.getElementById("footer");
    f.style.position="relative";
}
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
<span class="terms">position: fixed;</span> is the status for small and larger views, and the scrollbar detection method did not detect scrolling for browers on smaller devices. Since all the views in those devices have content past the view height anyway, <span class="terms">position: relative;</span> is set at the small breakpoint.
</div>

<div class="file-path">app/assets/stylesheets/application.scss</div>
{% highlight scss %}
@media screen and (max-width: 768px) {
...
    .footer {
        position: relative;
    }
}
{% endhighlight %}

<div style="margin-bottom:.75cm"></div>

<h5>Bootstrap Grid - <span style="color:#ec8013;">Wikit</span> - Mixed Columns & nesting</h5>
<div class="page-content-text">
Wikit employs mixed and nested columns to manage layout in medium and small viewports. In a small viewport (width 768px), I wanted to keep the plan option boxes and sign in/up forms on the same row, and drop the About Wikit box below them. In lieu of a code snippet, you can view the page's code in it's <a href="https://github.com/vidyagc/wikit/blob/master/app/views/welcome/index.html.erb" target="_blank">GitHub repository</a>.
</div>

<h5>Bootstrap Grid - <span style="color:#ec8013;">Liberty Hawk</span> - Mixed columns & push/pull</h5>
<div class="page-content-text">
<!--style="float:left; max-width:43%; text-align:justify; padding-right:10px">-->
Liberty Hawk uses various grid layout techniques, inlcuding mixed columns and push and pull in a number of views. One example of mixed colums is the user sign in view. In medium and larger viewports, there are equal column widths, containg the two forms and Account Benefits div. The most logical layout for small screens was to keep the sign up form and Account Benefits div next to eachother. This would not work for xs views, but as long as sufficient width existed to keep them in the same row, I wanted to do that. The border line between the Current User and New Account sections was used as a thematic division. A media query sets this border at the breakpoint at which these sections are on the same horizontal line (vs the New Account form dropping below).
</div>

<div class="row">
    <div class="col-md-12">
        <div class="wikit-resp-img" style="display:table; margin: auto">
        <img src="{{site.baseurl}}/img/blog/lh-ipad-hor.png" style="display:inline; margin-right:15px" class="img-responsive img-centered img-padded" alt="Wikit iPad mini horizontal view">
        <img src="{{site.baseurl}}/img/blog/lh-ipad-vert.png" style="display:inline" class="img-responsive img-centered img-padded" alt="Wikit iPad mini vertical view">
        </div>
    </div>
</div>

<!--<div style="float:left;">-->
<div class="row">
    <div class="col-md-6">
        <div class="file-path">app/views/devise/sessions/new.html.erb</div>
{% highlight erb %}
<div class="row col-width">
    <div class="col-md-3 col-sm-12 login-border">
        <h3>Current User</h3>
        ...
    </div>
    <div class="col-md-3 col-sm-4 mid-field">
        <h3>New Account</h3>
        ...
    </div>
    <div class="col-md-3 col-sm-4 auth" style="margin-left: 0px;"> 
        <!--account benefits-->
        ...
    </div>
</div>
{% endhighlight %}
    </div>
    
    <div class="col-md-6">
        <div class="file-path">app/assets/stylesheets/application.scss</div>
{% highlight scss %}
@media screen and (min-width: 992px) {
    .login-border {
        border-right: 2px solid #E0E0E0;
        min-width: 315px;
        margin-right: 15px !important;
    }
}
{% endhighlight %}
    </div>
</div>
<div>&nbsp;</div>
<!--</div>-->

<div class="page-content-text">
The Search page in Liberty Hawk uses push and pull to ensure that the search box is at the top of the screen in small viewports. In medium ones, it is to the right of the column containing search results. This is the view for signed in users. For not signed in users, the search box is only in the menu bar. 
</div>

<div class="file-path">app/views/searches/search.html.erb</div>
{% highlight erb %}
<div class="row page-row">
    <div class="col-md-4 col-md-push-8">
        <%= render 'form' %>
    </div>
    <div class="col-md-8 col-md-pull-4">
            ...
            <h2>Search Results</h2>
            ...
    </div>
</div>
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
Push and pull are also used on the landing page, to ensure that the Liberty Hawk logo (the center of three columns in md viewports) is at the top on small views. On the landing page, in small views, <span class="terms">&lt;hr class="star-primary" style="display:visible"&gt;</span> is also used to define thematic breaks between the vertically lined content sections.     
</div>

<div class="row">
    <div class="col-md-12">
        <div class="wikit-resp-img" style="display:table; margin: auto">
        <img src="{{site.baseurl}}/img/blog/lh-land-ipad-vert.png" style="display:inline; margin-right:15px" class="img-responsive img-centered img-padded" alt="Liberty Hawk iPad mini vertical view">
        <img src="{{site.baseurl}}/img/blog/lh-land-ipad-hor.png" style="display:inline" class="img-responsive img-centered img-padded" alt="Liberty Hawk iPad mini horizontal view">
        </div>
    </div>
</div>

<h5>Hopefully this post explains the reasoning behind some the layout choices for responsive design in Wikit and Liberty Hawk. Thank you for taking a look!</h5>