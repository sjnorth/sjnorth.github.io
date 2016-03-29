---
layout: post
title:  "Exploring AJAX"
post_author: Samantha North
date:   2016-03-25 15:00:47 +0200
categories: tech 
---

## This week I'm learning AJAX. 

To consolidate what I've been studying, here's a brief rundown of my first AJAX request. 

{% highlight ruby %}

var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function() {
  if (xhr.readyState === 4 && xhr.status === 200) {
    document.getElementById('sidebar').innerHTML = xhr.responseText;
  }
};
xhr.open('GET', 'sidebar.html');
xhr.send();

{% endhighlight %}

First, I created a variable named xhr, which I assigned the value of new XMLHttpRequest.Creating an XMLHTTP object like this is the first step in the AJAX request process. Next I added a callback function and set that to run when the correct ready state had been reached (state 4).

The function contained a conditional statement to check that the state was at the correct point to run (i.e. stage 4). If so, then the callback function runs. It first opens the AJAX request and then sends it to the server. 

When the request comes back, the function uses the getElementById and innerHTML directions to display the results in the DOM, within the specified div element as identified by the id of 'sidebar'.

This could be used for website features such as displaying a weather report in the sidebar, or for showing a timeline of your latest tweets. 

As the course progressed, we learned how to write more AJAX requests - both using vanilla JavaScript and with jQuery (it's amazing how much less code the latter way uses!), how to process JSON with jQuery, and how to use AJAX with third-party APIs such as those from Flickr. 

I made a simple app that pulls in photos from three different categories on Flickr. The app uses the Flickr API to access the public feed of latest photos, and uses keywords to bring in the right ones. 

To keep it simple, my page included three city names: Beijing, Istanbul and London, with buttons for each one. When the user clicks the button for each city, the page will display the latest Flickr photos tagged with that city's name. 

For now, the project is only on GitHub, but I'll put it on Heroku very soon. I'll add the link here when I do. I'm quite proud of this project because I managed to build it with very little help from the Treehouse course. Building it has helped me gain a much better understanding of key AJAX concepts. 

## UPDATE. I just tried pushing this app to Heroku, but encountered an error message that said "Push rejected, no Cedar-supported app detected". 

I did some Googling to figure out this error. My first instinct suggested that it was something to do with the back-end, or lack of it, as the last time I used Heroku successfully was to deploy a Rails app. 

Most mentions of Heroku online were about PHP, node.js, Flask and so on. The only way my app differed was in its lack of back-end. Some further Googling confirmed my suspicions. Heroku needs the full-stack [in order to work, as this useful blog post explains.](http://erictsang.co/deploying-your-angular-app-to-heroku/) 
