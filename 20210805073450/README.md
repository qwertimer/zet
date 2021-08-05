# Issues with setting up different ssh keys. 

I was trying to set up an ssh connection to my newly formatted surface
pro from my main workstation. Every time i tried to connect the system
would send an authentication error message, too many login attempts or
similar messages. This is issue as it turns out was caused by me having
too many different ssh keys on my main machine. I was using multiple
different keys for different interactions with some services. However
following this i think i may remove the other ssh keys and just have
one. You are able to get around this issue in a couple of ways as seen
on
(https://superuser.com/questions/187779/too-many-authentication-failures-for-username).

You can set up in your ssh/config file two lines the first being the
Identity file you are giving and a flag saying send only this key.

Eg:
```
  Host www.myawesomesite.com
    IdentityFile ~/.ssh/id_key
    IdentitiesOnly yes
    Port xx

```

If you don't use this method you are able to use flags in the ssh call.
We can use `-i` to indicate the identity file and `-o
IdentitiesOnly=yes`

This will stop the issue from occurring. If you wish to see when this
actually happens you are able to use `-v` for verbose mode.




