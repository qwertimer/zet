# Bash one liner to search zet titles and send to a selector.

This bash one liner will search through the zet titles and open the folder to that directory. This one liner will be put in a command that allows me to search my zet folder for a specific topic and open that folder. I can also extend it to automatically open a vim instance. Will need to automate the uploading to github as the commit message should be reset to the title.

`IFS=$'\n'; select title in `zet titles`; do cd $KN/zet/${title%% *}; break; done`
