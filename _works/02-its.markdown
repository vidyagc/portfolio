---
layout: work
title: In The Streets
permalink: in-the-streets
id: 4
img: ITS-400.png
img2: ITS-mon.png
alt: In the Streets
alt2: In the Streets news page desktop view
project-date: July - October 2021
project-type: Freelance web services (pro bono) - design and development
project-name: In the Streets
client: In the Streets
category: Web Development
description: new website launch for In the Streets
---
<div class="center-q" style="font-family: 'Montserrat',sans-serif; margin-bottom:100px;">
  <div class="quote1" style="background-color:#f8f8f8">
    <div class="txt">Vidya was responsive and dedicated to developing a site that worked well for us as a relatively new nonprofit and could change with us as we grew. She was also willing to train staff, so that we could make changes as needed. I recommend Vidya to any nonprofit without hesitation.</div>
    <div class="from">Sangeeta Prasad - Co-Founder, In the Streets</div>
  </div>
</div>


<h4>Client</h4>
<div class="page-content-text">
<a href="https://www.inthestreets.org/" target="_blank">In the Streets</a> is a Washington D.C. based 501(c)(3) social services nonprofit. It assists communities affected by generational trauma - working to heal that trauma via physical and mental health resources that prepare community members to support their own neighborhoods. It's "building meaningful livelihoods" through mentoring, restorative yoga, and participatory action groups.
</div>

<h4>Services Provided</h4>
<div class="page-content-text">
I became Web Administrator for In the Streets (<a href="https://www.inthestreets.org/" target="_blank">inthestreets.org/</a>) in June, 2021. I provided content strategy, web design, and web development services to launch a new site. In the summer of 2021, In the Streets was just getting off the ground and preparing for its first fundraising push in the fall (grants applications and private donations). This push was timed with a Washington Post Local Perspectives article on the organization. They wanted to have the new site ready to show their work and call for donations by the time the article came out. This proved to be the right approach as traffic to the site, and consequently donations, saw a huge spike after the Post article was published.  
</div>   

<h4>Services Outline</h4>
<div class="page-content-text">
Below is an outline of the main elements of creating the new site, followed by a more in-depth discussion of specific development and design topics.
</div>

<div class="page-content-text">
<h5>Content Strategy</h5>
<ul>
<li>Generated a sitemap (a list of all the pages on the site and how they relate to each other)</li>
<li>Defined site goals: what are the business objectives we want to achieve with the site?</li>
<li>Identified target audiences, based on audience values and interests</li>
<li>Created content for SEO settings</li>
</ul>   
</div>

<div class="page-content-text">
<h5>Design</h5>
<ul>
<li>Created a color palette. The org did not have a pre-existing logo or branding, so we were free to explore any option with the site's look. The only request of the Streets team was that it be "colorful"</li>
<li>Designed all pages</li>
<li>Incorporated CTA (call to action) prompts throughout the site, in areas targeted for various goals (e.g. donation and becoming a service provider)</li>
<li>Enhanced and corrected images in Photoshop. Pre-launch, In the Streets did not have many photo assets. The handful that were available need to be color-corrected and/or sharpened prior to use on the site. Since launch, we have replaced all the photos used on the site with great new images of community activities.</li>
<li>Created icons (for budget considerations, used free vector image packs and edited/customized those to create icons)</li>
<li>Designed mobile and tablet size layouts for all pages</li>
<li>Designed mobile menu</li>
</ul>
</div>

<div class="page-content-text">
<h5>Development</h5>
<ul>
<li>Technologies used: Squarespace, HTML/CSS, Photoshop</li>
<li>Built new pages and sections</li>
<li>Implemented custom styles (CSS) for all site components</li>
<li>Responsive testing of entire site (including testing pages in non-device specific screen sizes)</li>
<li>Cross browser testing of entire site</li>
<li>Set default Open Graph image (for social sharing image previews)</li>
<li>Set individual Page SEO settings</li>
</ul>

<strong><em>Why Squarespace?</em></strong> Prior to my engagement, In the Streets had already set up an initial attempt at a site on Squarespace. I thought Squarespace would continue to be a good fit for several reasons - part of the consideration being that they might have to manage the site themselves in the future. These reasons were managed web hosting and security, lower threshold for page and form building by novices, built-in website analytics, and user support. The primary drawback of Squarespace (vs say WordPress) is that it is less customizable. I found this to be an issue particularly with regard to responsive design, but was ultimately able to implement the desired behavior.
</div>

<h4>Development: Customization in Square</h4>
<div class="page-content-text">
When not using the <a href="https://developers.squarespace.com/quick-start" target="_blank">Developer Platform</a> to modify templates, customization in Squarespace is more limited compared to some other web builders. There are, however, options to go beyond just the built-in Site Styles feature (which requires no coding). These options include, but are not limited to, the code block, custom CSS, and third-party plugins.   Every element of the In the Streets site was customized, as the built-in blocks and Site Styles were not sufficient to implement the desired design/user experience. Below are just a few examples of these customizations.   
</div>

<h5>Code Block to Create News and Banner Elements</h5>
<div class="page-content-text">
When designing <a href="https://www.inthestreets.org/news-updates" target="_blank">News & Updates</a>, I wanted a way to highlight press features. Squarespace didn't offer anything that seemed adequate for this. Ultimately, I decided on a quote callout, linking to the news piece, and looked for design examples to base this on. I found an example on CodePen, and modified it to match the look of the rest of the site. To implement it, I generated custom code and added it with <a href="https://support.squarespace.com/hc/en-us/articles/205815928-Adding-custom-code-to-your" target="_blank">Squarespace's Code block (basic) and CSS Editor</a>. The code for the press highlight can be viewed on <a href="https://codepen.io/vidyagc/pen/oNdjRqd" target="_blank">my CodePen</a>, so you can experiment with it, as well as viewing it.

The Code block and custom CSS was also used to make the organization name and tagline callout on the homepage banner.  Below is the code for that element.  
</div>

<div style="margin-top:.50cm; margin-bottom:1cm">
<img src="{{site.baseurl}}/img/portfolio/banner-title.png" style="max-width:650px; height: auto; margin: auto; display: block;">
</div>
<div class="file-path">Code block content for banner title callout</div>
<div>
{% highlight html %}
<div style="text-align:center; max-width:650px;" id="banner-text-box">
  <div style="">
    <h2 style="margin-bottom:-30px;  padding-top:18px!important;">In the Streets</h2>
    <h2 class="background" style="font-size:25px;color: transparent;  text-shadow: 0 0 0 rgb(232,185,35);">&#10060;</h2>
    <p class="sqsrte-large" style="white-space:pre-wrap;margin-top:-30px;"><strong>Building meaningful livelihoods and disrupting generational trauma in Columbia Heights, Washington DC </strong></p>
  </div>
</div>
{% endhighlight %}
</div>
<div>&nbsp;</div>
