# Configuring zet for my systems

Working through robs initial zet program i modified the kn to zetdir. This zetdir points to a `$HOME/.local/share\zet` location. I have not got any configuration set but it is possible in the `.config/zet/config.yml`. Once i had the zet program configured i added the folder location to path. I also needed to add isosec to the path however in the future i will bring that into the zet program. The next thing i did was add a symlink to `$HOME/repos/github.com/qwertimer/zet` to point to the zet location. `ln -s ~/.local/share/zet ~/repos/github.com/qwertimer/`

Finally with the configuration out of the way i initialised a repo in the zet folder. I used gh to create the github repo and i then ran an initial push. This setup is now configured for me to write zets when needed.

