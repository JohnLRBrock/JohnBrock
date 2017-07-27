---
blog: multifaceted rubyist
layout: post
title: Using Semaphores and Active Jobs to Throttle API requests in Ruby on Rails
---

I love discovering new books. Recommendations from friends, suggestions from sites, or endorsements from interesting people. That's why using [Goodreads](goodreads.com) was a natural fit for me. It makes my lust for reading easier to catalog. 

But I have a problem. Goodreads has made it so easy to find and catalog books that I have over 600 books on my [to-read shelf](https://www.goodreads.com/review/list/12433997?shelf=to-read).
The list is totally unmanageable. 

A couple of years ago I created a [python script](https://github.com/Khanthulhu/Goodreads-Checkout) to search my local library for random books on my to-read shelf until it reached a page quota. I decided that this functionality would be more useful on a website.

This guide will go through how to construct a website using Ruby on Rails and Resque to create an app that interfaces with the Goodreads API to fetch random books until you've reached a page quota.

create a new app with
$rails new book-overload --skip-activerecord
$rails g controller static_pages home

in config/routes set your root path with 
$root, to: 'static_pages/home'

create a request model with
$rails g model request --skip-migration

rails g mailer SelectionMailer
use letter opener to preview emails

Using nokogiri and open-uri to make api requests to goodreads


https://github.com/brandonhilkert/sucker_punch#active-job

http://edgeguides.rubyonrails.org/active_job_basics.html