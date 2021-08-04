# Rather than using true and false in bash use is empty

Watching through robs scripting of dns resolv swap. It was mentioned
that it is better in bash and sh to use is empty and contains stuff to
show true and false. This can be done with the `-n` flag, for example:

``
var="y"
[[ -n $var ]] && echo "Contains text"
var=""
[[ -n $var ]] && echo "empty"
``
Will print Contains text after the first var is initialised.
Once var is changed the statement is false and empty wont be shown.



