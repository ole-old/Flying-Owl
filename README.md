Make your KA Lite installation lighter, put a bird on it.

# About
When placed in your KA Lite's installation directory, open start.html for serverless browsing of your KA Lite's videos and exercises. 


# Installation and dependencies
Place this directory in your KA Lite directory, convert all of the .MP4 files in your content directory to .webmsd.webm, and open in the start.html file in javascript.  The file format dependency and the browser dependency can be fixed with a little elbow grease, keep in mind this is a proof of concept.

# Technical stuff
The start.html page loads topics.json into your browser.  When that finishes loading, you are prompted to go to topics.html where you can browse the "Source of all knowledge", the topic tree.  When you drill down far enough, the links lead to video.html which will load a video from your ka-lite's content directory and also form a link to HTML exercises in your ka-lite directory.  When you click on the exercise link, it brings you to that exercise's HTML page.

# Room for improvement
## Improve the UI
Right now just the basics are there.

## Integrate the KA Lite video player and all its features
Most noteably, subtitles.  

## Cherry pick the topics.json file so only topics that have videos show up
This could work on two ends, when KA Lite does its import from the Internet it could generate a slim version of topics.json.  The other end is perhaps giving the user the option of only taking part of what is on the KA Lite installation. Loading a giant topics.json into a mobile browser is less than ideal.

## Don't use localStorage for maintaining session data. More browsers will be supported this way.
You'd be surprised how even the most modern version on Chrome chokes on localStorage.

## Less javascript, more static html
Instead of loading topics.json into the browser and asking javascript to render topic and video pages, render topic and video pages as an html tree. Think like Jekyll (https://github.com/mojombo/jekyll).

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

