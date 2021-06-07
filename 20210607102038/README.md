# Emailing me my public IP when it updates

I have been working with ssh for a long time. One of the issues i face is losing the link to the home machine when i have not been on for a while and the homes public IP address changes. To counter this rather than requesting a static IP address i built a script that will pull the current ip address from opendns using
`dig +short myip.opendns.com @resolver1.opendns.com`
Once this is pulled it is saved to a variable. This value is compared to a previous IP address stored in a mail.txt file. The text file is read into a variable using cat. To compare these to variables i use an if statement and a simple logical test with `!=`. If the ip address has changed i push the new ip address to the mail.txt file and then email this to me using curl. 

The command to send a message to someone with curl is incredible simple. However if you don't set it up correctly you are sending information such as your username and password over the internet. To counter this we are able to create a file called `.netrc`. In this file we place the location the email is being sent too. For example the gmail smtp server. Your username and Password. These are stored as follows.

`
machine smtp.gmail.com
user yourname
password MySeQRpAsswrd
`

Once done we can send a curl email with
`curl --ssl-reqd --netrc \
--url 'smtps://smtp.gmail.com:465' \
--mail-from 'myemail@gmail.com' \
--mail-rcpt 'myemail@gmail.com' \
--upload-file $HOME/Documents/mail.txt
`
This script is excellent as is. But to fully benefit from this i added the script to a cronjob with
`crontab -e`
` * * * * * /myprogram`
This runs the program every minute and if the IP has changed it will send an email to me telling me it has changed.

There is more i might do with this script or pipeline. Possibilities include adding an email scraper that automatically checks for a change in my home IP address and pushes it to my config file so i never have to worry about updating the config file and it will seemlessly ssh into the system from anywhere.

I also am not sure whether i need to run it every minute, as the script is quite small and only emails on a change i know it wont cause any issues so i am pretty happy with it at the moment.

