---
layout: post
title: 'Rails 6.0: Action Mailbox, Action Text, Multiple DBs, Parallel Testing, Webpacker by default, and Zeitwerk'
categories: releases
author: dhh
published: true
date: 2019-08-15 10:00:00 -08:00
---
Dealing with incoming email, composing rich-text content, connecting to multiple databases, parallelizing test runs, integrating JavaScript with love, and rewriting the code loader. These are fundamental improvements to the fundamentals of working with the web and building fast and fresh applications. This is the kind of work we've been doing for the past fifteen years, and we're still at it. THIS IS RAILS SIX!

And that's just the headline improvements! Since Rails 5.2 was release a little over a year ago, we've continued our high pace of improvement all over the framework. In 2019 alone, we've [had 341 code contributors](https://contributors.rubyonrails.org/contributors/in-time-window/this-year) submit improvements and fixes. We've tried to summarize just some of the goodies in [the release notes](https://edgeguides.rubyonrails.org/6_0_release_notes.html), but there are many more than that.

While we took a little while longer with the final version than expected, the time was spent vetting that Rails 6 is solid. In fact, GitHub, Shopify, and Basecamp, as well as plenty of other companies and applications, have been running the pre-release version of Rails 6 for months and months in production. We might not have caught everything, but if it's good enough for GitHub, Shopify, and Basecamp, it's probably good enough for you too!

So what are you going to get with Rails 6? Check it out:

[Action Mailbox](https://weblog.rubyonrails.org/2018/12/13/introducing-action-mailbox-for-rails-6/) routes incoming emails to controller-like mailboxes for processing in Rails. It ships with ingresses for Mailgun, Mandrill, Postmark, and SendGrid. You can also handle inbound mails directly via the built-in Exim, Postfix, and Qmail ingresses. The foundational work on Action Mailbox was done by George Claghorn and yours truly.

[Action Text](https://weblog.rubyonrails.org/2018/10/3/introducing-action-text-for-rails-6/) brings rich text content and editing to Rails. It includes the Trix editor that handles everything from formatting to links to quotes to lists to embedded images and galleries. The rich text content generated by the Trix editor is saved in its own RichText model that's associated with any existing Active Record model in the application. Any embedded images (or other attachments) are automatically stored using Active Storage and associated with the included RichText model. The foundational work on Action Text was done by Sam Stephenson, Javan Makhmali, and yours truly.

The [new multiple database support](https://github.com/rails/rails/pull/34052) makes it easy for a single application to connect to, well, multiple databases at the same time! You can either do this because you want to segment certain records into their own databases for scaling or isolation, or because you're doing read/write splitting with replica databases for performance. Either way, there's a new, simple API for making that happen without reaching inside the bowels of Active Record. The foundational work for multiple-database support was done by Eileen Uchitelle and Aaron Patterson.

With [parallel testing support](https://github.com/rails/rails/pull/31900), you can finally take advantage of all those cores in your machine to run big test suites faster. Each testing worker gets its own database and runs in its own thread, so you're not pegging one CPU to 100% while the other 9 sit idle by (y'all do have a 10-core iMac Pro, right 😂). Hurray! The foundational work for parallel-testing support was done by Eileen Uchitelle and Aaron Patterson.

Webpacker is now the default JavaScript bundler for Rails through the new app/javascript directory. We're still using the asset pipeline with Sprockets for CSS and static assets, though. The two integrate very nicely and offer the best trade-off of advanced JavaScript features with an it-just-works approach to other assets.

[Xavier Noria's new Zeitwerk code loader for Ruby](https://medium.com/@fxn/zeitwerk-a-new-code-loader-for-ruby-ae7895977e73). No more const_missing, no more code loading gotchas, hello Module#autoload!

Those are just some of the marque additions, but Rails 6.0 is also packed with minor changes, fixes, and upgrades. Just some I'd call out: [Proper Action Cable testing](https://github.com/rails/rails/pull/33659#issue-209385961), Action Cable JavaScript rewritten in ES6, protection against DNS rebinding attacks, and per-environment credentials. Also, Rails 6 will require Ruby 2.5.0+ now. You can check out everything in [the individual framework CHANGELOG files](https://github.com/rails/rails/tree/v6.0.0) for the nitty-gritty rundown.

This release was shepherded by release manager Rafael França with support by Kasper Timm Hansen.

Thanks again to everyone who keeps working on making Rails better! Thanks to everyone who uses Rails! I'm incredibly proud to see this open-source framework continue to thrive outside the pressures of market terms and reciprocal guilt. [This is a gift we give each other and expect nothing in return](https://www.youtube.com/watch?v=VBwWbFpkltg).
