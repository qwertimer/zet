# Getting IRC running with weechat.

Weechat provides an excellent command line interface for numerous chat groups. Notably it provides an excellent setup for a chat client to interface to the twitch community. This is great to keep the chat going without the video stream. The following zet is basically a short installation guide for future me when i inevitably break something and need to format and reinstall the OS.

## Installation

To install weechat we can run the installation from the command line with 
`sudo apt install weechat`

Once installed we can begin to configure it. This is used to allow the authentication fo the servers that are used for the chats.

## Twitch integration

TO connect to the twitch server we run
`/server add twitch irc.chat.twitch.tv`
This will add the twitch server with a label such as twitch. Once this is done we need to add the oauth key to the server for authentication. To get an oauth key we can go to twitchapps.com/tmi. Once we have our oauth key we can add this to the server settings with
`/server add twitch irc.twitch.tv/6667 -password=oauth:*** -nicks=TWITCH_NAME -username=TWITCH_NAME`

## Connecting and Chatting
Once this is complete we are ready to start connecting to channels. The first step is to run
`/connect twitch`
Then we can join whichever channel we want with `/join #channel_name`

## Saving and closing

When you wish to close down weechat we are able to save settings with `/save` and exit channel with `/part #channel_name`/ Finally to close weechat we use `/quit`


There is a quick gist created by noromanba -- https://gist.github.com/noromanba/df3d975613713f60e6ae. Which contains these steps in a more compact design for ease of reference.

