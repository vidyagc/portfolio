---
layout: work
title: Wikit
permalink: wikit
id: 1
img: wikit-400.png
img2: wikit-mon.png
alt: image-alt
project-date: July 2017
project-name: Wikit
client: Start Bootstrap
category: Web Development
description: a production quality SaaS app that allows users to create their own wikis
---

<h4>DESCRIPTION</h4>
<div class="page-content-text">
A production quality SaaS application built on Ruby on Rails that allows users to create public and private markdown wikis and share them with other collaborators. A step-by-step overview of implementation will not be outlined below, but rather, discussion will focus on key components including, authentication, associations, file attachment, Markdown incorporation, Stripe integration, and scope/authorization. There will also be a cursory overview of decisions regarding user flow. The write-up assumes basic familiarity with the technology on the part of the reader. Environment setup is outlined in README in the GitHub repository, and is not covered here. TDD (Test-Driven Development) was not used for this app, but I have used it in others with the RSpec framework.
</div>
<h5>UPCOMING FEATURES</h5>
<div class="page-content-text">
<ul>
<li>Email notification to collaborators about being added to collaborate on a wiki.</li>
<li>Sign in with user name, not just email address.</li>
</ul>
</div>

<h5>CODER COMMENT</h5>
<div class="page-content-text">
Collaborative and educational software is of particular interest to me. It goes without saying that information availability and sharing is the greatest social benefit the internet has offered, and I valued the opportunity to explore one corner of technologies used for these applications. Because of this app’s functionality, including multiple user roles and a subscription option, user flow took consideration. Determining paths and redirects after actions informed the app’s features. 
</div>

<h4>LINKS</h4>
<div class="page-content-text">
<a href="https://vn-wikit.herokuapp.com/" target="_blank">Live App</a>&nbsp;&nbsp;<span style="font-variant:small-caps">please read <span style="color:#ec8013"><b>testing</b></span> below before trying app</span><br>
<a href="https://github.com/vidyagc/wikit" target="_blank">GitHub Repo</a>
</div>

<h4>TESTING</h4>
<div style="margin-bottom:.75cm"></div>
<div class="page-content-text">
<h5>CONFIGURATION</h5>
<ul>
<li>Two-factor authentication is enabled. You will need to confirm an email account before signing in to the application. Confirmation emails can take a few minutes to be delivered. If you do not see one within five minutes, please check your spam folder.</li>
<li>Stripe Test Data (used for the Account Upgrade feature)
<ul>
<li><u>Email</u>: choose any email address</li>
<li><u>Card Number</u>: <span class="terms">4242 4242 4242 4242</span> or any of the test card numbers <a href="https://stripe.com/docs/testing#cards" target="_blank">here</a>.</li>
<li><u>Expiration</u>: choose almost any month and year in the future</li>
<li><u>CVC</u>: choose any three numbers</li>
</ul></li>
</ul>
</div>
<div class="page-content-text">
<h5>FEATURES</h5>
<ul>
<li>Authenticated user accounts (two-factor authentication is currently disabled for ease of testing)</li>

<li>User accounts with two plan options
<ul>
<li>Free/Standard (default) account – create public wikis</li>
<li>Premium account – create public or private wikis</li>
</ul>
</li>

<li>Upgrade a user account (from the Free plan to a Premium plan)</li>
<li>Downgrade a user account (from a Premium plan to a Free plan)</li>
<li>Create Markdown wikis with two privacy settings
<ul>
<li>Public (default) – can be viewed and edited by any user</li>
<li>Private (Premium user feature) – can only be viewed and edited by the wiki author, or any user added to the wiki as a collaborator</li>
</ul>
</li>
<li>Browse wikis</li>
<li>Edit wikis</li>
<li>Delete wikis</li>
<li>Add collaborators to private wikis</li>
<li>Collaborators can edit private wikis to which they have been added</li>
</ul>
</div>

<div class="page-content-text">
<h5>TASKS AND USER FLOW</h5>
The following is a set of tasks and instructions that are recommened to cover all major app features. A video overview of the app will be uploaded in the future for those who would rather watch instructions versus read them. It is recommened that you proceed through the tasks sequentially to avoid missing steps that are relied on in later tasks.

