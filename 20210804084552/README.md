# Modifying robs latest zet for my pipeline.

Robs zet is becoming really impressive. Some functionality i don't need
but i did have some issues moving his code to my base. The first issue
was that i didnt have `/usr/bin/bash` This was simple to fix. The second
more subtle issue was the default path for zet. For some reason my zet
doesn't need /zet at the end of `zetdir`.  The next issue i noticed was
that rob has hardcoded `main` into the web access scripts. Instead i
updated the script to use the `GITBRANCH` env variable.

For reference the git commit is https://github.com/rwxrob/dot/commit/9ab62255d7d95eb72f01bf0d3f4d03f5453d8143
