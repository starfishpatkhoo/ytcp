# About YTCP

This is YTCP (YouTube Control Panel).

The purpose of this plugin is to allow you to load YouTube in one browser window (the Player) but control its playback/video/etc from a second browser window (the Controller). By doing this, the Player window can be displayed/screen captured more cleanly without mouse clicks and YouTube controls being shown, even when playing/changing different YouTube videos. In addition, the Player will play the video in full screen mode automatically, and not in a small window. Here are two simple use cases:

-   Dual-screen: Open the Player in one browser window on Screen 1, facing the audience, and then open the Controller on Screen 2 where the video can be easily controlled by the operator. This is also true for dual screens when you connect from a laptop to a projector. This is kind of like asking PowerPoint to show/control the slideshow on another monitor, but you know, with YouTube.

-   Embedded players: Some systems such as OBS have built-in browsers to display web pages. However it is usually distracting and difficult to control (especially video playback) in the browser being recorded/streamed. By having a dedicated control panel, we do not need to touch the output browser during the recording/streaming session.

# How To Use

### Step 1: Open the Player in a new Window/Tab/Streaming Source

_For a normal web browser:_

1. Open a new browser window and go to this URL: https://starfishpatkhoo.github.io/ytcp/player.html
1. Put this browser window on a different screen or monitor

The Player is optimised for 1920 x 1080 displays and if you can see the borders without any scroll bars, you're good. But even if you have a smaller display, it's fine because the Player will switch to full screen mode anyway.

_For OBS:_

1. Create a `New Source` » `Browser`
1. Call it `YTCP Player` (or whatever you like)
1. In the properties:

-   `URL`: https://starfishpatkhoo.github.io/ytcp/player.html
-   `Width`: 1920
-   `Height`: 1080
-   `Use Custom Frame Rate`: No
-   `Control Audio from OBS`: Yes
-   `Shutdown Source When Not Visible`: No
-   `Refresh Browser When Scene Becomes Active`: No

### Step 2: Choose Player options

1. _[OBS Only]_ Right click on the source you just created and select `Interact`.
1. Choose Player options:

-   `Captions`: Choose `None` for no captions, or one of the languages. If no such language/caption exists for that video, no captions will be shown.
-   `Annotations`: Check if Annotations should be displayed or not.

3. Click `Load Player`. The Player should load and switch to full screen. Leave it alone, do not click on it or press any keys etc. Just `ALT-TAB` away, move your mouse back to the main screen or close the OBS Interact window.

### Step 3: Open the Controller in a new Window/Tab/Dock Panel

_For a normal web browser:_

1. Open a new browser window and go to this URL: https://starfishpatkhoo.github.io/ytcp/controller.html
1. Leave this browser window on your main "control" screen

_For OBS:_

1. Go to `View` » `Docks` » `Custom Browser Docks`
1. In the list:

-   Dock Name: `YTCP Controller` (or whatever you like)
-   URL: https://starfishpatkhoo.github.io/ytcp/controller.html

3. Click `Close`. A new OBS Panel will appear and you can dock it somewhere if you like.

### Step 4: Key in one or more YouTube Video ID(s) in the Controller

Enter a single YouTube Video ID, or multiple IDs separated by commas. Here are some examples:

-   `dQw4w9WgXcQ`
-   `3IEp9Gj86Tc`
-   `0tCsJ-SgIEE, cVEWkQa1Mso`

### Step 5: Press Play in Controller

### Step 6: Monitor and Control playback in Controller

-   Restart current Video from the begining
-   Previous Video (Only works if more than one Video ID was specified)
-   Go back 10 seconds
-   Play / Pause
-   Go forward 10 seconds
-   Next Video (Only works if more than one Video ID was specified)
-   Mute / Unmute Video
-   Loop / Unloop Video when it ends
-   Jump to a specific point in the Video by keying in the time in minutes and seconds and pressing ENTER. For example, you can type `5:10` or `3.45` or `30` for 5 minutes 10 seconds, 3 minutes 45 seconds and 30 seconds respectively.
-   Size refers to playback quality size as reported by YouTube. Examples include `1080`, `720` or `Medium`.
-   Display timer shows elapsed time followed by total video length. If this is a live stream, then video length refers to the duration since the live stream started.
-   Progress bars display the current position of the video playback in orange, and the buffered position in light orange. When the video has played past key points (25%, 50%, 75%, etc), the percentage will be displayed inside the progress bar.
-   Toggling the debug will display debugging messages, especially for embeded browsers that do not have easy access to the console.

# Frequently Asked Questions