<div style="margin-bottom:.75cm"></div>

<table style="width:100%">
  <tr>
    <td><div id="tab1" class="tab"><button type="button" class="btn btn-sm btn-default task-btn">Task 1</button></div></td>
    <td><div id="tab2" class="tab"><button type="button" class="btn btn-sm btn-default task-btn">Task 2</button></div></td>
    <td><div id="tab3" class="tab"><button type="button" class="btn btn-sm btn-default task-btn">Task 3</button></div></td>
    <td><div id="tab4" class="tab"><button type="button" class="btn btn-sm btn-default task-btn">Task 4</button></div></td>
    <td><div id="tab5" class="tab"><button type="button" class="btn btn-sm btn-default task-btn">Task 5</button></div></td>
  </tr>
</table>

<br />

<div id="tab0show" class="tab-content"></div>

<div id="tab1show" class="tab-content">
<h5 class="sub-head">TASK 1 – VIEW AND CREATE PUBLIC WIKIS</h5><span id="tab0" class="tab" style="margin-left:30px;"><button type="button" class="btn btn-sm btn-info hide-btn">Hide</button></span><br />
<div style="margin-bottom:.25cm"></div>
<ol class="task-list">
<li>Use either of the “Sign Up” links on the Home page to create an account. Note down the email address and password you enter, as they will need to be used again after a logout. This will be the <b>first</b> account you use.
<ul>
<li>By default, this is a free (Standard) account that allows creating public wikis</li>
</ul>
</li>
<li>Use the “Browse all Wikis” link to go to the wikis page. The list of wikis on the wikis page are public wikis only. Private wikis do not appear here.</li>
<li>Click on any of the wiki links to edit or delete the wiki.</li>
<li>Use the “Create a Wiki!” link in the side menu, or on the “My Wikis” page to create a new Markdown wiki, with title, body, and image.</li>
<li>A link to a Markdown Cheat Sheet is available on the New Wiki form page.</li>
<li>Use the “My Wikis” link to view wikis you have authored. Click on any of the wiki links to edit or delete the wiki.</li>
<li>Use the “Browse all Wikis” link to see your wiki(s) in the public wikis list.</li>
</ol>
</div>

<div id="tab2show" class="tab-content">
<h5 class="sub-head">TASK 2 – CREATE PRIVATE WIKIS</h5><span id="tab0" class="tab" style="margin-left:30px;"><button type="button" class="btn btn-sm btn-info hide-btn">Hide</button></span><br />
<div style="margin-bottom:.25cm"></div>
<ol class="task-list">

<li>Use the “Upgrade” link in the top navigation bar OR on your “My Account” page to  upgrade to a Premium account.
<ul>
<li><u>Email</u>: choose any email address</li>
<li><u>Card Number</u>: <span class="terms">4242 4242 4242 4242</span> or any of the test card numbers <a href="https://stripe.com/docs/testing#cards" target="_blank">here</a>.</li>
<li><u>Expiration</u>: choose almost any month and year in the future</li>
<li><u>CVC</u>: choose any three numbers</li>
</ul>
</li>

<li>Use the “Create a Wiki!” button to create a new wiki.
<ul>
<li>In the new wiki, select the option for “Make private”, and save the wiki.</li>
</ul>
</li>

<li>Use the “Browse all Wikis” link to see your wikis in the list.</li>
<li>Use the “Log out” link to log out of your account. </li>
<li>Use the “Sign Up” link to create a <b>second</b> account. Note down the email address and password you enter, as they will need to be used again after a logout.</li>
<li>Once logged in to the <b>second</b> account, use the “Browse all Wikis” link to view the list of public wikis (verify that you CANNOT see the private wikis created in the <b>first</b> account).</li>
</ol>
</div>

