# The Modern Web, via Vue

## Part 1: HTML Review

In the beginning, the Internet was created. (This has made a lot of people very angry and has been widely regarded as a bad move.) Someone somewhere invented a way for a lot of computers to talk to each other at once and mostly normal people used this to send text messages back and forth in things like chat rooms. You could also get files from other people's computers using services like FTP and gopher, or type commands that would run on other people's computers using protocols like Telnet (which was a predecessor to what we use today, SSH); but pretty much all communication and all files just consisted of text, and by that I mean plain text. For example, the first computer-to-computer communication over what would eventually become the Internet was [this](https://www.netvalley.com/cgi-bin/intval/net_history.pl?chapter=1):

> Kleinrock, a pioneering computer science professor at UCLA, and his small group of graduate students hoped to log onto the Stanford computer and try to send it some data. They would start by typing "login," and seeing if the letters appeared on the far-off monitor.
> 
> "We set up a telephone connection between us and the guys at SRI...," Kleinrock ... said in an interview: "We typed the L and we asked on the phone,
> 
> "Do you see the L?"
> 
> "Yes, we see the L," came the response.
> 
> "We typed the O, and we asked, "Do you see the O."
> 
> "Yes, we see the O."
>
> "Then we typed the G, and the system crashed."
> 
> Yet a revolution had begun."

So plain text is great if you plan to do technical stuff like logging into remote computers and sending simple commands back and forth. But in other situations, it lacks a certain something.

```text
Warning:

Dangerous radiation levels detected.

Flee immediately!

 - Leave the room
 - Leave the building
 - If possible, leave the metropolitan area
```

If you were designing a computer system that might need to send or display this message, is this how you'd want it to look? I can imagine ways to punch it up a little.

<img src="initial-markup.png" width="600" />

But unfortunately, especially back then, you couldn't just, like, write some notes on some text and have the computer spit out a formatted version. We might want to get more specific:

<img src="specific-markup.png" width="600" />

But really, what we're going to want to do is to try to take this information that I have indicated in this image here and come up with a way to express it within text. Then, we'll be able to send a plain text message over the Internet that gets interpreted and displayed as formatted text. The text that the sending computer sends and the text that the receiving computer displays is pretty much just going to be different. The sending computer is going to send something that looks like this:

```html
<h1>Warning:</h1>
<strong>Dangerous radiation levels detected.</strong>
<h2>Flee immediately!</h2>
<ul>
    <li>Leave the room</li>
    <li>Leave the building</li>
    <li>If possible, leave the metropolitan area</li>
</ul>
```

And the receiving computer is going to display something that looks like this:

# Warning:

**Dangerous radiation levels detected.**

## Flee immediately!

- Leave the room
- Leave the building
- If possible, leave the metropolitan area

So that's the magic trick that HTML lets us pull off. On one hand, we send some plain text that looks really weird, and on the other hand, the receiver displays formatted text that looks nice. And that works because the receiving computer knows to take the HTML and get rid of parts of it and transform the rest when it's displayed to make it look okay.

So, basically, we added some extra text within angle brackets, called "tags." Angle brackets are what we call these: \<>. If you put angle brackets with a name (meaning a word or some initials) inside them, that means "apply the format with this name to the text, starting here"; if you put angle brackets with a slash and then a name, it means "stop applying the format with this name to the text, starting here." The names of formats in HTML are a bit short and cryptic; we have things here like "ul", which means "unordered list", which means "list that uses bullet points and not numbers." And to write in HTML, you just kind of have to memorize all the tag names and what they mean. But that's the easy part, honestly.

And, a word of warning to beginners: HTML, which is what this is, started out as a way to format text, but gradually its uses began to expand and expand until at this point it's also used to divide text and other content on a page into sections so that those sections can then be layed out, in like, rows and columns and things, and sometimes to provide standalone content that has nothing to do with text, like images or videos. And that gets complicated. The little words in angle brackets that initially indicated text formatting now stand on their own to indicate other content and just kind of divide text into abstract sections sometimes. But we'll get through it, I promise.

## Part 2: The Modern Web

So, HTML is all well and good, but in its raw form, it's very non-interactive: the text that you put in the HTML tags just kind of sits there. That's boring. Also, it's not very organized; everything you want to display on web page, you're usually going to have to put in one single file, which can get kind of sprawling and messy. (Unless you use iframes, which introduce other complications, like figuring out what size they should be.) There are a lot of systems that promise to give you the ability to write organized, interactive HTML: React, Svelte, Web Components, Angular, etc, but the one I have chosen to look at today is called Vue. And if you go to this StackBlitz link, *(TODO: add link)* you're going to be able to write some HTML within the Vue framework.

So, as we can see, there are three basic sections in a Vue file. We have the `<template>` section, which is where you put HTML; we'll see why it's called "template" in a second. There's the `<script setup>` section, which is where you can put JavaScript code that makes your HTML changeable and interactive. This code runs once when your page initially loads, kind of like the "main" function in a C++ program. And there's the `<style scoped>` section, which is where you put CSS that lets you change the style and layout of your HTML.

```html
<template>
<!-- HTML content goes here -->
</template>

<script setup>
// JavaScript for interactive content goes here
</script>

<style scoped>
/* CSS for style & layout goes here */
</style>
```

So, yeah, there are three different programming languages involved here, and the default way that you write comments is different in all three of them, because God hates us. This whole thing, which basically creates a piece of a web page that you can also use multiple times, is called a Vue component. Pretty much none of the modern web is created with pure, raw, free-range HTML anymore; instead, you create a little segment of HTML and package some specific, related JavaScript and CSS with it, and the result is called a "component" by various different frameworks and systems.

So, let's go ahead and paste the HTML that I wrote earlier into the "template" section. I'll paste into the chat so you don't have to copy it all down. The result:

```html
<template>
  <!-- HTML content goes here -->
  <h1>Warning:</h1>
  <strong>Dangerous radiation levels detected.</strong>
  <h2>Flee immediately!</h2>
  <ul>
      <li>Leave the room</li>
      <li>Leave the building</li>
      <li>If possible, leave the metropolitan area</li>
  </ul>
</template>

<script setup>
// JavaScript for interactive content goes here
</script>

<style scoped>
/* CSS for style & layout goes here */
</style>
```

So, yeah. In the result pane on the right, you should see formatted text. We put HTML in, and we get formatted text back out. (In this case there isn't really a sending computer and a receiving computer; like, both of those computers are the same one, yours; but the point still stands.)

![image](https://github.com/hacksu/the-modern-web-via-vue/assets/49729978/962b83b9-2c6a-4109-81e7-a70c626a349a)

*TODO: when creating new, different components later, bring up the fact that the styles in a `<style scoped>` tag don't affect other components, which is useful sometimes*

I'm going to take the liberty of adding some basic CSS here to make the result look better. CSS is a language that lets you select some parts of the HTML and then write "rules" that change how they look. So, we can write a CSS selector that selects the "h1" section of the HTML (which stands for header 1, meaning the largest and most important header) and turn it red:

```css
h1 {
    color: red;
}
```

"color" automatically means text color, because, like, when CSS was created, pretty much everything was text, so that's the default assumption. But what I really want to do, to be honest, is to change the font of this whole thing, because serif fonts aren't very warning-y. So, I'm going to write a CSS selector that selects everything; and write a rule that changes the font that's used:

```css
* {
    font-family: sans-serif;
}
```

An asterisk, or "star", is used pretty often in programming to serve as a "wildcard", meaning it represents every possible possibility. In this case, it represents every possible CSS selector and applies the rule that I'm giving here to everything. This says "font-family" instead of "font" because technically, the bold and italic versions of a typeface are different fonts, and this sets all of those. "Sans-serif" is Latin for "without serif". And that's enough CSS for one lifetime.

```html
<style scoped>
/* CSS for style & layout goes here */
h1 {
  color: red;
}
* {
  font-family: sans-serif;
}
</style>
```

So far, this has all been pretty basic HTML and CSS stuff. But what really sets the Vue framework apart from other ways of creating web pages is how it handles HTML templates and JavaScript variables. As the word "template" in the angle brackets for the template tag implies, we don't have to manually type in all of the content that we want to show up on our page. We can also add placeholders that will get filled in later. For example, let's say that we wanted to add someone's name to the warnings. Let's say we wanted to put it in a new item on the bulleted list.

```html
<template>
  <!-- HTML content goes here -->
  <h1>Warning:</h1>
  <strong>Dangerous radiation levels detected.</strong>
  <h2>Flee immediately!</h2>
  <ul>
      <li>Leave the room</li>
      <li>Leave the building</li>
      <li>If possible, leave the metropolitan area</li>
      <li>This means you, {{ name }}.</li>  <!-- new! -->
  </ul>
</template>
```

So, to get our text to be formatted in the list, we have to put it between the start tag and the end tag for the "ul" formatting style, because that means "unordered list", and also between the start tag and the end tag for the "li" formatting style, because that means "list item" and those "li" start and end tags serve to separate different list items from each other. The templatey part of our template is the `{{name}}` part. This double-curly-brace syntax is sometimes called handlebar syntax, because some people think the curly braces look like sideways mustaches, and, well, there you go. For the moment the "name" placeholder in our template is not being filled in with anything. Let's fix that by adding a variable called "name" in our `<script setup>` section:

```html
<script setup>
// JavaScript for interactive content goes here
const name = "Mouch";
</script>
```

So yeah. The idea is that you create variables in JavaScript with certain names, use those names within double-curly-braces as placeholders in your HTML template, and lo and behold, you get the value of your JavaScript variable in the formatted result. You all probably know what a variable is; it's a name that refers to a piece of data in some code. In JavaScript, unlike in C++, you don't need to specify the type of data that a variable stores when you create it; however, you do need to use some keyword to indicate what you're doing and what kind of variable you're creating. The `const` keyword indicates that you're creating a variable that you don't plan on changing later.

Anyway, this still isn't very interesting, since we could get this exact same thing by putting the name in the HTML anyway, as it is hard-coded and doesn't change. Let's replace the simple text we're using in JavaScript with a function call:

```html
<script setup>
// JavaScript for interactive content goes here
const name = prompt("What name do you have ?");
</script>
```

Now we're in business. Now we have some code that asks you what your name is and then uses it to give you a personalized warning about a nuclear reactor meltdown.

## Part 3: State

But the real power of frontend frameworks like Vue is the way that they can dynamically update HTML templates over time. To investigate that, we're going to have to talk about application "state". "State" is a word that basically refers to the values of all of the variables that are part of a given component. It is conceptually and practically separate from the HTML and CSS that dictate how the page is displayed; it's interesting, if we edit our HTML template, even to use the "name" variable again somewhere else, it won't have to ask us for our name again, because the state and the template are separate and changing the template doesn't change the state.

```html
<h2>Flee immediately, {{name}}!</h2>
```

So, that's different from programs you might be used to where when you change one part of the program, the whole thing has to re-run. (It is true that when you change the JavaScript part of the program, then that has to re-run, and then that function call happens and asks you for your name again, and to avoid that happening I'm going to comment that line out for a while. But still.) And the next thing we have to talk about is reactive state. The concept of "state" just refers to the values of your JavaScript variables, separate from the template that displays them; "reactive state" refers to variables that can change later, after your JavaScript initially runs, and update what's displayed in your template.

We're going to create some reactive state in Vue by using the "reactive" function. To do access functions that were written somewhere else by other people in JavaScript, you can use the "import" keyword:

```js
import { reactive } from "vue";
```

This gives us a function that we can call like this:

```js
const state = reactive({

});
```

And in the call to `reactive`, we basically put the state variables we want to be reactive. Technically, what we're doing here is creating a JavaScript object; but unlike in other languages, in JavaScript, you can create "objects" without having to worry about classes (or structs) to provide a blueprint for them; you can just specify some named pieces of data. Although technically they're still called "object properties." In this case, we're going to provide a piece of data that is named `ignoredWarning` and initially stores the Boolean value `false`.

```js
const state = reactive({
    ignoredWarning: false
});
```

We are going to want to be able to update `ignoredWarning` in response to things that this user does on this web page. Like if they ignore a warning. To do that, we're going to want to add a button to our HTML, under the unordered list:

```html
<button>
Ignore this warning
</button>
```

And we're going to add an event listener to this button. An event listener is some code that runs when the user does something on a web page. In this case, we want to listen for the "click" event on the button. To do that in Vue, you just have to do this:

```html
<button @click="state.ignoredWarning = true">
Ignore this warning
</button>
```

Whenever you add an @click attribute to the start tag of an HTML element, you can write code that runs when that element is clicked. This is a very simple event listener; try not to be scared of the fact that a line of JavaScript has escaped containment and is appearing in the template HTML. JavaScript breaks containment a lot. The idea is just that unlike the code in the `<script setup>` section, which executes like a "main" function as soon as the page loads, this line of code will not be run until the user clicks on the button it's attached to.

And then, to represent this true/false value on the screen, we're not just going to display it like we did the name, earlier. Instead, with true/false Boolean values, we usually want to use them in conditional rendering. If you're familiar with "if" statements in other programming languages, you know that they're usually used with true/false values to do something given a certain condition is true. In this case, we want to display a certain message on the screen only if the Boolean variable is true:

```html
<p v-if="state.ignoredWarning">
Nice knowing you!
</p>
```

So this is an example of using reactive state. The `state` variable stores information; that information is used to render a page; initially, the page just uses whatever initial values are stored in the state; but over time, that state can be updated, and the page reacts to those updates, as long as the state is part of an object that was created using a call to the function `reactive`. (There's another common way to create reactive state using a different function called `ref`, but I think `reactive` makes it clearer what's going on in a simple example like this.)

Let's get fancy with our conditional rendering. It turns out that we can divide our template up into smaller sub-templates. Basically, we can take our existing HTML and put it in a template with the main template:

```html
<template>
  <!-- HTML content goes here -->

  <!-- new start tag -->
  <template>
    
    <h1>Warning:</h1>
    <strong>Dangerous radiation levels detected.</strong>
    <h2>Flee immediately, {{ name }}!</h2>
    <ul>
      <li>Leave the room</li>
      <li>Leave the building</li>
      <li>If possible, leave the metropolitan area</li>
      <li>This means you, {{ name }}.</li>
    </ul>
    <button @click="state.ignoredWarning = true">
      Ignore this warning
    </button>

    <p v-if="state.ignoredWarning">Nice knowing you!</p>

  <!-- new end tag -->
  </template>

</template>
```

Then, we can use the same `v-if` syntax to only show the content we've been using if the warning hasn't been ignored yet:

```html
  <!-- new start tag -->
  <template v-if="!state.ignoredWarning">
```

And we can add another sub-template directly underneath:

```html
<template>
    <!-- HTML content goes here -->

  <!-- new start tag -->
  <template v-if="!state.ignoredWarning">
    
    <h1>Warning:</h1>
    <strong>Dangerous radiation levels detected.</strong>
    <h2>Flee immediately, {{ name }}!</h2>
    <ul>
      <li>Leave the room</li>
      <li>Leave the building</li>
      <li>If possible, leave the metropolitan area</li>
      <li>This means you, {{ name }}.</li>
    </ul>
    <button @click="state.ignoredWarning = true">
      Ignore this warning
    </button>

    <p v-if="state.ignoredWarning">Nice knowing you!</p>

  <!-- new end tag -->
  </template>

  <!-- new start AND end tags: -->
  <template v-else>

  </template>


</template>
```

And we can put content in this other sub-template that we only want to show up if the warning Is ignored. Just like you can create an "else" block in most programming languages to contain code that you want to run if some condition Isn't true, you can add `v-else` to the start tag of an HTML element if you want it to show up if the condition in the preceding `v-if` Isn't true. (By the preceding `v-if`, I don't mean the `v-if` inside the preceding element, on the `<p>`; I mean the `v-if` on the preceding template. `v-else` looks for the `v-if` on the start tag that corresponds to the end tag that's immediately before the `v-else`.)

Inside this `v-else`ified template, we're going to put a petting zoo, because why not. Change the button to:

```html
<button @click="state.ignoredWarning = true">
    Ignore this warning and proceed to the petting zoo
</button>
```

And inside the petting zoo, we'll add:

```html
<template v-else>
    <h1>Petting zoo</h1>
    <img
        src="https://hacksu.com/animals/alpaca.jpg"
    />
</template>
```

This new HTML tag, which stands on its own and doesn't need an end tag because it encloses no text content within it, displays an image. Remember what I said earlier: HTML tags eventually stopped just wrapping text and eventually came to represent content all by themselves? This is an example of that. Let's take it one step further and make this an even more forceful example of that by adding a new component. Can you create a new file called "Animal.vue" in the components folder?

## Part 4: Components

In Animal.vue, we're going to want to create a new template and paste in the image tag we were just using:

```html
<template>
    <img
        src="https://hacksu.com/animals/alpaca.jpg"
    />
</template>
```

And then, if we add this to our Vue `<script setup>`:

```js
import Animal from './Animal.vue';
```

And change our petting zoo to this:

```html
<h1>Petting zoo</h1>
<Animal />
```

We have the same result as before. Except, we can create two animals without needing to have that long URL there twice:

```html
<h1>Petting zoo</h1>
<Animal />
<Animal />
```

Maybe "avoiding having a long URL twice" isn't an obvious enough benefit to justify creating a new file and exiling our content to it. But there are others. Crucially, both of these animals will have separate, non-shared, duplicate state. Let's see what that looks like, by adding state to the Animal component:

```html
<template>
  <img
    @click="state.timesPetted += 1"
    src="https://hacksu.com/animals/alpaca.jpg"
  />
  <p>Times petted: {{state.timesPetted}}</p>
</template>

<script setup>
import { reactive } from "vue";

const state = reactive({
  timesPetted: 0
});

</script>
```

Now we can pet each animal separately. When we put two animals on the page, we not only create two copies of the HTML that displays the image, but also of the state that each animal holds. This is the real power of Vue components; by bundling together state, style and HTML, we can easily reuse everything we need to add a feature in multiple places on a web page.

There's one more feature of Vue that I think we need to go over today, which is "computed properties". A computed property is basically a function that gets automatically re-called when the state variables that it uses in its computations change.

So, if I add a state variable to our reactive object like this:

```js
const state = reactive({
  timesPetted: 0,
  radiationLevel: 5
});
```

I can create a computed property like this:

```js
function getImageURL(){
  if (state.radiationLevel > 10){
    return "https://hacksu.com/animals/alpaca-fire.gif";
  } else {
    return "https://hacksu.com/animals/alpaca.jpg";
  }
}

const imageURL = computed(getImageURL);
```

So, the magic part about this function is that the value of `imageURL` is now linked to the function `getImageURL` and the state variable that it references, `state.radiationLevel`. Essentially, `imageURL` is a variable that indicates the first string whenever it's the case that the radiation level is greater than 10, and the second whenever it's not. A computed property is basically like a function that calls itself whenever the value that it returns needs to change.

To use it in the template, let's do this:

```html
  <img
    @click="state.timesPetted += 1"
    src="imageURL"
  />
```

Actually, that's not quite right. "imageURL" in this context will still get interpreted as a string URL, or really just as a string filename, when we actually need it to get interpreted as a variable name so that that variable's value is used. Normally, you switch between having things be interpreted as variable names or strings by adding or removing quotation marks from them in code, but in the case of Vue templates, for whatever reason, you add a colon before the attribute name that goes before the variable name:

```html
  <img
    @click="state.timesPetted += 1"
    :src="imageURL"
  />
```

This causes `imageURL` to be interpreted as a variable so that its value is used. Now the URL that it's storing will be used as the source for the image.

There's another way to update state over time without user interaction, which is to set a timer. The JavaScript function `setInterval` will call another function of your choosing every so often, in an interval measured in milliseconds:

```js
function raiseRadiationLevel(){
  state.radiationLevel += 1;
}

setInterval(raiseRadiationLevel, 1000);
```

To counteract this, we can add another state update to the click listener on the image tag:

```html
  <img
    @click="state.timesPetted += 1; state.radiationLevel -= 1"
    :src="imageURL"
  />
```

So yeah. There we have it. Pet the animals.

Final product link: https://stackblitz.com/edit/vitejs-vite-iujq8e?file=src%2Fcomponents%2FAnimal.vue
