---
layout: post
title:  "Pushing files to Amazon s3 using Angular and Rails"
date:   2015-09-28 17:36:05
author: Dominic V. Smith
categories: gSchool Blog technical Rails Angular
image: true
---


I recently completed a [project](http://www.myhwapp.com) that required file storage for users, allowing them to save and upload pdf files to be viewed by other users.

To achieve this in development, the project was using the Rails gem [Paperclip](https://github.com/thoughtbot/paperclip) to save files directly in to our postgreSQL database. Paperclip is a pretty easy to use file attachment library for ActiveRecord, that for the most part, treats attachments like any other data attribute. 

From a purely Rails perspective, Paperclip is pretty plug and play. I’d reccomend [this blog post](https://codeabout.wordpress.com/2011/03/08/gem-paperclip-uploading-files-and-pictures-into-your-rails-application/) for a walk through to implement a straight Rails and Paperclip application, and the Paperclip [docs](https://github.com/thoughtbot/paperclip#installation) for additional help. A quick note on the blog link above:  If you are using a more current version of Rails, there are a few changes you will need to make. See [this](https://medium.com/@parkerlewis_27970/paperclip-with-rails-4-3303e60fac94) blog post if working with Rails 4.0 or greater.

What I want to talk about for the rest of this post is how to implement the Rails gem Paperclip with Angular and Amazon’s s3 cloud storage. We’ll create a basic photo viewing application using Angular on the front-end, a Rails API on the back-end, and Amazon s3 for file storage.

We'll make a quick Rails app and scaffold it.

{% highlight ruby linenos %}
1 $ rails new photo_viewer -TBd postgresql
2 $ cd photo_viewer/
3 $ rails g scaffold image name:string url:string
{% endhighlight %}

In order to attach photos with Paperclip, you need to have [Imagemagick](http://www.imagemagick.org/script/index.php) installed. If you do not have it installed already, you can use homebrew to install it pretty easily.

{% highlight ruby linenos %}
1 $ brew install imagemagick
{% endhighlight %}

If you are dealing with pdf uploads or running the test suite, you'll also need to install GhostScript. 

{% highlight ruby linenos %}
1 $ brew install gs
{% endhighlight %}

In our gem file, we'll add the following gems:

{% highlight ruby linenos %}
gem 'aws-sdk', '~> 1.6'
gem 'paperclip', '~> 4.3'
{% endhighlight %}

and then bundle, and create migrations. A special note on using aws-sdk, the most current version of this gem is not supported by Paperclip yet. The folks at Thoughtbot, the gems creators have acknowledged the conflicts created by using Paperclip and the most recent AWS gem, but do not have a fix it yet. Until then, using version 1.6 of the AWS SDK gem has not caused any problems, in my experience. 

Paperclip has a migration generator, where all we need to do is specify the model and the name of our attachment. We'll call our attachments photo.

{% highlight ruby linenos %}
1 $ bundle
2 $ rails generate paperclip Image photo
{% endhighlight %}

Next we need to create our DB, and implement our migrations.

{% highlight ruby linenos %}
1 $ rake db:create
2 $ rake db:migrate
{% endhighlight %}

When we look at our Schema, we see that the Paperclip migration added some important columns in our images table. 


{% highlight ruby linenos %}
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





Next we'll modify our image.rb model to accept Paperclip attachments, and we'll also set the foundation for saving our files to s3.

In image.rb we want to tell the model that it has attached files, and also tell it what type of attachments it should accept.

{% highlight ruby linenos %}
class Image < ActiveRecord::Base
	has_attached_file :photo


	validates_attachment_content_type :photo, :content_type => /\Aimage\/.*\Z/

end
{% endhighlight %}








<div class="post-img">
	<img class="img-responsive img-post" src=""/>
</div>