<div id="tab3show" class="tab-content">
<h5 class="sub-head">TASK 3 – ADD A COLLABORATOR TO A PRIVATE WIKI</h5><span id="tab0" class="tab" style="margin-left:30px;"><button type="button" class="btn btn-sm btn-info hide-btn">Hide</button></span><br />
<div style="margin-bottom:.25cm"></div>
<ol class="task-list">
<li>Log back into your <b>first</b> account.</li>
<li>Use the “My Wikis” link to view your wikis, and click on the link for the private wiki you created.</li>
<li>On the page for your private wiki, enter the email address for the <b>second</b> account you created, in the text box for “Add a Collaborator”. Then click “Submit a Collaborator”.</li>
<li>Verify that you can see the address listed in the Collaborators table.</li>
</ol>
</div>

<div id="tab4show" class="tab-content">
<h5 class="sub-head">TASK 4 – EDIT  A WIKI AS A COLLABORATOR</h5><span id="tab0" class="tab" style="margin-left:30px;"><button type="button" class="btn btn-sm btn-info hide-btn">Hide</button></span><br />
<div style="margin-bottom:.25cm"></div>
<ol class="task-list">
<li>Log out of your account, and sign back in with your <b>second</b> account.</li>
<li>Use the “Browse all Wikis” link to verify that you can see all public wikis AND the private wiki on which you are a collaborator.</li>
<li>Use the “My Wikis” link to see the wiki on which you are a collaborator.</li>
<li>Click on the link for the wiki on which you are a collaborator. Verify that you can edit this wiki.</li>
</ol>
</div>

<div id="tab5show" class="tab-content">
<h5 class="sub-head">TASK 5 – DOWNGRADE AN ACCOUNT</h5><span id="tab0" class="tab" style="margin-left:30px;"><button type="button" class="btn btn-sm btn-info hide-btn">Hide</button></span><br />
<div style="margin-bottom:.25cm"></div>
<ol class="task-list">
<li>Log out of the <b>second</b> account, and log back in with your <b>first</b> account.</li>
<li>Use the “My Account” link in the side menu to see your account page.</li>
<li>Read the Downgrade Warning and click on the “Downgrade” button to downgrade your account back to Standard. You will have to click “OK” on a pop-up warning before the Downgrade is submitted.</li>
<li>Use the “My Wikis” link to verify that your private wiki no longer has collaborators or an add collaborators option (it is now public).</li>
<li>Log out of this account. Once logged out, use the “Browse all Wikis” link to verify that your once private wikis are now public.</li>
</ol>
</div>
</div>

<h4>Authentication</h4>
<div class="page-content-text">
After creating the Rails app structure, I updated the <span class="terms">Gemfile</span> with, among other gems, <span class="terms">sqlite3</span> for the Development database and <span class="terms">pg</span>, Heroku Postgres database, for the Production environment. After generating the Welcome Controller and related views, authentication was added using <span class="terms">Devise</span>. This app only required one <span class="terms">Devise</span> model, <span class="terms">User</span>, and views, redirects, and error messages were customized. Customization included overriding the default <span class="terms">RegistrationsController</span> and a creating a <span class="terms">CustomFailure</span> class to redirect paths after failed authentications or account creation. A <span class="terms">_form.html.erb</span> partial with customized Devise forms was rendered on the Welcome page, and resource mapping was used in the <span class="terms">ApplicationController</span> to allow these forms to access Devise variables and methods. The full implementation of this customization will not be covered here, but rather discussed in a separate blog entry that will be posted in the near future.  
</div>

<div class="file-path">config/routes.rb</div>
{% highlight ruby %}
devise_for :user, controllers: { registrations: "registrations" }
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
Devise controller filters and helper methods are used in <span class="terms">application.html.erb</span> and throughout the templates and controllers. In <span class="terms">application.html.erb</span> in particular, <span class="terms">user_signed_in?</span> is used to display items in the sidebar.  
</div>

<div class="file-path">app/views/layouts/application.html.erb</div>
{% highlight erb %}
<% if user_signed_in? %> 
    <%= link_to "My Wikis", users_show_path, :class => "list-group-item" %> 
    <%= link_to "My Account", account_management_path, :class => "list-group-item" %> 
<% end %>
{% endhighlight %}

