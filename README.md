# InteractiveAudioDemo_HTML
This is a web-based HTML demo of the Interactive Audio Engine implemented in JavaScript. See it in action here:  
https://www.newgrounds.com/portal/view/913019  
https://bladepoint.heliohost.us/demo

You can replace the audio and script with your own content to make your own adventure! Unfortunately, if you download everything so you can edit it, then attempt to view it locally off your hard drive, your browser will probably give you CORS errors and it won't work properly. Your browser's CORS policy prevents one domain from loading certain types of content from another domain for security reasons. Strangely, it considers local HTML content to be another domain even if everything is just on your hard drive. You will have to do one of the following to get around this:
1. Disable Cross-Origin Restrictions in your browser, then view the HTML. This is not recommended for security reasons.
2. Upload the files to a web server and view them that way. This might seem like the most convenient way, but you would have to reupload every time you want to view any changes you make. Also, your browser might display the old cached version instead, so you have to clear your cache or do a hard refresh every time. On PC browsers, a hard refresh is typially done by pressing Ctrl + F5. On Macs it is Cmd + Shift + R.
3. Set up a local server on your computer, copy the files onto it, and serve them to yourself locally. This is probably the best way, but you have to learn how to set up a local server.
