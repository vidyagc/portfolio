---
layout: post
url: 2018-01-16-devise-customization
date: 2018-01-16
alt: image-alt
project-date: month 4-dig-year
client: 
category: 
title: Rails - Devise Customization 
featured: true
introduction: Devise is a complete MVC authentication solution for Rails. It can be used in lieu of building authentication from scratch. This post is an overview of Devise customization solutions that were used in <a href="/wikit" target="_blank">Wikit</a>. Some of the customizations below were also used in <a href="/libertyhawk" target="_blank">Liberty Hawk</a>, but the discussion and code snippets pertain to <a href="/wikit" target="_blank">Wikit</a>.
---

<h5>Devise Customization Resources</h5>
<div class="page-content-text">
There are a number of free resources that discuss customization of Devise, including <a href="https://github.com/plataformatec/devise/wiki" target="_blank">Devise Wiki</a>, <a href="http://railscasts.com/episodes/209-devise-revised?autoplay=true" target="_blank">RailsCasts #209</a> and <a href="http://railscasts.com/episodes/210-customizing-devise" target="_blank">RailsCasts #210</a>. The RailsCasts episodes cover the following topics.
<p>
<ol class="ol-blog">
<li><span class="li-col">Including and removing modules (e.g. confirmable and validatable)</span></li>
<li><span class="li-col">Configuring Devise messages in devise.en.yml</span></li> 
<li><span class="li-col">Customizing Devise views by using templates to override them – generating these templates via the devise:views generator.</span></li>
<li><span class="li-col">Customizing authentication routing by adding options to the devise_for call in routes.rb</span></li> 
<li><span class="li-col">Customizing fields used for authentication – e.g. using a username field instead of the default email field.</span></li>
<li><span class="li-col">Customizing validations when a user signs up for an account by changing configuration options in devise.rb.</span></li> 
</ol>
</p>
</div>

<h5>Beyond Layouts</h5>
<div class="page-content-text">
What if, instead of just changing the styles of existing forms or <a href="https://github.com/plataformatec/devise/wiki/How-To:-Create-custom-layouts" target="_blank">adding additional layouts</a>, you want to change where the forms are rendered in your application (e.g. you want sign up and sign in forms located inside another view)? And what are the considerations that follow this new placement? A failed registration will still redirect to Devise's default sign up path (not the new form location you implemented) unless these redirects are updated via a controller. And how do you make sure error messages are displayed on your new view. When I wanted to render devise sign in and sign up forms as partials on the welcome page of my application, <a href="/wikit" target="_blank">Wikit</a>, this was the problem and follow up customization issues that needed to be addressed. The efficacy of the following solutions are limited to the scope in which Devise was used in that application. It has not been tested beyond that (e.g. with models that inherit from another Devise model).  
</div>
<div class="page-content-text">
On his <a href="https://pupeno.com/2016/04/26/show-a-devise-log-in-or-sign-up-forms-in-another-page/" target="_blank">blog</a>, J. Fernández offers a solution for showing Devise forms on another page. <a href="https://github.com/plataformatec/devise/wiki/How-To:-Display-a-custom-sign_in-form-anywhere-in-your-app" target="_blank">Devise wiki</a> shows it as well, with some revisions. As Fernández suggests, I found the use of a partial as the best way to use the form on another view.
</div>

<div class="file-path">app/views/welcome/index.html.erb</div>
{% highlight erb %}
<div class="col-md-4 col-sm-6">
    <a name="signin"></a>
    <div class="center-div">  
        <%= render "devise/sessions/form" %>
    </div>
</div>
{% endhighlight %}

<div>&nbsp;</div>

<div class="file-path">app/views/devise/sessions/_form.html.erb</div>
{% highlight erb %}
<div>
<h3 style="margin-top:0">Sign In</h3>
<%= form_for(:user, :url => session_path(:user), :html => { :class =>
'auth-form-for'}) do |f| %>
    <p><i class="fa fa-envelope-o" aria-hidden="true"></i><%= f.text_field :email, placeholder: "email", class: "auth-form" %></p>
    <p><i class="fa fa-lock" aria-hidden="true"></i><%= f.password_field :password, autocomplete: "off", placeholder: "password", class: "auth-form" %></p>
    <p><%= f.check_box :remember_me %>&nbsp;<%= f.label :remember_me %></p>
    <p><%= f.submit 'Sign in' %></p>
    <p><%= link_to "Forgot your password?", new_password_path(:user) %></p>
    <p><%= link_to "Didn't receive confirmation instructions?", new_user_confirmation_path(:user) %></p>
<% end %>
</div>

