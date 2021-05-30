# Setting up multiple zets

When i am looking to setup new zet repositories i have a couple of things that need doing. For now they are manual but could possibly be automated. 

The first is to create the folder in `~/.local/share/<folder>`. Once the folder is created i link it to my repositories folder to make it easier to find all my stuff. This folder is stored at `~/repos/github.com/qwertimer`. To link the new zets i run `ln -s ~/.local/share/<folder> ~/repos/github.com/qwertimer/`. This adds the link to my main repos location.

From here i cd into the new zet folder run `git init` and set the origin with `git add origin https://www.github.com/qwertimer/<folder>.git` if i haven't set up a repo i am able to do it from the command line using `gh` with this i can run `gh repo create`. Once completed i need to symlink the zet program to my new zet repository. This is done by moving into my scripts folder which is stored in my `.dotfiles` folder. By symlinking to a new name i am able to run that command and open the zet for that folder. For example linking zet to todo, when i run todo in the command line i begin writing a zet for that repo.

This configuration makes it very easy to setup new zets and start storing everything on github. 
