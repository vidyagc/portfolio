---
layout: work
title: Git'er Done!
permalink: giterdone
id: 2
img: giterdone-400.png
img2: giterdone-mon.png
alt: Giterdone logo, links to Giterdone application writeup
alt2: Giterdone app view
project-date: August 2017
project-type: Academic assignment
project-name: Git'er Done!
client: Personal Project
category: Web Development
description: a to-do list management application that automatically deletes expired tasks
---

<h4>DESCRIPTION</h4>
<div class="page-content-text">
A web application that uses Firebase API and AngularJS to create tasks and automatically expire them. The project write up below does not detail every aspect of implementation. Rather, it summarizes or skips common practice code, but highlights the relatively more individualistic components. It also assumes basic familiarity with the technology on the part of the reader. Environment setup is outlined in README in the GitHub repository, and is not covered here.
</div>

<h5>CODER COMMENT</h5>
<div class="page-content-text">
Working with AngularFire was great experience, but the design of the task display and making choices about ease of viewing and editing were among the most stimulating parts of this project. Also, I liked using theme throughout color scheme, images, and font to achieve a cohesive aesthetic.
</div>

<h4>LINKS</h4>
<div class="page-content-text">
<a href="https://vn-giterdone.herokuapp.com/" target="_blank">Live App</a> - the live app is no longer available. It was an academic assignment from 2017, and no longer being maintained for security updates. Please refer, however, to this case study for an understanding of the work performed.<br>
<a href="https://github.com/vidyagc/giterdone" target="_blank">GitHub Repo</a>
</div>

<h4>TESTING</h4>
<div style="margin-bottom:.75cm"></div>
<div class="page-content-text">
<h5>CONFIGURATION</h5>
<ul><li>Tasks expire after 90 seconds so testers can see the task expiration functionality within a reasonable testing time frame.</li>
<li>The Firebase database does not require users to be logged in to the application, and is set to allow anyone to read/write.</li></ul>
<div style="margin-bottom:.75cm"></div>
<h5>FEATURES</h5>
<ul>
<li>Create tasks with title and priority</li>
<li>Edit tasks (including multiple at once)</li>
<li>Task expiration after 90 seconds - it is removed from home view to history view</li>
<li>Delete task - it is removed from home view to history view</li>
<li>Purge tasks from history individually</li>
<li>Purge entire task history</li>
</ul>
</div>

<h4>VIEWS</h4>
<div class="page-content-text">
The two views in the application consist of a default view that displays active tasks and a separate view that presents expired and completed tasks. <span class="terms">index.html</span> acts as a global file and contains a <span class="terms">uiview</span> <span class="terms">viewport</span>. The templates are home.html and history.html.
The <span class="terms">UI-Router</span> module is used with <span class="terms">$locationProvider</span> and <span class="terms">$stateProvider</span> to disable <span class="terms">Hashbang</span> mode for application paths and configure states for <span class="terms">home</span> and <span class="terms">history</span>. The state changes are triggered using <span class="terms">ui-sref</span> on each of the views.
</div>

<h4>DATABASE</h4>
<div class="page-content-text">
Firebase was used to save and sync data on the backend. Structurally, the database has a ‘tasks’ key, and <span class="terms">task</span> objects have four properties – date, status, title, and pThread. Task-related API queries are handled in a <span class="terms">Task</span> factory in Angular. Within the <span class="terms">Task</span> factory, the <span class="terms">orderByChild()</span> method is called three times on a <span class="terms">Reference</span> for the ‘tasks’ location. These <span class="terms">Query</span> objects are ordered by the ‘status’ key, and <span class="terms">equalTo()</span> is used to match all three possible values for status – ‘incomplete’, ‘complete’, and ‘expired’. The <span class="terms">$firebaseArray</span> service is used to return this data as an array. How this data is used will be explained in further detail in the Angular section.
</div>

<div class="file-path">app/scripts/services/Task.js</div>
{% highlight ruby %}
var ref = firebase.database().ref().child("tasks");

Task.tasksIncomplete = $firebaseArray(ref.orderByChild("status").equalTo("incomplete"));
Task.tasksComplete = $firebaseArray(ref.orderByChild("status").equalTo("complete"));
Task.tasksExpired = $firebaseArray(ref.orderByChild("status").equalTo("expired"));
{% endhighlight %}

<div>&nbsp;</div>

<h4>ANGULAR</h4>
<div style="margin-bottom:.75cm"></div>
<h5>Basic Architecture</h5>
<div class="page-content-text">
To briefly summarize the Angular application architecture, the root Angular module is named ‘giterdone’ and is bootstrapped in the <span class="terms">&lt;html&gt;</span> element of <span class="terms">index.html</span>. Two controllers, <span class="terms">HomeCtrl</span> and <span class="terms">HistoryCtrl</span> are used, and each state has one designated for it in <span class="terms">$stateProvider</span>. Finally, a <span class="terms">Task</span> factory handles Firebase queries and is injected into both controllers.
</div>

