---
layout: post
title:      "Sorting in React"
date:       2021-02-17 22:41:31 +0000
permalink:  sorting_in_react
---


Sorting in React is important to understand as it is used often and creates a better experience for those interacting with the app. In my final project at Flatiron School I was able to implement sorting options in order to list nonprofits alphabetically. At first I was concerned with sorting the specific id attributes of the items on the list but with the .localCompare method I was able to reference string instead of integer values within my sort function. 

The sort function I created will list the nonprofits in descending alphabetical order and looks like this;

```let sortDescending = this.props.nonprofits.sort((a, b) => b.name.localeCompare(a.name))```

Sorting without using .localCompare would sort using integer values. For example;

```let sortDescending = this.props.nonprofits.sort((a,b) => b.name > a.name ? 1 : -1)```

These two methods do the same thing but one is using string values to compare and the other is using integer values. 

Ok so now I have my nonprofits ordered the way I’d like them but would like to have the option to see the sorted version as well as the original version that appeared on the page on the first render. The next step is to add a few buttons that will allow me to toggle between views. 

Starting with the code I wish I had in my return statement;

```
<button onClick={this.sortDesc}> Sort Z-A </button>
<button onClick={this.sortOrig}> Sort Original </button>
```

To manage the onClick I’ll hand in the sorted values I created before into a function that I can then call in my buttons onClick;

```
   sortDesc = () => {
        let sortedDesc = this.props.nonprofits.sort((a, b) => b.name.localeCompare(a.name))
        this.setState({ nonprofits: sortedDesc })
    }

   sortOrig = () => {
        let originalList = this.props.nonprofits.sort((a,b) => a.id > b.id ? 1 : -1)
        this.setState({nonprofits: originalList})
    }
```

Now each time a button is clicked the view will render the nonprofit list sorted based on whichever button is clicked. Notice how I sorted using integer values to get the original list back. I did this because the page automatically renders the list of nonprofits based on their personal id from starting from 1 so sorting them by id is ideal when implimenting the original view as apposed to using string values to order by name. I’ll also go ahead and add a sort button from A-Z to add more functionality to the page. 

```
sortAsc = () => {
     let sortedAsc = this.props.nonprofits.sort((a, b) =>  a.name.localeCompare(b.name))
     this.setState({ nonprofits: sortedAsc })
 }

<button onClick={this.sortAsc}>Sort A-Z</button>
```

The user now has the ability to sort through nonprofits alphabetically from A-Z and Z-A with the option to also view the page as it was originally rendered. Having extra usability on a website is important because it encourages the user to interact more in depth with the application. With the ability to sort through nonprofits, a user visiting this page will likely be more inclined to spend more time on the site. 


