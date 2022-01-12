# Cleaning up docker images with awk and xargs

I had a huge amount of docker images that had been accumulating during development. I decided to clean them up using a linux pipeline

`docker image ls | head -n 28 | awk '{ print 3 }' | xargs -l docker image rm -f `

This zet is basically a reminder that for many things a linux pipeline is the simplest solution. I basically searched all my docker images, got the top x number of images. In this case 28, for the iterations i went through in development. Sent this to awk to get the third row and sent the result of this to xargs, there is a little hiccup in this code as it tried to remove the images with the labels of the columns. But apart from that it worked well.


    #pipelines #docker


