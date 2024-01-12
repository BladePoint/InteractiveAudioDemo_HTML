# InteractiveAudioDemo_HTML
This is a web-based HTML demo of the Interactive Audio Engine implemented in JavaScript. See it in action at any of these sites:  
https://www.newgrounds.com/portal/view/913019  
https://bladepoint.github.io/InteractiveAudioDemo_HTML/  
https://bladepoint.heliohost.us/demo

Download the latest version from the Dropbox link near the upper right corner:  
https://github.com/BladePoint/InteractiveAudioDemo_HTML.git  

You can replace the audio and script with your own content to make your own adventure! Unfortunately, if you attempt to view it locally off your hard drive, your browser will probably give you CORS errors and it won't work. Your browser's CORS policy prevents loading certain types of content from a different domain for security reasons. Strangely, it considers local JavaScript files to be another domain even if everything is just on your hard drive. You will have to do one of the following to get around this:
1. Disable Cross-Origin Restrictions in your browser, then view the HTML. This is not recommended for security reasons.
2. Upload the files to a website and view them that way. This might seem like the most convenient way, but you would have to reupload every time you want to view any changes you make. Also, your browser might display the old cached version instead, so you have to clear your cache or do a hard refresh every time. On PC browsers, a hard refresh is typially done by pressing Ctrl + F5. On Macs it is Cmd + Shift + R.
3. Set up a local web server on your computer, copy the files onto it, and serve them to yourself locally. This is probably the best way, but how to do that is beyond the scope of this readme.

The script.iae file controls the flow of audio that is played and the choices that are presented. It is simply an XML file so you should be able to open and edit it in any text editor. There are 8 main elements that are the building blocks used to make an Interactive Audio Adventure.

## 1. `<scene>`
The `<scene>` element is used to logically divide different parts of your adventure. They are not actual destination points that can be traversed. That type of element is the `<node>`, which `<scene>`s are a collection of.

## 2. `<node>`
The `<node>` element is a branching point in the flow of logic. Typically a `<node>` has `<prompt>`s and `<choice>`s.

## 3. `<prompt>`
A `<prompt>` is an audio file that is to be played when the player arrives at a `<node>`. If a `<node>` has several `<prompt>`s, they will be played in succession. If a `<prompt>` has child `<condition>`s, they all must be true in order for the `<prompt>` to be included in the play list. Otherwise the `<prompt>` will be ignored.

## 4. `<choice>`
A `<choice>` is what allows the player to determine the course of the game. For every `<choice>` that a `<node>` has, a button will appear for the player to select. A `<choice>` may have `<condition>` children as well, and all of them must be true in order for the `<choice>` to be displayed. All `<choice>`s must have a child `<goto>` that leads to the next destination if selected.

## 5. `<goto>`
The `<goto>` element indicates which `<node>` the game should flow to next. A `<goto>` may be the child of a `<choice>`, or it may be the child of a `<node>` if and only if that `<node>` has no `<choice>`s. A parent may have multiple `<goto>` children, in which case the first `<goto>` that evaluates as true will be executed.

## 6. `<var>`
Near the beginning, a script should have a `<Variables>` element with `<var>` children for each variable you need to use in the game. These can be used to keep track of decisions the player has made, such as items that have been picked up.

## 7. `<condition>`
 A `<condition>` tests the value of a `<var>` using an operator against a number. The `<condition>` is considered true if the `<var>`'s value passes this test. If a parent has multiple `<condition>`s, all of them must be true for the parent to be considered true. A parent with no `<condition>`s is automatically considered true.

## 8. `<modifyVar>`
A `<modifyVar>` is used to change the value of a `<var>`. A `<modifyVar>` may be the child of a `<prompt>`. When the player reaches the `<prompt>`s parent node, if that `<prompt>` is true, the <modifyVar> will be executed.
