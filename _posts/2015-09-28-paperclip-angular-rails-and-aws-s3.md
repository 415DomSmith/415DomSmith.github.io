---
layout: post
title:  "Pushing files to Amazon s3 using Angular and Rails"
date:   2015-10-3 17:36:05
author: Dominic V. Smith
categories: gSchool Blog technical Rails Angular
image: true
---


I recently completed a [project](http://www.myhwapp.com) that required file storage for users, allowing them to save and upload pdf files to be viewed by other users.

To achieve this in development, the project was using the Rails gem [Paperclip](https://github.com/thoughtbot/paperclip) to save files directly in to our postgreSQL database. Paperclip is a pretty easy to use file attachment library for ActiveRecord, that for the most part, treats attachments like any other data attribute. 

From a purely Rails perspective, Paperclip is pretty plug and play. I’d reccomend [this blog post](https://codeabout.wordpress.com/2011/03/08/gem-paperclip-uploading-files-and-pictures-into-your-rails-application/) for a walk through to implement a straight Rails and Paperclip application, and the Paperclip [docs](https://github.com/thoughtbot/paperclip#installation) for additional help. A quick note on the blog link above:  If you are using a more current version of Rails, there are a few changes you will need to make. See [this](https://medium.com/@parkerlewis_27970/paperclip-with-rails-4-3303e60fac94) blog post if working with Rails 4.0 or greater.

What I want to talk about for the rest of this post is how to implement the Rails gem Paperclip with Angular and Amazon’s s3 cloud storage. We’ll create a basic photo viewing application using Angular on the front-end, a Rails API on the back-end, and Amazon s3 for file storage.

We'll make a quick Rails app and scaffold it.

{% highlight ruby %}
$ rails new photo_viewer -TBd postgresql
$ cd photo_viewer/
$ rails g scaffold image name:string url:string
{% endhighlight %}

In order to attach photos with Paperclip, you need to have [Imagemagick](http://www.imagemagick.org/script/index.php) installed. If you do not have it installed already, you can use homebrew to install it pretty easily.

{% highlight ruby %}
$ brew install imagemagick
{% endhighlight %}

If you are dealing with pdf uploads or running the test suite, you'll also need to install [GhostScript](http://www.ghostscript.com/). 

{% highlight ruby %}
$ brew install gs
{% endhighlight %}

In our gem file, we'll add the following gems:

{% highlight ruby %}
gem 'aws-sdk', '~> 1.6'
gem 'paperclip', '~> 4.3'
{% endhighlight %}

and then bundle, and create migrations. A special note on using aws-sdk, the most current version of this gem is not supported by Paperclip yet. The folks at Thoughtbot, the gems creators have acknowledged the conflicts created by using Paperclip and the most recent AWS gem, but do not have a fix for it yet. Until then, using version 1.6 of the AWS SDK gem has not caused any problems, in my experience. 

Paperclip has a migration generator, where all we need to do is specify the model and the name of our attachment. We'll call our attachments photo.

{% highlight ruby %}
$ $ bundle
$ $ rails generate paperclip Image photo
{% endhighlight %}

Next we need to create our DB, and implement our migrations.

{% highlight ruby %}
$ rake db:create
$ rake db:migrate
{% endhighlight %}

When we look at our Schema, we see that the Paperclip migration added some important columns in our images table. 


{% highlight ruby %}
create_table "images", force: :cascade do |t|
    t.string   "name"
    t.string   "url"
    t.datetime "created_at",         null: false
    t.datetime "updated_at",         null: false
    t.string   "photo_file_name"
    t.string   "photo_content_type"
    t.integer  "photo_file_size"
    t.datetime "photo_updated_at"
  end
{% endhighlight %}


The "photo_file_name", "photo_content_type", "photo_file_size", and "photo_updated_at" columns are all generated and filled by Paperclip.

Next let's set up Angular for our front-end.

You can use a CDN and link the files in the application.html.erb, or you can download Angular files and place them directly in to the rails pipline. For this example, I'll do just that. 

So go ahead and navigate to the most recent version of [Angular](https://code.angularjs.org/), download it, and place it in to your assets < javascripts folder. I find it good practice to make a new folder for angular files in this directory, and I usually put the minified Angular file and any other modules in to another folder in this directory that I usually call lib. But in the end, they all get compiled and minified through the rails pipeline, so it doesn't really matter where you put them.

Additionally, there is a [rails gem](https://github.com/hiravgandhi/angularjs-rails) for Angular. However, I still like placing the files directly in to my assets folder. Call me crazy.

The next step for installing Angular is editing our  ```app/assets/javascripts/application.js``` file to require Angular, and specifically, to require it before other Angular modules.

application.js should look like this:

{% highlight ruby %}
//= require jquery
//= require jquery_ujs
//= require angular/lib/angular.min
//= require_tree ./angular/lib
//= require_tree .
{% endhighlight %}

Also note that we removed ```//= require turbolinks``` from application.js because turbolinks can cause problems with Angular. It's a good idea to remove the turbolinks gem from our gemfile, and also remove turbolinks dependency from our ```app/views/layouts/application.html.erb``` file. In the head of our application.html.erb file, change the ```javascript_include_tag``` to not include turbolinks. 

{% highlight ruby %}
<%= javascript_include_tag 'application', 'data-turbolinks-track' => false %>
{% endhighlight %}

While we're in application.html.erb, let's also remove the yield tag from the body of our file, and add in some Angular directive tags.

{% highlight html %}
<!DOCTYPE html>
<html>
<head>
  <title>ContactsApp</title>
  <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track' => true %>
  <%= javascript_include_tag 'application', 'data-turbolinks-track' => false %>
  <%= csrf_meta_tags %>
</head>
<body ng-app>
   
</body>
</html>
{% endhighlight %}

And don't forget to bundle after removing ```gem 'turbolinks'``` .





Next we'll modify our image.rb model to accept Paperclip attachments, and we'll also set the foundation for saving our files to s3.

In image.rb we want to tell the model that it has attached files, and also tell it what type of attachments it should accept.

{% highlight ruby %}
class Image < ActiveRecord::Base
	has_attached_file :photo


	validates_attachment_content_type :photo, :content_type => /\Aimage\/.*\Z/

end
{% endhighlight %}

TO BE CONTINUED






<div class="post-img">
	<img class="img-responsive img-post" src=""/>
</div>



