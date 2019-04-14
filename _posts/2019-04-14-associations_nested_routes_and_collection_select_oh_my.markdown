---
layout: post
title:      "Associations, Nested Routes, and Collection_Select, Oh My!"
date:       2019-04-14 21:48:37 +0000
permalink:  associations_nested_routes_and_collection_select_oh_my
---


I know it's very common to mention how far you can come in just a couple months of coding bootcamps, but I am proud to be where I am.  A little under two months ago, I had only built my first gem to scrape headlines from a news website, and now I'm building a fully functional rails application.  

However, my Rails Project for Flatiron School did not come without a lot of opportunities to learn and improve (aka difficulties).  I would like to share some tips so that any new rails programmers can hopefully learn even more efficiently than I did.  

My Rails Project is called PetMed: a content management system where a user can create and store their pets' information and book veterinary appointments from a selection of vet providers in their area.

**My first tip:** never forget to add object attribute columns to the object's table in the form of foreign id's, or to the object's controller params in the form of permissable attributes.  I made a decision later in my coding that I was having too many issues connecting a user's pets to the appointment because I had `pet belongs_to :user` and `appointment belongs_to :user`, but appointment and pet were only connected through user (`pet has_many_appointments, through: :user`, `appointment has_one_pet, through: :user`).

After I decided to make this change in my appointment model to say `belongs_to :pet` as well, I failed to run rails g migration `AddPetIDToAppointments pet_id:integer`.  Of course, if you don't create the foreign key so the appointment knows what particular pet it's associated to, you'll find yourself with a lot of headaches.

As I said, I also failed to add pet_id to the appointments controller, but corrected myself:

```
  private

  def appointment_params
    params.require(:appointment).permit(:reason_for_visit, :date_time, :user_id, :vet_provider_id, pet_id)
  end

```

Again, avoid the headache, and write a checklist when adding new associations (or creating them in the first place).


**My second tip:** typing rails routes in your console is an incredible tool whether you're a beginner or not.  For this application, I needed some nested resource routes:

```
  resources :users, only: [:show] do
    resources :pets
  end

  resources :users, only: [:show] do
    resources :appointments
  end
```

However, there are wonderful and frustrating aspects to nested routes because while you can create more dynamic functionality for your associated objects, you also have to be mindful of Rails' genius.  Rails likes to assume a lot of things, so in my case where I was creating a new pet, rails wants to assume it should take you to a url of `pets/new`, but in my case, a pet should never be created unless that pet has an owner.  This would be a route of `owners/id/pets/new`.  How do I know this?  Because after I created my routes, I ran `rails routes | grep pet` (to see only pet routes) and saw this:

```
        user_pets GET      /users/:user_id/pets(.:format)                                                           pets#index
                              POST     /users/:user_id/pets(.:format)                                                           pets#create
        new_user_pet GET      /users/:user_id/pets/new(.:format)                                                       pets#new
        edit_user_pet GET      /users/:user_id/pets/:id/edit(.:format)                                                  pets#edit
        user_pet       GET      /users/:user_id/pets/:id(.:format)                                                       pets#show
                                 PATCH    /users/:user_id/pets/:id(.:format)                                                       pets#update
                                 PUT      /users/:user_id/pets/:id(.:format)                                                       pets#update
                                 DELETE   /users/:user_id/pets/:id(.:format)                                                       pets#destroy
```

If we look at pets#new to the right, we can see the route to the left of it is as stated above.  So what does that mean for my pets controller and views?  In my controller, I have to make sure to associate my new pet with the user_id (which is a column on the pets' table).  

Pets Controller 

```
def new
    if params[:user_id] && !User.exists?(params[:user_id])
      flash[:notice] = 'User not found.'
      redirect_to new_user_registration_path 
    else
      @pet = Pet.new(user_id: params[:user_id])
    end
  end

  def create
    @pet = Pet.new(pet_params)
    if @pet.save 
      @user = current_user
      redirect_to user_pet_path(@user, @pet)
    else
      render :new
    end
  end
```

In pets#new view, I have to make sure the form includes a url that calls out the user and the pet so it gets the association right:

Pets#new top of form:

```
<%= form_for @pet, url: user_pets_path(@pet.user) do |f| %>
...
```

These can be tricky, but keep practicing and never forget the tools you're already given (rails routes, rails console, etc).


**Final Tip:** make sure to understand `collection_select` before you use it in a form; don't just copy it from somewhere else you've seen it.  [This forum](https://stackoverflow.com/questions/8907867/can-someone-explain-collection-select-to-me-in-clear-simple-terms) on Stack Overflow explains it better than anywhere else I've seen it, and if you just need a drop down of selections from an array you created, just use `collection_select`'s less fancy friend, `select`.  Here is an example of my use of this:

My array method from Pet model:

```
  def self.allowed_types
    %w[Dog Cat Bunny]
  end
```
	
My form field using this array with select:

```
<%= f.select :animal_type, Pet.allowed_types %> 
```

If all else fails, let your errors guide you, and use the vast network of knowledge on Google.  Coding is not about memorizing everything, it's about being able to find the solution.
	
	
	



