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
project-type: Freelance web services - design and development
project-name: In the Streets
client: In the Streets
category: Web Development
description: new website launch for In the Streets
---
<h4>Client</h4>
<div class="page-content-text">
<a href="https://www.inthestreets.org/" target="_blank">In the Streets</a> is a Washington D.C. based 501(c)(3) social services nonprofit. It assists communities affected by generational trauma - working to heal that trauma via physical and mental health resources that prepare community members to support their own neighborhoods. It's "building "meaningful livelihoods" through mentoring, restorative yoga, and participatory action groups.
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
<li>Created icons (for budget considerations, used free vector image packs and customized those for color, etc. in PS)</li>
<li>Designed mobile and tablet size layouts for all pages</li>
<li>Designed mobile menu</li>
</ul>
</div>

<div class="page-content-text">
<h5>Development</h5>
Prior to my engagement, In the Streets had already set up an initial attempt at a site on Squarespace. I thought Squarespace would continue to be a good fit for several reasons - part of the consideration being that they might have to manage the site themselves in the future. These reasons were managed web hosting and security, lower threshold for page and form building by novices, built-in website analytics, and user support. The primary drawback of Squarespace (vs say WordPress) is that it is less customizable. I found this to be an issue particularly with regard to responsive design, but was ultimately able to implement the desired behavior.

<div style="margin-bottom:.25cm"></div>
<ul>
<li>Technologies used: Squarespace, HTML/CSS, Photoshop</li>
<li>Built new pages and sections</li>
<li>Implemented custom styles (CSS) for all site components</li>
<li>Responsive testing of entire site (including testing pages in non-device specific screen sizes)</li>
<li>Cross browser testing of entire site</li>
<li>Set default Open Graph image (for social sharing image previews)</li>
<li>Set individual Page SEO settings</li>
</ul>
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

<div style="margin-top:.50cm; margin-bottom:.75cm; justify-content: center;">
<img src="{{site.baseurl}}/img/portfolio/banner-title.png" style="max-width:650px; height: auto;">
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

<div class="file-path">CSS for banner title callout</div>
<div style="max-height: 350px; overflow: scroll;">
{% highlight css %}
h2.background {
  position: relative;
  z-index: 1;
  margin-left:auto;
  margin-right:auto;
  max-width:400px;

  &:before {
    background:linear-gradient(to right, #796DC5 50%, #405ebd 50%) bottom;
    height: 6px;
    content:"";
    margin: 0 auto;
    position: absolute;
    top: 40%; left: 0; right: 0; bottom: 0;
    width: 95%;
    z-index: -1;
  }

  span {
    background: #fff;
    padding: 0 15px;
  }
}

#banner-text-box {
  padding-left:15px!important;
  padding-right:15px!important;
  background-color:rgba(0,0,0, .7);
  margin-bottom:-40px!important;
  padding-bottom:15px!important;
}
{% endhighlight %}
</div>
<div style="margin-bottom:.75cm">&nbsp;</div>

<h5>Lightbox Plugin for Bio Popups</h5>
<div class="page-content-text">
For the <a href="https://www.inthestreets.org/our-team" target="_blank">Team page</a>, I wanted a layout with bio teasers and links that open the full personnel profile as a popup. Ideally, I would have had the bio images be clickable, but in using the built-in list feature for the teasers, this was not an option (even with custom coding). Also, a popup/lightbox feature was not available for a text link, so I set up a third-party <a href="https://www.sqspthemes.com/plugins/ultimate-squarespace-lightbox-plugin" target="_blank">Lightbox plugin</a> for that.
</div>

<div class="page-content-text">
For the popup content itself, I used the Image (overlap) block, heavily modified with Site Styles, to create the section with profile image, name, and title. I really liked the use of this element, because its default responsive (smaller screen size) behavior looked good - open a popup and squeeze the window down to see for yourself (the name and title fall under, and slightly overlap, the profile photo). One of the more amusing parts of working on the Team page was getting some of the staff and one board member to provide headshots with matching backgrounds and similar poses: they were nice enough to take new photos when needed <i class="fa fa-smile-o" aria-hidden="true"></i>.  
</div>

<h5>Custom CSS: Resources and Use</h5>  
<div class="page-content-text">
Adding custom CSS in Squarespace involves targeting existing elements (pages, section, selectors, etc.) and overriding/appending their styles. There are many tutorials for this, but the resource I found most useful was <a href="https://insidethesquare.co/" target="_blank">Inside the Square's</a> YouTube <a href="https://www.youtube.com/c/InsideTheSquare" target="_blank">Channel</a>. I still had to use browser Developer Tools, but the Inside the Square Tutorials were a quick reference point for different selectors (e.g. navigation, list cards, etc.).  
</div>

<div class="page-content-text">
As aforementioned, every portion of the site had custom CSS applied. Here are a few examples of areas that required special consideration (in addition to the code blocks cited previously):
<div style="margin-bottom:.25cm"></div>
<ul>
<li><a href="https://www.inthestreets.org/" target="_blank">Homepage</a> <strong>Structure and Theory</strong> (using the Simple List block)</li>
<li><a href="https://www.inthestreets.org/" target="_blank">Homepage</a> <strong>Building Support</strong>, and similarly, <a href="https://www.inthestreets.org/acknowledgements-partners" target="_blank">Acknowledgements</a></li>
<li><a href="https://www.inthestreets.org/provide-services" target="_blank">Provide Services</a> service areas list (using Image and Text blocks)</li>
<li><a href="https://www.inthestreets.org/" target="_blank">Homepage</a> <strong>What We Do half</strong> (using Image and Text blocks )</li>
</ul>
</div>