### Why can't XYZ video play?

Make sure the video allows embedded playback and you are allowed to view it. If it is a private video that you have access to, you will need to log into YouTube on your browser first.

### Can I reload/refresh the browser/source?

You can reload the Controller while a video is playing in the Player and it will pick up where it left off. But if you reload the Player (OBS Source), then you will need to click on Load Player in the Player and click on Play in the Controller again.

### Can I switch videos in the middle?

Yes. If a video is currently playing, just key in the new Video ID into the controller and press Play. The old video will stop and the new one will start playing right away.

### If I switch to a different scene in OBS, what happens to the video when I switch back?

If you had set Shutdown Source When Not Visible and Refresh Browser When Scene Becomes Active to No, then when you switch away, the YouTube video will continue to play in the background but no audio will be heard. If you set either one to Yes, then the Player will reload/refresh and you will have to click on Load Player in the Player and click on Play in the Controller again. If you want to pause the Video when you switch to a different scene, use the Controller to pause and resume before and after you switch scenes.

### What browsers are supported?

At the moment, Chrome, Edge and Firefox. Safari and IE are not, but if there is enough requests for it, I will add it.

### Can I open the Player and Controller on two different computers/devices, like my PC and my smartphone?

No, you cannot. This is because the communication system between the Player and the Controller only works if they are both on the same browser on the same machine. So opening the Player in Edge and the Controller in Chrome on the same computer is not going to work either.

### Can someone else control my Player?

No, they cannot. For the same reason why remote control from a different device won't work (as explained in the previous question), no one can control your Player instance with another browser window of the Controller. Unless of course, they've already hacked your computer.

### Does this slow down or affect my YouTube playback speed/quality?

No. Your video will play as well as and as fast as you normally would since it is still your browser that does the actual playing directly from YouTube.

### Can I force YouTube to play back the video at a certain quality level?

No. While YouTube's iFrame loading has workarounds that allow forcing the video quality levels, YouTube's embedded controller API does not and instead works very hard to auto-detect the "correct" quality level. This auto-detection is based on two major factors - screen size and bandwidth. We can't do much about the bandwidth part, but YTCP tries very hard to default to 1080 by maximising the size of the player from the outset. Unfortunately, the we can't use the iFrame method because it does not allow us to remote-control the YouTube player (meaning you would need to manually click Play inside the video and press F to go to full screen).

### Why is the text in the Player so big?

In embedded players such as OBS, the screen size in the preview/interact/source/monitor is small(er) than 1080, so making the fonts and buttons bigger will make it more visible and easy to click on.

### Are you tracking our Video IDs?

I do not track or record anything that this script does or is used for. If you want to be reassured, feel free to open the link to the Player and Controller and `View Source`.

### Is Google/YouTube/GitHub tracking our Video IDs?

No! Most definitely, absolutely, totally, 100% of course NOT! That's just, like, fake news, you know? Emperor Palpatine assured me and I believe him.

### Does playing videos through the YTCP count towards a Video's view count?

No, it doesn't. YouTube policy states that playback through embedded players do not count towards a video's view count.

### How can I get help with this thing?

If you find a bug, please file an issue at https://github.com/starfishpatkhoo/ytcp/issues or for general chit-chat, come on by to the YTCP Thread at OBS: https://obsproject.com/forum/resources/ytcp-youtube-control-panel.1098/

### Is this website/service free for me to use?

Yes. As long as hosting and bandwidth is free to me. But if you like YTCP or you find is useful and would like to show your appreciation, please support the Starfish at https://ko-fi.com/starfishpatkhoo

### Can I download this script and run it from my local computer?

Yes (mostly). In fact these two web pages are purposefully written as single self-contained pages with no external CSS/JS/images. So it is easy to just save it and open it in your browser locally. However, in some clients (such as the OBS built-in browser) and videos (such as `dQw4w9WgXcQ`) there are security restrictions imposed by the YouTube player that will prevent it from being loaded or the video from being played. From my investigations, the YouTube player will not load successfully from a local file when loaded in OBS (but works in Chrome desktop browser). Secondly, some vidoes are blocked from playing when the source of the embedding is not a domain. `C:\player.html`, http://127.0.0.1/player.html will not work. Only http://localhost/player.html will work. So, it's just easier to load the URL listed above. Besides, if you use this URL, you will always be using the updated version of this script.

<a href="https://ko-fi.com/starfishpatkhoo" title="Support Starfish at Ko-Fi"><img src="https://starfishpatkhoo.github.io/ytcp/ko-fi-starfish.svg" width="250px"></a>
