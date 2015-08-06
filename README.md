# Read about this here https://github.com/h5bp/lazyweb-requests/issues/186

### Preface 
I recently started using Google Tag manager and liked the way I could setup little snippets of code to run on certain pages. You can trigger these snippets to either run on all pages or on certain pages based on what was in the URL.

I had a quick idea to try and use the async loading of TM and a trigger in the URL to have a suite of tests or tools run on my site and give me feedback. 

### Idea
Setup a collection of common best practice tests or pitfalls for developers to try and avoid or fix when they are making their sites and have them run in realtime in some way. The tests should run without being seen, unless the user wants to see an output.

These tests will run directly on the site and can cover anything. 
##### Example Tests
* Are any resources being loaded in with a protocol relative URL - flag them to the user
* How many CSS rules do you have in total - IE8 & IE9 limitations
* How much of the CSS is NOT being used by this current page - Warn if over a certain percent (80% perhaps)
* Warn is page load time is over 1 second - best practice can be measured by Navigation Timing

Also provide the users with a handy list of Tools they can use. These would be an opinionated tool set that we think would help users out in some way or an other, so these examples are just to show what I mean

##### Example Tools
* Highlight all BEM objects on a page for display / debug purposes (https://github.com/AaronLayton/bem-highlighter)
* Show all colours used on a page (https://bgrins.github.io/devtools-snippets/#allcolors)
* Generate a sprite of all the images on the page

### Implementation
Tag Manager was an initial idea to load these tests onto a dev site, but the community would not be able to manage each tag on TM, instead some solution should be made with Github.

Test and Tools will be loaded async after window load so as not to impact normal development. Show a GUI only when there is a querystring present - something like ?wpt_debug

Each test and tool should be a separate JS file in a Github repo and return the following
* Test status - pass || fail
* Link to the GIthub file so the user can see the test code

A master JSON file could be created that holds the URL's for all live Tests / Tools and a small script on the site could load this first and then Async load the tests in. Tools will be listed but only loaded in when the users clicks on.

All files could be served from https://rawgit.com/ but I havn't used the site myself so not sure how good it is.

#### Mock
I chucked something together to give a rough idea of what I envision for the GUI. 

http://codepen.io/AaronLayton/pen/waNPXJ

<img width="562" alt="wpt" src="https://cloud.githubusercontent.com/assets/694964/9101031/a2e8f78a-3bd9-11e5-8849-e40647405db1.PNG">


#### Moving forward
Lets discuss!!

Is there something like this already? Could some other website be used to perform this but allow us to share a list of tests? Is this a stupid idea? Would it be useful to some people?

It's late and I figured I would share to see what everyones thoughts are.

I have created a repo here - https://github.com/AaronLayton/WebPlatformTools
I plan on working on the above initial idea and loading in the GUI and placing the code there