<div class="file-path">CSS for Structure and Theory chart</div>
<div style="max-height: 350px; overflow: scroll;">
{% highlight css %}
[data-section-id="61714f1a7094ed1b42dfc3a5"] {
  margin-bottom:15px;
  li:nth-child(1) p, li:nth-child(2) p, li:nth-child(3) p {
    font-weight:600;
    font-size:1.15rem;
    color:white;
  }
  li:nth-child(3) {
    background-color: #9e6f59!important;
  }
  li:nth-child(2) {
    background-color: #405ebd!important;
    .sqs-block-button-element--medium {
      background-color:white!important;
      color:black!important;
    }
  }
  li:nth-child(1) {
    background-color: #e8b923!important;
    p {
      color:#000000;
    }
  }

  @media only screen and (min-width:650px) {
    .list-item {
      min-height:37vh;
    }
  }
  .list-item-content__button-container {
      margin-top:40px!important;
    }
  }
{% endhighlight %}
</div>
<div style="margin-bottom:.75cm">&nbsp;</div>

<h4>Design Considerations</h4>
<div style="margin-bottom:.75cm"></div>

<div class="page-content-text">
<h5>CONDENSING THE COMPLEX</h5>
In regards to content layout, one of the more design-intensive sections was the Structure and Theory of Change chart on the <a href="https://www.inthestreets.org/" target="_blank">homepage</a>. When I originally collected content from the client, it included the diagrams on the <a href="https://www.inthestreets.org/theory-of-change" target="_blank">Theory of Change page</a>. These diagrams were submitted in a grant application, and the client wanted them on the site to show their approach to addressing Trauma. As it is key to understanding the work of this new organization, I wanted to include a callout to <a href="https://www.inthestreets.org/theory-of-change" target="_blank">Theory of Change</a> on the homepage.         
</div>

<div class="page-content-text">
It was preferable to have something more engaging than just text, and I decided to use an infographic to summarize their approach. Originally, I made an image of a flow diagram with icons and had a button underneath linking to the Theory page.   
<div style="margin-top:.50cm; margin-bottom:.75cm; justify-content: center;">
<img src="{{site.baseurl}}/img/portfolio/ITS-chart.jpeg" style="max-width:750px; height: auto;">
</div>

<div class="page-content-text">
After showing the site (pre-launch) to an associate who is a professional web designer, however, she had some great suggestions for this section. She, Erika, mocked up the three box layout with the button and icons inside the boxes. Additionally, she said to make it via code vs an image, so that it would be responsive and accessible (readable by assistive technology). Her rough mockup included the other site colors (blue, brown, and yellow) for the boxes. This was a great touch to tie together the overall look of the homepage. I made a couple changes as far as the order of the colors, and updating the icons to "pop" more on the new backgrounds. Then, I created the infographic with custom code. Erika and I had a related (brief) discussion about the need to adapt the diagram images on the <a href="https://www.inthestreets.org/theory-of-change" target="_blank">Theory page</a> to also be more web-friendly, but due to time and budget constraints, I have not yet been able to consider updates for those.    
</div>  

<h5><i class="fa fa-music" aria-hidden="true"></i> "With a Little Help From My Friends" <i class="fa fa-music" aria-hidden="true"></i></h5>
<div class="page-content-text">
I really appreciated Erika's generosity in reviewing the prototype site and offering suggestions. In addition to the Theory infographic, she also mocked up the aforementioned title and tagline callout on the homepage banner. Prior to her design, I just had the title and text left-aligned on a semi-opaque purple background over the banner image. She suggested centering the content, so it would draw the eye down the center of the page. Her mockup also included the double-color line with X (made with all the primary site colors). She said it would help tie all the colors into the banner. This did, in fact, achieve a more cohesive look. And as before, she said to make this via code vs an image. Moral of the story? Don't hesitate to ask for a little advice when you're near an expert.    
</div>  

<h5>Icon Creation and Theme</h5>
<div class="page-content-text">
Part of making content more engaging is having icons to help convey the message. Due to a limited budget, I relied primarily on free vector image packs to create these. I was not able to find images that, in entirety, were what was needed: rather, I cut out and/or combined parts of the vector images to create the icons, and further edited them for color, etc.  

Because the organization's name is In the Streets, icons with a distressed look seemed appropriate. Likewise, I styled certain callouts (e.g. Building Support on the <a href="https://www.inthestreets.org/" target="_blank">homepage</a> and <a href="https://www.inthestreets.org/acknowledgements-partners" target="_blank">Acknowledgements</a>) with grunge/distressed borders.
</div>  

<h4>Additional Updates Needed</h4>
<div class="page-content-text">
As previously stated, the diagrams on <a href="https://www.inthestreets.org/theory-of-change" target="_blank">Theory of Change</a> need to be translated into web-friendly content. Instead of images, infographics should be made with real text (so the content is accessible), and they should be responsive (i.e. adapt to different screen sizes for readability). These updates will be made when time and/or budget become available.
</div>  
