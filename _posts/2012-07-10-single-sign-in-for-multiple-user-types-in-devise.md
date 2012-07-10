---
layout: post
title: "Single sign in for multiple user types in Devise"
description: ""
category: 
tags: []
---
{% include JB/setup %}

*I'm Jesse Pollak, a rising sophomore at [Pomona College](http://pomona.edu). This summer, I'm a [hackNY](http://hackny.org) Fellow and technical intern at [BuzzFeed](http://buzzfeed.com). To assist in my learning process, I've decided to write a blog post every day: today is day 49. You can [follow me on twitter](http://twitter.com/jessepollak) or keep reading my [blog](http://jessepollak.me).*

For [Mentor.im](http://mentor.im), we are using [devise](https://github.com/plataformatec/devise/) to do user authentication. The way we've written the models, we have two distinct users: mentors and mentees. While for most of what we are doing, this is a logical split, having two sign in pages (1 for mentor, 1 for mentee) was deemed bad UX by Conway. Therefore, over the past few hours, I've been trying to figure out the best way to do single sign in for 2 user models with devise. While I'm definitely not sure that this is the best solution, I thought I'd put it on the internet in case other people are having a similar problem.

The basic premise of the solution is to choose one user type as your "main" user type, then route sign in through that controller and readjust the user type appropriately. Accordingly, I chose the mentor user type as the "main" user type:

*/config/routes.rb*

    devise_for :mentors, controllers: { sessions: 'sessions' }
    
    devise_scope :mentor do
      match '/sign_in' => 'sessions#new'
    end
    

The first line produces the routes for :mentors and sets the sessions controller (the one used for signin/signout) to be a custom controller. The second batch of code simply maps `/sign_in` to the normal mentor sign in page (what would otherwise be `/mentors/sign_in`).

With that in place, I just need to prepare the new controller.

*/app/controllers/sessions_/new_controller*


    class SessionsController < Devise::SessionsController
      layout :false
    
      def create
        unless Mentor.find_by_email(params[:mentor][:email])
          auth_options = {scope: :mentee, recall: 'sessions#new'}
          resource_name = :mentee
          warden.config[:default_scope] = :mentee
          params[:mentee] = params.delete(:mentor)
          resource_name = :mentee
        else
          resource_name = :mentor
          auth_options = {scope: :mentor, recall: 'sessions#new'}
        end
        resource = warden.authenticate!(auth_options)
        set_flash_message(:notice, :signed_in) if is_navigational_format?
        sign_in(resource_name, resource)
        respond_with resource, :location => after_sign_in_path_for(resource)
      end
    
    end
    
The bottom 4 lines of code in this section are copied directly from the source code of the devise sessions controller create action. The unless/else statement is the magic that makes it work with either user type.

In the unless statement, I check to see if there is a mentor in the database with that email. If there is, I set the resource_name and auth_options to what would be the defaults regularly. If there isn't a mentor with that email, I rejigger everything to make it be mentee-centric. With these changes in place, you can successfully log in with eithe type of user.

There are some problems with this implementation, however. Primarily, a variety of other devise-centric functionality (like 'forgot my password') needs to be rewritten to handle these cases as well.

Does anyone else have a better solution? Or see something I'm doing wrong? Let me know in the comments.
