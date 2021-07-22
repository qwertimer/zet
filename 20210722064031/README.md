# Need to learn more about find

I had a pile of zet folders with .index in them when i tried to integrate zets to nb. When i gave up on that i realised all of these had a .index file but i didnt want all these so i decided to use find to remove them.
Using the below command i found all files in the directory with .index and piped to rm using xargs.

`find . -name '.index' | xargs rm`

However a twitch chat guy suggested doing it all with find as there is a delete flag in find. The below command is :
`find -type f -name '.index' -print -delete`

This is a fast and simple way to remove all the files.