<h5>Directives and Forms</h5>
<div class="page-content-text">
Tasks are displayed in the home and history views using the <span class="terms">ng-repeat</span> directive on the aforementioned three sets of ‘status’ ordered array data. The history view displays ‘expired’ and ‘completed’ tasks and home shows ‘incomplete’ objects. In <span class="terms">home</span>, <span class="terms">&lt;li&gt;</span> is the repeated HTML element. <span class="terms">&lt;li&gt;</span> contains an <span class="terms">ng-class</span> directive to add background color to the list item based on its priority. The collection is also ordered by priority.
</div>

<div class="file-path">app/templates/home.html</div>
{% highlight html %}
<li class="list-group-item list-style-do" ng-class="{'h-fade': task.pThread.split(',')[1] == '1', 'm-fade': task.pThread.split(',')[1] == '2', 'l-fade': task.pThread.split(',')[1] == '3'}">
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
In the <span class="terms">home</span> template, this list element contains two sets of items. Each set of items is shown or hidden using <span class="terms">ng-show</span> and <span class="terms">ng-hide</span>. The items that are shown by default are the task title, a button to update tasks as completed, and an edit button to update the task. The edit button has an <span class="terms">ng-click</span> directive that shows the textbox and radio buttons to update the task <span class="terms">title</span> and <span class="terms">priority</span>, and the submit button which calls the <span class="terms">updateTask</span> method. <span class="terms">ng-click</span> in the edit button also hides the default display items, including itself. The button to submit the task update form elements, also has an <span class="terms">ng-click</span> that correspondingly, hides the form elements, and shows the default display items.
</div>

<div class="file-path">app/templates/home.html</div>
{% highlight html %}
<button ng-show="newP" class="submit-with-icon" style="float: right !important;" ng-click="home.updateTask(task, newTitle, newPriority); newP=false; editP=false; oldT=false; newT=false;"><span class="glyphicon glyphicon-ok" style="vertical-align: middle;"></span></button>

<button ng-hide="editP" type="button" class="submit-with-icon" style="float: right !important;"><span class="glyphicon glyphicon-pencil"  ng-click="newP=true; subP=true; editP=true; oldT=true; newT=true"></span></button>
{% endhighlight %}

<div>&nbsp;</div>

<h4>TASK MANAGEMENT WITH FIREBASE</h4>
<div style="margin-bottom:.75cm"></div>
<h5>Completion and Expiration</h5>
<div class="page-content-text">
The <span class="terms">status</span> of task objects is updated via two methods: first, the user marking the task as complete; second, a <span class="terms">setInterval</span> method in Angular’s <span class="terms">Task</span> factory which expires tasks based on their <span class="terms">date</span> property. In the <span class="terms">home</span> template, ‘incomplete’ tasks are displayed with a button that has an <span class="terms">ng-click</span> directive. Clicking it executes the <span class="terms">completeTask</span> function in <span class="terms">HomeCtrl</span> and passes the respective task object as an argument. Within this method, the <span class="terms">status</span> property of the object is updated to ‘complete’.
</div>

<div class="page-content-text">
In the <span class="terms">Task</span> factory, JavaScript's <span class="terms">setInterval()</span> method is used to update the object’s <span class="terms">status</span> to ‘expired’ based on its <span class="terms">date</span> property. Within the method, <span class="terms">orderByChild()</span> generates a query object ordered by the ‘status’ key, and <span class="terms">equalTo()</span> limits the query to children with a status of 'incomplete'. <span class="terms">on()</span> is called on the query object and the tasks are looped through with <span class="terms">forEach()</span>. A conditional statement then checks if the <span class="terms">date</span> of the snapshot is 90 seconds behind the current time. Then <span class="terms">update()</span> is used on the <span class="terms">Reference</span> for that location to change <span class="terms">status</span> to ‘expired’.
</div>

<div class="file-path">app/scripts/services/Task.js</div>
{% highlight ruby %}
setInterval(function(){
    var query = ref.orderByChild("status").equalTo('incomplete');
    query.on("value", function(snapshot) {
        snapshot.forEach(function(snapshot) {
            if (snapshot.val().date < (Math.round(Date.now() / 1000) - 89)) {
                snapshot.ref.update({status: 'expired'})
             }
        });
    });
}, 1000)
{% endhighlight %}

<div>&nbsp;</div>

<div class="page-content-text">
Taking a step back, ‘date’ is assigned when a task is added. The <span class="terms">addTask</span> method is located in <span class="terms">HomeCtrl</span>. Within it, <span class="terms">Date.now()</span> is called and the result is divided by 1000 to get a value in seconds vs milliseconds. Then <span class="terms">Math.round()</span> is used to get the result in whole seconds.
</div>

<div class="file-path">app/scripts/controllers/HomeCtrl.js</div>
{% highlight ruby %}
...
this.newTask.date = Math.round(Date.now() / 1000);
...
{% endhighlight %}

<div>&nbsp;</div>
<div class="page-content-text">
In the history view, users can delete tasks individually or clear the entire history. <span class="terms">off()</span> is used to detach the callbacks on the references.
</div>

<div class="file-path">app/scripts/controllers/HistoryCtrl.js</div>
{% highlight ruby %}
this.deleteAll = function() {
    ref.orderByChild("status").equalTo("complete").on("child_added", removeSnap);
    ref.orderByChild("status").equalTo("expired").on("child_added", removeSnap);
    ref.off("child_added", removeSnap);
}
{% endhighlight %}
