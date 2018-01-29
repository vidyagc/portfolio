---
layout: post
url: 2018-01-28-js-dynamic-content
date: 2018-01-28
alt: image-alt
client: 
category: 
title: JavaScript for Dynamic Content
title2: JS - Dynamic Content
featured: 
introduction: <a href="/libertyhawk" target="_blank">Liberty Hawk</a> and <a href="/wikit" target="_blank">Wikit</a> rely on JavaScript (and the JQuery library) for one of its more common uses (to show/hide content). The show/hide functions are used in conjunction with responsive design features to conserve space where possible on small and xs screens. Another use in <a href="/libertyhawk" target="_blank">Liberty Hawk</a> use was to detect a scrollbar on the window to update the position of the footer. As with most coding, there were alternative ways to achieve this functionality, but these implementations seemed efficient (lines of code, ease of implementation, etc.). 
---

<div class="page-content-text">
Neither Liberty Hawk nor Wikit required much DOM traversal. In both apps, JavaScript and the JQuery library are used to make elements visible on user request. <span class="terms">onclick</span> is used to trigger JavaScript that dynamically changes element properties. 
</div>

<h4><u>Liberty Hawk</u></h4>
<div style="margin-bottom:.75cm"></div>
<h5>Toggle Display & TextContent</h5>
<div class="page-content-text">
When a user is signed in on Liberty Hawk, the search page has a history panel that shows the user’s last 10 searches. There are two history panels used (each for a different view
width). One panel is visible only in view width ≥ 769px. The other panel, <span class="terms">panel-history-small</span>, is only visible in view width ≤ 768px. The display of these panels is updated at the breakpoints using CSS. <span class="terms">panel-history-small</span> can have the display of its body contents (<span class="terms">history</span>) toggled. By default, <span class="terms">history</span> is not displayed. A link in the <span class="terms">panel-heading</span> allows users to show and hide it. 
</div>

<div class="row">
    <div class="col-md-12">
        <div class="resp-img-page" style="display:table; margin: auto">
        <img src="{{site.baseurl}}/img/blog/lh-resp-mon-search.png" style="display:inline; margin-right:15px" class="img-responsive img-centered img-padded" alt="Wikit uncollapsed menu view">
        <img src="{{site.baseurl}}/img/blog/lh-phone-search-hide.png" style="display:inline" class="img-responsive img-centered img-padded" alt="Wikit collapsed menu view">
        </div>
    </div>
</div>

<div class="file-path">app/views/searches/_form.html.erb</div>
{% highlight erb %}
<div class="panel panel-default panel-history-small" style="max-width: 350px">
    <div class="panel-heading">
      <div id="historyHeader">Last 10 searches Show</div>
    </div>
    <div class="panel-body">
      <div id="history">
        <% current_user.searches.order('created_at DESC').each do |search| %>
    
          <table width="100%">
            <tr>
              <td align="left">
                <%= link_to controller: "searches", action: "search", method: "get", subject: search.metadata do %><u><%= search.metadata %></u><% end %>
              </td>
              <td align="right">
                <%= search.created_at.to_date %>
              </td>
            </tr>
          </table>
    
        <% end %>
      </div>
    </div>
</div>
{% endhighlight %}
<div>&nbsp;</div>

<div class="page-content-text">
Javascript is used to show/hide history and correspondingly update <span class="terms">historyHeader</span>. <span class="terms">toggleHistory()</span> updates the <span class="terms">display</span> of<span class="terms">history</span>, and the <span class="terms">textContent</span> of <span class="terms">historyHeader</span>. The helper method <span class="terms">lastWord()</span> updates the last word of <span class="terms">historyHeader</span>’s text content into a link with an <span class="terms">onclick</span> event to toggle the display. In the code snippet below, the functions are commented to explain how they work. 
</div>

<div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight javascript %}
// function to get last word of search history panel heading, and apply css and an onclick function to it. 
function lastWord() {
  $('div#historyHeader').html(function(){	
  	// separate the text by spaces
  	var text= $(this).text().split(' ');
  	// drop the last word and store it in a variable
  	var last = text.pop();
  	// join the text back and if it has more than 1 word add the span tag
  	// to the last word
  	return text.join(" ") + (text.length > 0 ? ' <p class="last" style="float:right" onclick="toggleHistory();">'+last+'</p>' : last);   
  });
}