<div>&nbsp;</div>

<h4>MODELS</h4>
<div style="margin-bottom:.75cm"></div>
<div class="page-content-text">
<h5>ASSOCIATIONS</h5>
Three models were generated for this app <span class="terms">User</span>, <span class="terms">Wiki</span> and <span class="terms">Collaborator</span>. The Rails generator was used, so the Ruby model classes and database migration files were created. <span class="terms">User</span> was discussed in Authentication, and I’ll refer you to the GitHub repo to review the models’ attributes. As to relationships, <span class="terms">User</span> and <span class="terms">Wiki</span> have <span class="terms">has_many</span> and <span class="terms">belongs_to</span> associations, as do <span class="terms">Wiki</span> and <span class="terms">Collaborator</span>. <span class="terms">Wiki</span> also has a destroy dependency with <span class="terms">Collaborator</span>. As a reminder (from the Features section), collaborators are users who have been given permission by the <span class="terms">Wiki</span> owner, <span class="terms">User</span>, to edit a private <span class="terms">Wiki</span>. 
</div>

<div class="page-content-text">
The <span class="terms">belongs_to</span> relationship between <span class="terms">Collaborator</span> and <span class="terms">Wiki</span> is relied on just once - the <span class="terms">wiki</span> method for <span class="terms">Collaborator</span> is used in the <span class="terms">_show.html.erb</span> partial in <span class="terms">views/collaborators</span>. The partial is rendered on the show view for users. The users show view first lists links to wikis the signed in user has created, and below that, there are links to wikis on which the user is a collaborator. 
</div>

<div class="file-path">app/views/collaborators/_show.html.erb</div>
{% highlight erb %}
<% collaborators.where(emailid: current_user.email).each do |collaborator| %>
    <%= link_to markdown(collaborator.wiki.title), wiki_path(collaborator.wiki.id) %>
<% end %>
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
Several options were considered for creating collaborators on wikis. One option was a Has Many Through (HMT) relationship with <span class="terms">User</span>. I decided not to create a HMT relationship with <span class="terms">User</span> for several reasons. Foremost, I wanted to easily add non-users as collaborators – once the non-user collaborator finally sets up a <span class="terms">User</span> account, the <span class="terms">Collaborator</span> email address would match the <span class="terms">User</span> account email address, and that <span class="terms">User</span> would then already have access to edit the private <span class="terms">Wiki</span>. A more efficient implementation of this may have been possible – e.g. one where fewer <span class="terms">ActiveRecord</span> objects are saved to the database (right now, multiple wikis can have collaborators with the same <span class="terms">emailid</span> key) – but the current means worked easily for what was needed. 
</div>

<div class="page-content-text">
<h5>VALIDATION</h5>
As previously alluded to, <span class="terms">Collaborator</span> objects, unlike <span class="terms">User</span> are not unique by a primary key. Instead, <span class="terms">Collaborator</span> has a unique relationship based on its foreign key, <span class="terms">wiki_id</span>. The <span class="terms">Collaborator</span> model’s validations, ensure that a <span class="terms">Wiki</span> cannot have more than one <span class="terms">Collaborator</span> with the same email address.  
</div>

<div class="file-path">app/models/collaborator.rb</div>
{% highlight ruby %}
validates :emailid, uniqueness: { scope: :wiki_id, :message => "The user you entered is already a collaborator on this wiki." } 
validates_format_of :emailid, { :with => /\A([^@\s]+)@((?:[-a-z0-9]+\.)+[a-z]{2,})\Z/i, :on => :create, :message => "This is not a valid email address." } 
{% endhighlight %}

<div>&nbsp;</div>

<h4>WIKI FEATURES</h4>
<div style="margin-bottom:.75cm"></div>
<div class="page-content-text">
<h5>IMAGES</h5>
<span class="terms">Paperclip</span> was used for file attachment to wikis. The <span class="terms">Paperclip</span> helper was used to add the image database fields to the existing <span class="terms">Wiki</span> model. The <span class="terms">has_attached_file</span> method and a security validation are added to the <span class="terms">Wiki</span> model class. The <span class="terms">styles</span> hash just has two image sizes specified.   
</div>

