---
layout: post
title:      "Rails Project "
date:       2020-12-04 17:44:45 -0500
permalink:  rails_project
---


Well this one was a doozy to say the least. Learning rails has been really exciting but also very difficult. There are just SO many things rails can do. After working with vanilla Sinatra it seems like rails has an endless amount of magic available. It was only after writing my “Santa’s Workshop Rails App” that I was truly exposed to the magic. That being said, the magic wasn’t always helpful. There were so many times that I would add new code and break something somewhere else because I didn’t understand the full scope of how much magic was being created. It took a little while, but I began really understanding the methods used and where everything was going (aka flow). 


Project weeks always feel like they go by way too fast. What I have come to learn though, is that as hard as the project may seem I always come out at the end of the week with a working app, a load of anxiety lifted from my chest, and having learned a TON. As much as the lessons prepare you, actually coding an app from begin to end is a whole different beast. I was nervous about this project because it seemed so huge and I worried I would never fully understand ‘joins tables.’ As is turns out, and like every developer I know has said, the repetition that comes with coding really does help set it in your mind. I created my Santa’s Workshop app but only after beginning an app about astrology. I didn’t get too far before changing my mind but rewriting the code helped me understand more clearly the paths I needed to take at least for the first little bit. I even decided that I’m going to follow through with building my astrology app in my free time for extra experience! I didn’t expect to enjoy coding as much as I do now and I think the further we get with our projects the more exciting it becomes. In the end I had a lot of fun (in between anxiety driven hours of coding) and am looking forward to the next project.

One of the cooler methods that was required for this project is the *scope* method. According to Ruby Guides, "scopes are custome queries that you define inside your Rails models with the *scope* method." The scope that I used in my app was one that finds the most expensive gift the user has logged within the app. Setting it up went something like this...

1. Create the scope in the gifts model ```scope :most_expensive_gift, -> {where(cost: self.maximum(:cost))}``` 

2. Define a method within the gifts controller called ```most_expensive_gift```

3. Add the logic to the ```most_expensive_gift``` method and render the index (aka the page where the scope will be used)

4. Create a route that knows about the scope 

      ``` get 'gifts/most_expensive_gift', to: 'gifts#most_expensive_gift', as: 'meg'``` 
			
5. Lastly, add the route logic to the index page where the scope will be seen by the user 

     ```<%= link_to "See Most Expensive Gift", meg_path %>```
		 
		 
And voila! A working scope method that finds the most expensive gift for the user. 

An aspect that was kind of fuzzy to me when writing the scope was how to write the route properly without needing to call on any params. The route that is shown above was originally way different looking and was refactored to look as clean as it does now. ```get 'gifts/most_expensive_gift``` is using the gifts route and will be what seen in the url when the user navigates to the scoped method. ```to: 'gifts#most_expensive_gift``` is grabbing the most_expensive_gift method from the gift controller and the ```as: 'meg'``` is a helper used to grab the meg_path in the index link, without it I could have handed in the ```'gifts/most_expensive_gift'``` instead  of mag_path in step 5 but meg_path is faster and cleaner on the page so I went ahead and used that. Routes can be dauting but once I understood what each part of the route was doing it was easier to ensure the code was working properly throughout other files. Another important thing to note is how most_expensive_gift has its own method in the gifts controller and is not inside of the index method. I made that mistake at first but was able to refactor the scope in its own method which then allowed me to call on that method from the route making for more logically placed code =D

Overall scopes are pretty straight forward and a fun way to add more user capabilities. If I were to continue adding to my app, I would likely add a scope that allows the user to organize their gifts from cost: low -> high and vice versa. I could even add a search bar for the user to search for a specific gift. One of the reasons project weeks are so essential is because of how they push you as a developer to learn new things that you may not have learned otherwise. Before this I would have had no clue how to use scopes in app but now, I understand the magic they provide to the user and even find myself curious about how the sites I personally visit could be potentially using scope methods. 

             