<div>
<h3>New User</h3>
<%= form_for(:user, :url => registration_path(:user), :html => { :class =>
'auth-form-for'}) do |f| %>
    <p><i class="fa fa-envelope-o" aria-hidden="true"></i><%= f.text_field :email, placeholder: "email", class: "auth-form" %></p>
    <p><i class="fa fa-lock" aria-hidden="true"></i><%= f.password_field :password, autocomplete: "off", placeholder: "password", class: "auth-form" %></p>
     <% if @minimum_password_length %>
     <em>(<%= @minimum_password_length %> characters minimum)</em>
     <% end %>
    <p><i class="fa fa-lock" aria-hidden="true"></i><%= f.password_field :password_confirmation, autocomplete: "off", placeholder: "confirm password", class: "auth-form" %></p>
    <p style="margin-top:15px"><%= f.submit 'Sign up' %></p>
<% end %>
</div>
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
The second part of this solution, addressed by Fernández, involves resource mapping to ensure that the methods relied on by the forms as accessible. I placed them in <span class="terms">ApplicationController</span>.
</div>

<h5>Consistent User Flow</h5>
<div class="page-content-text">
The solution above allowed Devise methods to be used from the partial view. The remaining issues, however, were maintaining consistency in the user flow in the event of failures, and handling error messages. With the above implementation, a failed authentication or registration still redirects to the default Devise paths/views. But if a user fails to authenticate or sign up from the welcome page, they should be redirected to the welcome page and see the error messages for the failure there. 
</div>

<div class="page-content-text">
In order to customize the redirect and error message display for failed registration, you can subclass <span class="terms">Devise::RegistrationsController</span> and override the <span class="terms">create</span> action. The default Devise views use a call to <span class="terms"><%= devise_error_messages! %></span> to display error messages on the page<span class="terms">resource.errors</span>, but I wanted to display them to <span class="terms">flash[:danger]</span>. The value for <span class="terms">flash[:danger]</span> is set inside <span class="terms">create</span>, using the <span class="terms">map</span> method on <span class="terms">resource.errors</span> to display the items in list form. 
</div>

<div class="file-path">app/controllers/registrations_controller.rb</div>
{% highlight ruby %}
class RegistrationsController < Devise::RegistrationsController

    def create
        build_resource(sign_up_params)
    
        if resource.save
            yield resource if block_given?
            if resource.active_for_authentication?
                set_flash_message :notice, :signed_up if is_flashing_format?
                sign_up(resource_name, resource)
                respond_with resource, location: after_sign_up_path_for(resource)
            else
                set_flash_message :notice, :"signed_up_but_#{resource.inactive_message}" if is_flashing_format?
                expire_data_after_sign_in!
                respond_with resource, location: after_inactive_sign_up_path_for(resource)
            end
        else
            clean_up_passwords resource
            flash[:danger] = resource.errors.full_messages.map { |error| "<li>#{error}" }.join("</li>")
            redirect_to root_path
        end
    end
...
{% endhighlight %}
<div>&nbsp;</div>

<div class="page-content-text">
Also, because <span class="terms">html_safe</span> is not preserved from the controller to the view, it is called in <span class="terms">application.html.erb</span> instead, <span class="terms"><%= flash[:danger].html_safe %></span>. Redirects after a failed authentication needed to be customized as well. This can be done with a <a href="https://github.com/plataformatec/devise/wiki/How-To:-Redirect-to-a-specific-page-when-the-user-can-not-be-authenticated" target="_blank">CustomFailure class</a>. As I am using <span class="terms">flash[:danger]</span> for error messages, that is set in <span class="terms">def respond</span>.
</div>

<div class="file-path">app/controllers/registrations_controller.rb</div>
{% highlight ruby %}
class CustomFailure < Devise::FailureApp

  def respond
    if http_auth?
      http_auth
    else
        flash[:danger] = i18n_message
        redirect_to welcome_index_path
    end
  end
end
{% endhighlight %}
<div>&nbsp;</div>

<div class="page-content-text">
Other customizations included the following: styling the <span class="terms">passwords/new</span> and <span class="terms">confirmations/new</span> views to match (but not duplicate) the style of the sign in and sign up forms; removing messages for successful sign up and sign in, by editing them in <span class="terms">devise.en.yml</span>; and editing paths for certain links in <span class="terms">shared/_links</span>. Additional controllers were also implemented to customize redirects on password recovery and resending confirmation actions.
</div>

<div class="file-path">app/controllers/confirmations_controller.rb</div>
{% highlight ruby %}
def after_confirmation_path_for(resource_name, resource)
  if signed_in?(resource_name)
    account_management_path(resource)
  else
    root_path(resource_name)
  end
end
{% endhighlight %}
<div>&nbsp;</div>

<h5>I hope this post was useful in understanding the how and why of the customized Devise implementations in this portfolio's apps. Even better if you learned something new about using Devise forms on different pages in your app, and correspondingly handling paths and error messages on failures.</h5>
