# An Introduction to Vue

For the slides, see https://sgelbart.github.io/vue4u-talk

# What's up with Vue?

1. Super simple to add to existing projects
The best thing about Vue is it can be easily used in just about any web app.

2. No tooling or crazy changes?
You don't have to install any command line tools, know about node, compile anything, have any fancy tools, change your folder structure, anything.

3. What do you need to know to get started?
If you know how to work with normal HTML and CSS, and have a basic understanding of JavaScript fundamentals, you are just about ready to go with Vue.
---
# Vue at its simplest...
Follow along at: https://jsfiddle.net/sgelbart/62aq0Lfm/44/

1. Create html page
`https://jsfiddle.net/boilerplate/bootstrap`
2. Add vue
```html
<script src="https://unpkg.com/vue@2.5.21/dist/vue.js"></script>
```
3. Add vue template
Normal template w/ID
Handlebar syntax
```html
	<div id="myElement">
		{{ message }}
	</div>
```
4. Load single variable
```javascript
	var demo = new Vue({
	  el: '#myElement',
	  data: {
		message: 'Hello World'
	  }
	});
```
---
# Add sparkle

5. Add list of content
Make it cooler! Let's spice it up and cycle through some messages to liven up the page a bit...
```html
	<div id="myElement">
		{{ messageOptions[messageIndex] }}
	</div>
```
```javascript
data: {
	...
	messageOptions: [
		'Hola',
		'What\'s Up?',
		'What\'s Crackliackin\'?',
		'Hey hey hey!',
		'Yolo fools'
	]
	messageIndex: 0
},
methods: {
	cycleMessages: function () 	{
      var that = this;
      setInterval(function(){
      	that.i = that.i++%that.messages.length;
      },5000);
	}
}
```
And we want it to have it start changing right away when the component is created. (It could be called on click or something else instead...)

```javascript
created: function(){
	this.cycleMessages();
}
```
---
# Easy Input Binding

5. Add variable binding
Add a custom field..

input with:

```html
<input v-model="customMessage"/>
```

```js
	customMessage: ""
```
Field is automatically set!

(add to input)
```html
{{ customMessage || messageOptions[messageIndex] }}
```

6. Event binding
want to do something on click? On change?
- Validation
- Tooltips
- Submission
When this...do that...
```html
<input v-model="customMessage" v-on:input="logMessage"/>
```

```js
	logMessage: function() {
		console.log(customMessage)
	}
```

Link to final product:
https://jsfiddle.net/sgelbart/62aq0Lfm/13/
---
# Ajax
https://sgelbart.github.io/vue4u-talk/example.html
- Run ajax in created function
- Set returned value to a data field
- Updates once loaded automatically!
- Gotchas: can't use handlebars in attributes
- Also cool...pipes (filters)
---
# Command Line Vue
Tools
- package installation
- .vue files
  - syntax highlighting
  - css scoping
- sass etc
---
# Server side rendering
- Search Engine Optimization
- Faster
- Caching
- Want to know the difference? View the source.
---
# NUXT.js
- Vue's SSR Framework
- Vue templates work backend and continue on front end
- Very easy to use
---
# Let's get started
- Working example: https://codesandbox.io/s/jjj67w4k15
- package.json
- Add axios for ajax
- has it's own server, does things on the fly behind the scenes
---
# SSR Romcoms
- Add our list from the earlier project.
- module exports
- asyncData
- routing
---
# Make better?
- DRY with Components
- Vuex store
---
# UI Goodies
- Element - https://element.eleme.io/#/en-US
- Bootstrap - https://bootstrap-vue.js.org/docs/components/alert
- Material - https://vuetifyjs.com/en/
- Vue's own - https://vuejs.github.io/ui/#/demo/button
---
# Possible Backends
- API - Django API? - most common approach
- SSR MVC (old fashioned Rails, Django)
- SSR MVC & SSR JS via PROXY!
- Firebase!