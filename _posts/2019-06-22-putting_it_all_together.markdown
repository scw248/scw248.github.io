---
layout: post
title:      "Putting it All Together"
date:       2019-06-22 15:34:38 -0400
permalink:  putting_it_all_together
---


For my final project - a React/Redux front-end with a Rails API and backend - I planned on doing what I had done for previous projects: any cracks in my knowledge about the particular language or topic I could figure out during the project because this is the opportunity to test and fail repeatedly until you get it right.  You live in the land of the failing in coding, and it's exciting and fulfilling for me to work my way out of it.

However, what took me by surprise was how much of what I had learned over the last six months of my Flatiron School course was popping up: Ruby API, models, controllers, JSON, Javascript, and React.  Take this action function for instance:

```
export const deleteDestination = (id, currentUser) => {
  return dispatch => {
    return fetch(`http://localhost:3000/api/v1/users/${currentUser.id}/destinations/${id}`, {
      credentials: "include",
      method: "DELETE",
      headers: {
        "content-type": "application/json",
        Accept: "application/json"
      },
      body: JSON.stringify(id)
    })
      .then(response => response.json())
      .then(data => {
        if (data.error) {
          alert(data.error)
        } else {
          dispatch(removeDestination(id))
        }
      })
  }
}
```

For a good fifteen minutes, I was trying to figure out how I could add currentUser.id into my fetch method without importing from the store until I realized, "HEY! This is just plain old Javascript!  The component can provide currentUser, and it can hold as a parameter here!"  

Another example was with my controller on the backend:

```
def create
      @destination = current_user.destinations.build(destination_params)
			
      if @destination.save
        render json: DestinationSerializer.new(@destination), status: :created
      else
        resp = {
          error: @destination.errors.full_messages.to_sentence
        }
        render json: resp, status: :unprocessable_entity
      end
    end
```

For another fifteen minutes, I was wondering why my front-end could not grab data when I was creating a new destination until I realized "OH YEAH!  I only need to render json since React is doing all of the view rendering!  Then I remembered serializing and tried out Netflix's new Fast_JSON_API serializer, and there we go!

I guess the point I'm trying to make is that while React/Redux are not easy to learn and have their own fun challenges, it's the 'putting it all together' that has been so interesting and rewarding to me for this project.  Now when I go onto open source projects, I have a better understanding of what I'm looking at, what goes where, and how 'x' works!

Thanks for a great learning experience Flatiron School!  Over and out!