// function to toggle display of the history panel body and heading content
function toggleHistory() {
  var x = document.getElementById("history");
  var z = document.getElementById("historyHeader");
  if (x.style.display === "none" || z.textContent === 'Last 10 searches Show') {
      x.style.display = "block";
      z.textContent="Last 10 searches Hide";
  } 
  else {
      x.style.display = "none";
      z.textContent="Last 10 searches Show";
  }
  
  // call of last word function to update the last word of the history panel heading (make it a link)
lastWord();
}

// call of last word function to update the last word of the history panel heading on page load
jQuery(document).ready(lastWord());
{% endhighlight %}
<div>&nbsp;</div>

<h5>Responding to Scroll & Viewport</h5>
<div class="page-content-text">
The use of JavaScript to detect and respond to a scrollable view is discussed in <a href="/2018/01/20/responsive-design/#scrollbar">Responsive Design</a>. 
</div>

<h4><u>Wikit</u></h4>
<div style="margin-bottom:.75cm"></div>
<h5>Show/Hide Elements</h5>
<div class="page-content-text">
As mentioned in Responsive Design, at breakpoint ≤ 767px, the Devise forms on the landing page are displayed at the top of the view, and their display is toggled with buttons. 
</div>

<div class="row">
    <div class="col-md-12">
        <div class="resp-img-page" style="display:table; margin: auto">
        <img src="{{site.baseurl}}/img/blog/wikit-resp-mon.png" style="display:inline; margin-right:15px" class="img-responsive img-centered img-padded" alt="Wikit uncollapsed menu view">
        <img src="{{site.baseurl}}/img/blog/wikit-phone-toggle.png" style="display:inline" class="img-responsive img-centered img-padded" alt="Wikit collapsed menu view">
        </div>
    </div>
</div>

<div class="page-content-text">
The toggle feature required several considerations.
    <div style="margin-bottom:.25cm"></div>
    <ol class="ol-blog">
    <li><span class="li-col">Displaying the forms and hiding the toggle bottons at breakpoint ≥ 768px</span></li> 
    <li><span class="li-col">Hiding the forms and displaying the toggle buttons at breakpoint ≤ 767px</span></li> 
    <li><span class="li-col">Showing a form when the user is redirecting to the landing page</span></li>
    </ol>
</div>

<h5><span style="color:#ec8013;">1. & 2.</span> Displaying the forms according to breakpoint</h5> 
<div class="page-content-text">
The two forms are contained inside <span class="terms">tab-content</span> elements. These are the elements whose display is toggled. First, the forms are always displayed (and the toggle buttons <b><i>hidden</i></b>) at breakpoint ≥ 768px, and vice versa at breakpoint ≤ 767px. Because this display based on screen width is done in JavaScript vs CSS, <span class="terms">&lt;body onresize="toggleTabs()"&gt;</span> is used to update the display when the screen size is changed. 
</div>

<h5 class="code-header">HTML for buttons (to toggle forms) & CSS to update their display</h5>
<div class="file-path">app/views/welcome/index.html.erb</div>
{% highlight erb %}
<div class="col-md-4 col-sm-6 signin-top" style="margin-bottom: 15px">
    <table style="width:100%" id="tab-btns" style="display:none;">
      <tr>
        <td align="left"><div id="tab1" class="tab"><button type="button" class="btn btn-default task-btn"><i class="fa fa-sign-in" aria-hidden="true"></i>Sign In</button></div></td>
        <td align="right"><div id="tab2" class="tab"><button type="button" class="btn btn-default task-btn"><i class="fa fa-user" aria-hidden="true"></i>New User</button></div></td>
      </tr>
    </table>
    <div class="center-div">  
        <%= render "devise/sessions/form" %>
    </div>
</div>
{% endhighlight %}
<div>&nbsp;</div>

<div class="file-path">app/assets/stylesheets/application.scss</div>
{% highlight scss %}
@media (max-width: 767px) {
  #tab-btns {
    display: block;
  }
}

@media (min-width: 768px) {
    #tab-btns {
        display: none;
    }
    #signin-h {
        margin-top:0;
    }
}
{% endhighlight %}
<div>&nbsp;</div>