<div class="file-path">app/models/wiki.rb</div>
{% highlight ruby %}
has_attached_file :image, styles: { medium: "300x300>", thumb: "150x150#" } #, default_url: "/images/:style/missing.png"
validates_attachment_content_type :image, content_type: /\Aimage\/.*\z/
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
The image is attached (new or updated) and removed on the wiki edit view. A couple removal methods were tried, and the one that was kept allows the user to select removal in conjunction with updating the other wiki attributes. This implementation uses a checkbox in the wiki update form. <span class="terms">remove_image</span> is a non-persistent field, and is used to flag removal of the attachment. 
</div>

<div class="file-path">app/views/wikis/edit.html.erb</div>
{% highlight erb %}
<div class="form-group">  
    <% if @wiki.image.exists? %>
        <br>
        <%= f.check_box :remove_image %>
        <label for="remove_image", style="color: red;">Remove Image</label>
    <% end %>
</div>
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
<span class="terms">attr_accessor</span> is used in the <span class="terms">Wiki</span> model class to make this instance variable editable and readable. Then a method reference callback is used to update the wiki’s <span class="terms">image</span> attribute based on the value (checkbox checked or not checked) of <span class="terms">remove_image</span>. <span class="terms">!image_updated_at_changed?</span> is used to determine if the user is trying to upload a new image while also checking <span class="terms">Remove Image</span>. In that case, <span class="terms">image</span> is not updated to <span class="terms">nil</span>.
</div>

<div class="file-path">app/models/wiki.rb</div>
{% highlight ruby %}
attr_accessor :remove_image
before_save :delete_image 
...
private

def delete_image
    if self.remove_image =="1" && !image_updated_at_changed?
        self.image = nil
    end
end
{% endhighlight %}

<div style="margin-bottom:.75cm"></div>

<div class="page-content-text">
<h5>MARKDOWN</h5>
<span class="terms">Redcarpet</span> was used for Markdown processing on <span class="terms">Wiki</span> content. A <span class="terms">markdown</span> helper method is defined in <span class="terms">application_helper.rb</span>. Two hashes are specified containing Markdown <span class="terms">options</span> and <span class="terms">extensions</span>. A <span class="terms">Redcarpet::Markdown</span> object is instantiated with these settings. An HTML renderer is also initialized. Finally, the markdown text passed into the method is rendered. The <span class="terms">markdown</span> method is called in three views, including <span class="terms">app/views/wikis/show.html.erb</span>.
</div>

<h4>ROLES</h4>
<div style="margin-bottom:.75cm"></div>
<div class="page-content-text">
<h5>UPGRADING AN ACCOUNT</h5>
One of Wikit’s features includes a user account being upgraded from the Standard (default) to a Premium account. An upgraded account allows the user to create private wikis. Account status is assigned in the <span class="terms">role</span> attribute of <span class="terms">User</span>. <span class="terms">role</span> is set to ‘standard’ upon object instantiation, using the <span class="terms">after_initialize</span> callback. 
</div>

<div class="file-path">app/models/user.rb</div>
{% highlight ruby %}
after_initialize :init

def init
    self.role  ||= 'standard' 
end
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
To upgrade an account, and change <span class="terms">role</span> from ‘standard’ to ‘premium’, a user makes a payment via <span class="terms">Stripe</span>. The user can also downgrade a Premium account back to Standard. Integration was done using the <span class="terms">Stripe</span> gem. Per Stripe’s prescribed pattern, after configuration with the initialization file, I generated a <span class="terms">ChargesController</span> with <span class="terms">new</span> and <span class="terms">create</span> actions. <span class="terms">customer</span> and <span class="terms">charge</span> objects in the <span class="terms">ChargesController</span>.  The <span class="terms">new</span> and <span class="terms">create</span> actions are standard for <span class="terms">Stripe</span>. A <span class="terms">Customer</span> is created as opposed to a <span class="terms">Charge</span>, so the card is available later for subscription charging. 
</div>

