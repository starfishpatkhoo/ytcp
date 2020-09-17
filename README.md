# About YTCP

This is the YTCP (YouTube Control Panel).

In short, it allows you to load YouTube in one browser window (the Player) and then control its playback/video/etc from a second browser window (the Controller). In addition, the Player will play the video in full screen mode automatically, and not in a small window. Here are two simple use cases:

-   Dual-screen: Open the Player in one browser window on Screen 1, facing the audience, and then open the Controller on Screen 2 where the video can be easily controlled by the operator. This is also true for dual screens when you connect from a laptop to a projector. This is kind of like asking PowerPoint to show the slideshow on another monitor, but you know, with YouTube.

-   Embedded players: Some systems such as OBS have built-in browsers to display web pages. However it is usually distracting and difficult to control (especially video playback) in the browser being recorded/streamed. By having a dedicated control panel, we do not need to touch the output browser during the recording/streaming session.

# How To Use

### Step 1: Open the Player in a new Window/Tab/Streaming Source

For a **normal web browser**:

1. Open a new browser window and go to this URL: https://starfishpatkhoo.github.io/ytcp/player.html
1. Put this browser window on a different screen or monitor

The Player window is optimised for 1920 x 1080 displays. If you can see the borders without any scroll bars, you're good.

For an **OBS Source**:

1. Create a new source » `Browser`
1. Call it `YTCP Player` (or whatever you like)
1. In the properties:

-   URL: https://starfishpatkhoo.github.io/ytcp/player.html
-   Width: `1920`
-   Height: `1080`
-   Use Custom Frame Rate: `No`
-   Control Audio from OBS: `Yes`
-   Shutdown Source When Not Visible: `No`
-   Refresh Browser When Scene Becomes Active: `No`

### Step 2: Choose Player options

1. In OBS, right click on the source you just created and select `Interact`.
1. Choose Player options:

-   Captions: Choose None for no captions, or one of the languages. If no such language/caption exists for that video, no captions will be shown.
-   Annotations: Check if Annotations should be displayed or not.

3. Click `Load Player`

### Step 3: Open the Controller in a new Window/Tab/Dock Panel

For a **normal web browser**:

1. Open a new browser window and go to this URL: https://starfishpatkhoo.github.io/ytcp/controller.html
1. Leave this browser window on your main "control" screen

For **OBS**:

1. Go to `View` » `Docks` » `Custom Browser Docks`
1. In the list:

-   Dock Name: `YouTube Control Panel` (or whatever you like)
-   URL: https://starfishpatkhoo.github.io/ytcp/controller.html

3. Click Close

A new OBS Panel will appear and you can dock it somewhere if you like.

### Step 4: Key in one or more YouTube Video ID(s) in the Controller

Enter a single YouTube Video ID, or multiple IDs separated by commas. Here are some examples:

-   `dQw4w9WgXcQ`
-   `3IEp9Gj86Tc`
-   `0tCsJ-SgIEE, 3IEp9Gj86Tc`

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
-   Jump to specified point in Video by keying in the time in minutes and seconds and pressing ENTER. For example, you can type `5:10` or `3.45` or `30` for 5 minutes 10 seconds, 3 minutes 45 seconds and 30 seconds respectively.
-   Size refers to playback quality size as reported by YouTube. Examples include `1080` or `720`.
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

If you had set Shutdown Source When Not Visible and Refresh Browser When Scene Becomes Active to No, then when you switch away, the YouTube video will pause and no audio will be heard. When you switch back, the video will continue playing where you left off. If you set either one to Yes, then the Player will reload/refresh and you will have to click on Load Player in the Player and click on Play in the Controller again.

### Can I open the Player and Controller on two different computers/devices, like my PC and my smartphone?

No, you cannot. This is because the communication system between the Player and the Controller only works if they are both on the same browser on the same machine. So opening the Player in Edge and the Controller in Chrome on the same computer is not going to work either.

### Can someone else control my Player?

No, they cannot. For the same reason why remote control from a different device won't work (as explained in the previous question), no one can control your Player instance with another browser window of the Controller. Unless of course, they've already hacked your computer.

### Does this slow down or affect my YouTube playback speed/quality?

No. Your video will play as well as and as fast as you normally would since it is still your browser that does the actual playing from YouTube.

### Why is the text in the Player so big?

In embedded players such as OBS, the screen size in the preview/interact/source/monitor is small(er) than 1080, so making the fonts and buttons bigger will make it more visible and easy to click on.

### Are you tracking our Video IDs?

I do not track or record anything that is generated by this script. If you want to be reassured, feel free to open the link to the Player and Controller and "View Source".

### Is Google/YouTube tracking our Video IDs?

Most definitely, absolutely, totally, 100% of course not! That's just, like, fake news, you know? Emperor Palpatine told me and I believe him.

### Is this website/service free for me to use?

Yes. As long as hosting and bandwidth is free to me.

### Does playing videos through the YTCP count towards a video's view count?

No, it doesn't. YouTube policy states that playback through embedded players do not count towards a video's view count.

### Can I download this script and run it from my local computer?

Yes (mostly). In fact these two web pages are purposefully written as single self-contained pages with no external CSS/JS/images. So it is easy to just save it and open it in your browser locally. However, in many clients (such as the OBS built-in browser) and videos (such as dQw4w9WgXcQ) there are security restrictions imposed by the YouTube player that will prevent it from being loaded or the video from being played. From my investigations, the YouTube player will not load successfully from a local file when loaded in OBS (but works in Chrome desktop browser). Secondly, some vidoes are blocked from playing when the source of the embedding is not a domain. C:\player.html, http://127.0.0.1/player.html will not work. Only http://localhost/player.html will work. So, it's just easier to load the URL listed above. Besides, if you use this URL, you will always be using the updated version of this script.
