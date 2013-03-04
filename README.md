Make your KA Lite installation lighter, put a bird on it.

# About
When placed in your KA Lite's installation directory, open start.html for serverless browsing of your KA Lite's videos and exercises. 

# Installation
Place this directory in your KA Lite directory and then open the start.html file. Your done! Well, almost.  This includes a pruned version of the topics.json file because most browsers (Chrome, Android web browser) will choke (QuataExceeded: DOM Exception 22) if you put that into localStorage. You may want to roll your own topics.json file or help out with the efforts to make a file system based JSON store so the whole topics.json doesn't have to be loaded all at once (see GIST https://gist.github.com/rjsteinert/5080816). 

# Compatible browsers
Currently only browsers that support the mp4 format, the format that KA Lite imports from Khan Academy, will work because the flash fallback is failing when using the file protocol in the browser (at least this is the case for Firefox on Mac and Android).  

# What works with which browsers

## Browsing the topic tree
Chrome on Mac (passes, as long as the topics.json file is so large that it exceeds localStorage limit)
Chrome on Android (N/A) -> Can't figure out how to open a file...
Android browser (passes, as long as the topics.json file is so large that it exceeds localStorage limit)
Firefox on Mac (passes, even with the entire topics.json)
Firefox on Android (passes, probably needs a smaller topics.json file depending on your hardware)

## Watching Videos
Chrome on Mac (passes, has support for mp4)
Chrome on Android (N/A) -> Can't figure out how to open a file...
Android browser (passes, has support for mp4)
Firefox on Mac (fails, no support for mp4 AND the flash fallback fails when used on file protocol)
Firefox on Android (fails, no support for mp4 AND the flash fallback fails when used on file protocol)

## Exercises
Chrome on Mac (fails, no support for XMLHTTPRequest when using file protocol)
Chrome on Android (N/A) -> Can't figure out how to open a file...
Android browser (fails, no support for XMLHTTPRequest when using file protocol)
Firefox on Mac (passes)
Firefox on Android (passes)

# Technical stuff
The start.html page loads topics.json into your browser.  When that finishes loading, you are prompted to go to topics.html where you can browse the "Source of all knowledge", the topic tree.  When you drill down far enough, the links lead to video.html which will load a video from your ka-lite's content directory and also form a link to HTML exercises in your ka-lite directory.  When you click on the exercise link, it brings you to that exercise's HTML page.

# Room for improvement
## Improve the basic UI
Right now there isn't a single line of CSS.

## Exercises dashboard
Only the topic tree for videos is exposed at the moment. That means you can only get to an exercise by going to its related video.

## Integrate the KA Lite video player and all its features
Most noteably, subtitles.  

## Cherry pick the topics.json file so only topics that have videos show up
This could work on two ends, when KA Lite does its import from the Internet it could generate a slim version of topics.json.  The other end is perhaps giving the user the option of only taking part of what is on the KA Lite installation. Loading a giant topics.json into a mobile browser is less than ideal.

## Turn topics.json into a JSON store so the browser doesn't have to load the entire topics.json file all at once.
You'd be surprised how even the most modern version on Chrome chokes on localStorage, albeit, due to defined quotas creates the dreaded QUOTA_EXCEEDED_ERR: DOM Exception 22.  Even KA Heavy has this issue (https://code.google.com/p/khanacademy/issues/detail?id=7936).  It's possible to write a script that breaks out topics.json (or any JSON for that matter) into a neat folder/text file structure so browsers only have to request the part of the JSON they need.  See  [my gist](https://gist.github.com/rjsteinert/5080816) for an idea of how to make a file based JSON store.

## Less javascript, more static html
Instead of loading topics.json into the browser and asking javascript to render topic and video pages, render topic and video pages as an html tree. Think like [Jekyll](https://github.com/mojombo/jekyll).

## Capture user activity data in the browser, prompt user to save it to the file system, have it picked up with a sync back to ka-lite or have user import manually
Mainly from a functional stand point, the difference of using Flying Owl as opposed to KA Lite is that that your activity data (mastery on topics, points, etc.) is not saved, nor can you see a the progress of other users for the sake of coaching. We could however build this out to prompt the user to import an activity data file (so they can see past progress) and also export an activity data file to save their progress.  Getting even crazier, contained in your own user file you could store references to other user files that would then allow your browser to build a coaching page for you to see others' activity data. 

## Incorporate other KA Lite goodies
:)

# Inspiration
> In character, in manner, in style, in all things, the supreme excellence is simplicity.

by Henry Wadsworth Longfellow (Thanks to Sal Khan for using this quote in his book One World Schoolhouse) 

> Put a bird on it.

by Kari Neumeyer and Fred Armisen of Portlandia


# Credits
Flying Owl coded from R.J. Steinert's hammock in Ghana.  R.J. Steinert is CTO of Open Learning Exchange and is a big fan of putting birds on things.

Thanks to the KA Lite and KA "heavy" team for making awesome sauce!

Thanks to Sal Khan for all of the awesome videos and inspiration. Your book rocks btw.