<div class="page-content-text">
Error handling with <span class="terms">flash</span> alerts was included in the <span class="terms">new</span> and <span class="terms">destroy</span> methods. Additionally, a <span class="terms">User</span> class method, <span class="terms">update_role</span>, is called in <span class="terms">create</span> and <span class="terms">destroy</span> to update the <span class="terms">User</span> <span class="terms">role</span> attribute and utilize <span class="terms">customer.id</span>. <span class="terms">customer.id</span> is stored in the <span class="terms">User</span> <span class="terms">cid</span> attribute in the <span class="terms">create</span> method, and <span class="terms">current_user.cid</span> is used in <span class="terms">destroy</span> to retrieve the <span class="terms">customer</span> object to be deleted. This method also updates the <span class="terms">User</span> <span class="terms">role</span> attribute, which is used in scopes and authorization. 
</div>

<div class="file-path">app/controllers/charges_controller.rb</div>
{% highlight ruby %}
def destroy
    if current_user.role == 'standard'
        flash[:alert] = "You already have a Standard account."
        redirect_to account_management_path 
    else 
        cu = Stripe::Customer.retrieve(current_user.cid)
        cu.delete
        current_user.update_role('standard', nil)
        flash[:notice] = "#{current_user.email}, your Premium account has been downgraded back to a Standard account."
        redirect_to account_management_path 
    end 
end 
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
Finally, resource routing is used for the charges controller with the <span class="terms">only</span> option to specify creating only the <span class="terms">new</span> and <span class="terms">create</span> routes. I then use the <span class="terms">as</span> option to declare two custom routes for charges. 
</div>

<div class="file-path">config/routes.rb</div>
{% highlight ruby %}
resources :charges, only: [:new, :create]

as :charge do  
    get 'account_management' => 'charges#account'
    delete 'downgrade' => 'charges#destroy', as: :destroy_charge
end 
{% endhighlight %}

<div style="margin-bottom:.75cm"></div>

<h5>SCOPE AND FILTERS</h5>
<div class="page-content-text">
With three user roles (Standard, Premium, and Admin) and access for non-signed in visitors, <span class="terms">Pundit</span> was used to restrict wiki access based on <span class="terms">User</span> roles. The Admin role was not discussed previously, as it is not available via the app’s user functions (sign up, or upgrade). <span class="terms">scope</span> is used to restrict which wikis appear on the index page. An inner <span class="terms">scope</span> class is added to <span class="terms">wiki_policy.rb</span> to do this. The <span class="terms">policy_scope</span> method is then used in the <span class="terms">index</span> action in <span class="terms">WikisController</span> to return the array to be iterated over. 
</div>

<div class="page-content-text">
<span class="terms">policy_scope</span> was not used in views. The retrieval of appropriate objects there was done via the <span class="terms">has_many</span> or <span class="terms">belongs_to</span> associations between models. Also, instead of Pundit’s <span class="terms">authorize</span> method, <span class="terms">before_action</span> filters are used to halt the request cycle. Devise’s <span class="terms">authenticate_user</span> method is used for the <span class="terms">new</span> and <span class="terms">create</span> actions. The <span class="terms">check_permission</span> method is used for all others. This implementation seemed more efficient than using <span class="terms">authorize</span> in <span class="terms">Pundit</span>, but the code could perhaps be refactored to use <span class="terms">authorize</span>. 
</div>

<div class="file-path">app/controllers/wikis_controller.rb</div>
{% highlight ruby %}
before_action :authenticate_user!, only: [:new, :create] 
before_action :check_permission, except: [:index, :new, :create]
...
def check_permission
    @wiki = Wiki.find(params[:id])
    if current_user 
        if not (@wiki.private == false || @wiki.user_id == current_user.id || current_user.role == 'admin' || @wiki.collaborators.where(emailid: current_user.email).length == 1)
            redirect_to root_url, :flash => { :alert => "You do not have access to this wiki" }
        end
    else 
        if not (@wiki.private == false)
            redirect_to root_url, :flash => { :alert => "You do not have access to this wiki" }
        end 
    end 
end
{% endhighlight %}


