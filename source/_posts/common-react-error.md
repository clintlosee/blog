---
title: Common React Error
date: 2016-04-20 09:43:34
intro:
category: Front-End Development, React
tags: React, JavaScript, Errors
---
![Common React Error](/blog/images/common-react-error.jpg)

## A React Error You May Have Encountered

As I’ve been progressing in my learning and helping others with React, a common error has surfaced in [React](https://facebook.github.io/react/) development. So I figured I could potentially help some people out who are new to React and provide a solution to what I’ve found on this error.

What’s this error, or warning, you may be asking? Well it’s this:

`Warning: React.createElement: type should not be null, undefined, boolean, or number. It should be a string (for DOM elements) or a ReactClass (for composite components).`

Or this one:

`Uncaught Invariant Violation: Element type is invalid: expected a string (for built-in components) or a class/function (for composite components) but got: object.`

What causes this? Well here’s what I’ve found can cause this often very frustrating error when you’re starting out in React Development.

Without going into all of the setup and inner-workings of a React site or component, there are two common scenarios I’ve seen that cause these errors. One instance is when setting up routing in your app using [React Router](https://github.com/reactjs/react-router). In this case, you have your Routes.jsx file (or whatever you name your routing file) and inside that file you have something set up like the following:

``` javascript
var React = require('react');
var ReactRouter = require('react-router');
var Router = ReactRouter.Router;
var Route = ReactRouter.Route;

var Base = require('./components/base.jsx');
var PageOne = require('./components/pageone.jsx');
var PageTwo = require('./components/pageTwo.jsx');

var Router = (
    <Router>
    	<Route path="/PageOne" component= {PageOne}></Route>
    	<Route path="/pageTwo" component= {PageTwo}></Route>
    </Router>
);

module.exports = Router;
```

You’ll notice when creating var Router it is set up using (…). This isn’t creating a React Class like you usually would with React.createClass. That means you need to set this up differently in your main.jsx file. In that file, when rendering a component with React-DOM you would do something like the following:

``` javascript
var React = require("react");
var ReactDOM = require("react-dom");
var ListManager = require('./components/ListManager.jsx');

ReactDOM.render(<ListManager />, document.getElementById('ght'));
```

However, when rendering your routes file where you did not create a React class, you would need to use the following format (pay attention to the ReactDOM.render method):

``` javascript
var React = require("react");
var ReactDOM = require("react-dom");
var Routes = require('./routers.jsx');

ReactDOM.render(Routes, document.getElementById('ght'));
```

When setting up this type of routing, you omit the <... /> from your render method and just use your variable name for your route file. Watch out for that if you are running into this error when starting out learning React. If that isn’t the case, check out the next one.

### Another Scenario For This React Error
Another scenario I have come across in helping others out with [React](https://facebook.github.io/react/) is a common error in JavaScript in general.

One of the weird parts of JavaScript has to do with semicolons. Debates abound about this and I’m not going to get into it. ES2015 helps this issue out, but again, that’s another topic.

What I’m talking about is how JavaScript terminates line endings. You may not be aware but JavaScript sees the end of a line and can sometimes insert it’s very own little semicolon without you wanting it to. This can cause huge problems, especially on return statements. Here’s what I’m talking about and where I’ve seen this in React.

Take the following code plucked from a React component:

``` javascript
var List = React.createClass({
    render: function(){
    	var createItem = function(text,index){
    		return <ListItem key={ index + text} text = {text} />;
    	};

    	return
        (
            <ul>
                {this.props.items.map(createItem)}
            </ul>
        );
    }
});
```

The return statement in the React class shows the return and then the `(` on the next line. This is a common coding convention in many other languages, one such is Java. This can cause some major problems in JavaScript though. What you need to make sure you do to format this is as follows (return statement pulled out of the above code for reference):

``` javascript
return (
    <ul>
        {this.props.items.map(createItem)}
    </ul>
);
```

Move that `(` up to directly after your return statement and you can save yourself loads of time researching errors of undefined being returned. It’s a weird one, but it’s out there.
