---
layout: work
title: Liberty Hawk
permalink: libertyhawk
id: 3
img: libertyhawk-400.png
img2: libertyhawk-mon.png
alt: Liberty Hawk logo, links to Liberty Hawk application writeup
alt2: Liberty Hawk app view
project-date: December 2017
project-name: Liberty Hawk
client: Start Bootstrap
category: Web Development
description: a congressional bill search application that uses the ProPublica API ‘Search Bills’ endpoint.   
---

<h4>Upcoming Overview and Refactoring</h4>
<div class="page-content-text">
<ul>
<li>A complete project writeup will be posted by the end of the first week of February, For now, you can read about the app's responsive design features in the blog post, <a href="/2018/01/20/responsive-design/">Responsive Design</a>, and its dynamic content in <a href="/2018/01/28/js-dynamic-content/#">JavaScript for Dynamic Content</a>.</li>
<li>The code is currently being refactored for resourceful routing and other Rails best practices and efficiencies. If you see anything in the GitHub repo that you would like to discuss (e.g. "How are you planning on improving the following items?"), just contact me, and I'm happy to talk.</li>
</ul>
</div>

<h4>DESCRIPTION</h4>
<div class="page-content-text">
A congressional bill search application that uses the ProPublica API ‘Search Bills’ endpoint. Users can search bills while logged in or search just as site visitors. Logged in users can save bills (favorites), see a history of their past 10 searches, sort bills by multiple categories, and their most recent search results are persisted (you can see them when you log back in to a new session). 
</div>

<h5>UPCOMING FEATURE</h5>
<div class="page-content-text">
Foldering that allows users to create named folders and organize their saved bills into them.  
</div>

<h5>CODER COMMENT</h5>
<div class="page-content-text">
Creating a Ruby on Rails app with a RESTful API was interesting. Constructing resources for two use cases (user not signed in and signed in) involved multiple overlapping considerations: first, when did data need to be persisted and when did it not; second, which views does each use case need or need to be limited from, based on the purpose(s) of that view, etc. Furthermore, view design for persisted versus non-persisted data of the same object class required different controller methods or actions, partials for differing object access abilities, etc. These are some of the points that will be covered in the upcoming writeup sections. 
</div>

<h4>LINK</h4>
<div class="page-content-text">
<a href="https://libertyhawk.herokuapp.com/" target="_blank">Live App</a>&nbsp;&nbsp;<span style="font-variant:small-caps">please read <span style="color:#ec8013"><b>testing</b></span> below before trying app</span><br>
<a href="https://github.com/vidyagc/libertyhawk" target="_blank">GitHub Repo</a>
</div>

<h4>TESTING</h4>
<div class="page-content-text">
<ul>
<li>Two-factor authentication is enabled. You will need to confirm an email account before signing in to the application. Confirmation emails can take a few minutes to be delivered. If you do not see one within five minutes, please check your spam folder.</li>
<li>For guidance on running queries (searches), click the orange info button (<i class="fa fa-info-circle" aria-hidden="true" style="color: #e6902a;"></i>) next to the search box. It will open a panel that explains results and how to use mutliples word searches.</li>
</ul>

<h5>FEATURES</h5>
<ul>
<li>Authenticated user accounts</li>
<li>Sign in and do the following</li>
<ul>
<li>Search bills</li>
<li>Sort bills by three different criteria (Title, Date Introduced, and Active Status</li>
<li>Save bills</li>
<li>Unsave bills</li>
<li>Re-run any of your 10 most recent searches via the links in the search history panel</li>
</ul>
<li>Search bills when not signed in</li>
</ul>
</div>

<h4>Responsive design</h4>
<div class="page-content-text">
Responsive design was employed on this app. The landing page, sign in, and search views employ it to reorder content for logic and prominence. The bill and saved bill show pages use it for aligning content, but also to resize, or <span class="terms">scale</span>, objets that are larger than the screen width at given breakpoints. These topics are discussed in <a href="/2018/01/20/responsive-design/">Responsive Design</a>.
</div>

<h4>Dynamic Content</h4>
<div class="page-content-text">
JavaScript was used to show and hide content on small screens. This is discussed in <a href="/2018/01/28/js-dynamic-content/">JavaScript for Dynamic Content</a>.
</div>

<h4>JQuery Animate</h4>
<div class="page-content-text">
JQuery animated scroll was used to help users easily and smoothly get back to the top of the page on small screens. This is discussed in <a href="/2018/02/04/jquery-animated-scroll/">JQuery - Animated Scroll</a>.
</div>
