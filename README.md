# LockScreen
AppleScript for automator for the use of the Application Template and once compiled installed in Applications folder.

# Apple Script Introduction

* To be called by HotKey: https://apps.apple.com/us/story/id1509582362
* But something that was invaluable because I didn’t know how to use Automator was the line on Post 1 that stated: Type “Run AppleScript” as shown in below Image and Double click to open.
* Because in setting up Automator to do it’s thing. I had no idea that I would need an AppleScript action to add the script instruction.  So I added a Run Apple Script action. 
* I also would not have known to make sure to continue the set up by: Check the checkbox with title “Service receives no input in any application“.
* Those two things that were key to the set up of being able to create my AppleScript App on Automator would not have been possible with out those instruction although the article was fundamentally stale. 
* The lesson relearned was don’t dismiss old doc because thing don’t fit any more in many parts of the doc.  Because the old doc might give you the insight you need to build your own new doc. 
* Needless to say this tool is not intuitive to me. 
* I ran the script in script in the old doc anyway, I’ve been trained to watch it break first. (Fail early fail often.)
tell application “System Events” to tell process “SystemUIServer”
    tell (menu bar item 1 of menu bar 1 where description is “Keychain menu extra”)
        click
        click menu item “Lock Screen” of menu 1
    end tell
end tell
And save with name of your choice “Lock Screen”
Click on the lock icon on Menu Bar and Mac Os Screen will be locked

* If you haven't seen AppleScript before as you can see it’s super chatty.  You can use JavaScript but there was an additional hurdle that I didn’t want to add to the process of getting there. 
* So more searching got me to Post 2
* As you can see the user on Post 2 had gotten to Post 1 also.  Had a set up but no working script. 
* The a person giving support does something wonderful, they complete my mental model by talking about the sys obj that you have to talk to to get the task done and in one line of code they solved it.  Later they gave another implantation two but I love one liners, so I went we that. 
* The line of code was:
tell application "System Events" to keystroke "q" using {control down, command down}
* To me the tone was humble and kind, but I didn’t read much past that so I don’t know if there was anything not worth after that one line of code. 
* Have my Automator set up by Post 1 and looking at note the Automator leaves for you when you do an AppleScript app:  (* Your script goes here *) 
* I did just that I placed the line of code right there. 
* The apple script action when double clicked as requested above looks like this:
on run {input, parameters}
 	(* Your script goes here *)
 	return input
end run
* When I was done it looked like this: 
on run {input, parameters}
 	tell application "System Events" to keystroke "q" using {control down, command down}
 	return input
end run
* The Automator program indicates to the user that the script successfully compile by changing the color of the text to this:
on run {input, parameters}
 	tell application "System Events" to keystroke "q" using {control down, command down}
 	return input
end run
* If you run the script once it actually compiles the script with it’s appropriate “app” wrapper a combination of a Apple DSL implemented in XML and some binary elements.  
* I loved this script because of how little code it was the only better solution would have been no code at all. 
* There was a point where It was not clear at all what the default location where the app was saved to.  
Post 3 helped find that:
https://apple.stackexchange.com/questions/14030/location-of-services-created-in-automator
* It turns out that the default location that Automator saves to on the file system was ~/Library/Services
* I had to do some checking in my file system because a you can tell in Post 3 there was some ambiguity.
* In the process of looking I stumbled upon a video from a podcast I recommend:
Post 4:
https://macmost.com/an-introduction-to-using-mac-automator.html
* Again all in the process of looking for the default location Automator saves to.  
* By the way, I was looking because the first 2 assemblies I created I just hit save and assumed it would be saved to something like Documents/Automator since on the UI and in the docs it refers to the elements of the assembly as docs what better place to save to than Documents for something you are calling docs.
* But no it was ~/Library/Services. 
* I’m sure that is legacy nomenclature that referred to the assemblies as Services but the word Services got so overloaded with different meaning that they abandoned the use of it except in the file system. 
* I have to say that I feel that that Garry @MacMost is a powerfully thoughtful podcaster for the following reasons:
    * His video are focused on one topic and one topic only. 
    * They tend to run between 5 and 12 minutes. (Which is perfect to get an answer.)
    * Ok, here is what I love the most.  They deal with the mundane + critical.  It’s the thing that you need to know but were afraid to try to find out for yourself because you might fall asleep. Yet are super critical.
    * Case in point: when I watched his video he validated the things I knew and taught me details I didn’t in a very short amount of time.  Key thing was that I could save the assemblies I was making to a more recognizable folder.
* Once my tiny assembly was ready I did what I’ve wanted to do for a very long time. I dropped it in the Application folder.  
* Once it was there I proceeded to test it and came across 3 dialog boxes that all dealt with permissions.
* I went to give it permissions and all of the sudden before I could get there it gave me a dialog asking me if I wanted to give it permissions and I said yes and went in and did it and it is running just fine. 
* Along the way I found Automators User’s Guide:
https://support.apple.com/guide/automator/welcome/mac
* It’s something that I will be looking to automate the mundane in my life. 
* I have NOT found this yet but I will be looking for the docs that present the object model in JavaScript for both Script Editor and Automator. What I looking for would be the counter part of what JavaDoc or ScalaDoc or the Pyton Docs but for the resources available to call with JavaScript so I can automate much more. 
* Checked in you will find a .as file with the code that can be pasted into your Automator UI of course:
* ...THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND… 
          **As you will see in the licensing section.**