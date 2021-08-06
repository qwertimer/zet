# tmux windows basics

To create a new window in tmux we use `Prefix c`, windows will be added
where aothers have been removed. We can move between windows using
`Prefix p` and `Prefix n` to move back and forward, we can use numbering
instead and if the numbering is above 10 we can use `Prefix '` to prompt
for the window.

If we wish to change the window layouts we use `Prefix space` which will
change the layouts through the presets. We can set layouts in the config
with commands such as `bind m set-window-option main-pane-height 60;
select-layout main-horizontal`.

