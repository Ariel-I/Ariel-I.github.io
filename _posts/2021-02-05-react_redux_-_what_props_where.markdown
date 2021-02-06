---
layout: post
title:      "React / Redux - What Props Where?"
date:       2021-02-06 02:05:27 +0000
permalink:  react_redux_-_what_props_where
---


First, let me say that React and Redux are fantastic tools for JavaScript and open a lot of fun avenues for developers. I have personally enjoyed the developer tools Google Chrome offers as it makes debugging a sinch, especially when finding state and components! One of the simplest aspects of React that had me up reading into the wee hours of the night was truly understanding the difference between stateless components and stateful components. I know I’m a newb for no understanding what should be obvious seeing as its literally in the wording – stateful vs stateless – but when I began my project I was SO confused about how stateless components were being passed props. Let’s start with the basics;
Stateful Components AKA Container Components:
```
class App extends Component {
   constructor() {
      super()
         this.state = {
                 items: []
           }
      }
          render(){
              return (
                   <div>
                       <h2><Todos items={this.state.items}</h2>
                    </div>
                )
            }
} 

```

To *state* the obvious, heheh, this component holds the state within and can use the state to render params on a webpage.
Now, let's take a look at a stateless component.

Stateless Components AKA Presentational Components:
```
const Todos = ({items}) => {
        return (
             <ul>
                {items.map(item => {
                       return <li>item</li>
                })}
             </ul>
        )
}


```

Clearly the about component has not listed state anywhere. What baffled me was how a stateless component like the one above has access to any parameters or props or state. Upon closer look however, there is a very important aspect that I admit I didn't catch onto until I was already nearly done with my project. 
**Stateless components will not work without a parent component that does in fact hold the state aka a stateful parent component**

In the above example the *stateless* child component is being passed down props from the almighty *stateful* parent component. The important part of code to note here is the h2 element; 
```<h2><Todos items={this.state.items}</h2>```
This element is importing the Todos child component(stateless) and handing it the props with a key of items pointing to {this.state.items}. without that little bit of code the statless component would have no idea about its' state. We then use the props handed in and map through to get all of the items. It's as simple as that! For me, the biggest part of understanding how these components worked was first understanding their relationship then not forgetting that the relationship is connected through importing and exporting the components and of course not forgetting to hand the stateful props down to the stateless component. 

After fully understanding how these componets worked together I had a lot  of fun removing presentational code in my project from non-presentational components and dressing up the views in stateless components. It gives so much more room for designing a beautiful webpage with tons of flare without causing tons of codebloat in components that hold important logic. 