<h5 class="code-header">HTML for forms & JavaScript to update and toggle their display</h5>
<div class="file-path">app/views/devise/sessions/_form.html.erb</div>
{% highlight erb %}
<div id="tab1show" class="tab-content">
    <div>
        <h3 id="signin-h">Sign In</h3>
        ...
        <!-- sign in form -->
        ...
    </div>
</div>

<div id="tab2show" class="tab-content">
    <div>
        <h3>New User</h3>
        ...
        <!-- sign up form -->
        ...
    </div>
</div>
{% endhighlight %}
<div>&nbsp;</div>

<div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight javascript %}
function toggleTabs() {
    var $contents = $('.tab-content');
    // check if view width is <= 767px
    if (window.matchMedia('(max-width: 767px)').matches) {
        // if view width is <= 767px, hide all of the tab-content elements
        $contents.hide();
        // show a tab-content when its corresponding button is clicked. 
        $('.tab').click(function() {
            // retreives the ID of the tab-content element based on the ID of the clicked div and shows it.
            var $target = $('#' + this.id + 'show').show();
            // hides the tab-content elements whose corresponding button was not clicked (otherwise multiple elements can show at once)
            $contents.not($target).hide();
        });
    }
    else {
        // if view width is >= 768px, show all of the tab-content elements
        $contents.show();
    }
 }
 
// run toggleTabs() on window load
toggleTabs();
{% endhighlight %}
<div>&nbsp;</div>

<h5><span style="color:#ec8013;">3.</span> Display form when redirecting to landing page</h5> 
<div class="page-content-text">
The password recovery and resend confirmation pages have links to the log in and sign up forms. These links lead back to the landing page. I wanted the respective forms to show when each link is clicked. This is achieved by creating a global variable called <span class="terms">showTab</span>, and setting the value of the variable in an <span class="terms">onclick</span> event for each link. Using <span class="terms">$('#tab2show').show()</span> or <span class="terms">$('#tab1show').show()</span> in the <span class="terms">onclick</span> does not work, as the event needs to fire after the redirect. Instead of using a method for triggering the event after the redirect, <span class="terms">showTab</span> is set, and used to show the corresponding <span class="terms">tab-content</span> (sign in or sign up form).</div>

<h5 class="code-header">showTab variable declaration & conditional to show element</h5>
<div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight javascript %}
var showTab;
if (showTab==1)
{
    $('#tab2show').show();
}
else if (showTab==2)
{
    $('#tab1show').show();
}
else 
{
    // hide all tab-content elements when the landing page is redirected to (showTab is set to 0 in the an onclick on links to landing page)
    $('#tab1show').hide(); 
    $('#tab2show').hide();
}
{% endhighlight %}
<div>&nbsp;</div>

<h5 class="code-header">redirect with onclick to set showTab value</h5>
<div class="file-path">app/views/devise/shared/_links.html.erb</div>
{% highlight erb %}
<%- if controller_name != 'sessions' %>
  <%= link_to "Log in", root_path(resource_name), :onclick => "showTab=2" %><br />
<% end -%>

<%- if devise_mapping.registerable? && controller_name != 'registrations' %>
  <%= link_to "Sign up", root_path(resource_name), :onclick => "showTab=1" %><br />
<% end -%>
{% endhighlight %}
<div>&nbsp;</div>

<div class="page-content-text">
When a user leaves the landing page, after <span class="terms">showTab</span> has been set from a log in or sign up redirect link, I do not want the form to remain displayed when they go back to the landing page. There were several was to do this, but I just chose to set <span class="terms">showTab=0</span> in an <span class="terms">onclick</span> event in links that redirect to the landing page. 
</div>

<div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight erb %}
<div class="brand"><%= link_to "<u><h3 style='font-weight: bold; color:#80668a;'>Wikit <i class='fa fa-pencil' aria-hidden='true'></i></h3></u>".html_safe, welcome_index_path, class: "nav-logo", :onclick => "showTab=0" %></div>
...
            <li class="list-group-item mid-list-item">
                <%= link_to "<i class='fa fa-home' aria-hidden='true'></i> Home / Sign in".html_safe, welcome_index_path, :onclick => "showTab=0" %>
            </li>
{% endhighlight %}
<div>&nbsp;</div>

<h5>Hopefully this post explains how JavaScript was used in conjunction with responsive design in Wikit and Liberty Hawk. Thank you for taking a look!</h5>