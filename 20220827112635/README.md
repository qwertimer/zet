# Simple quick way to remove .env from git history

The other night i did it. I accidently pushed an env file to github and
i was trying to figure out the best way to remove the file without
leaving anything in the commit history. I finally found this simple
solution. 
`git filter-branch --index-filter "git rm -rf --cached --ignore-unmatch
.env" HEAD`

