# Dynaconf is an awesome configuration manager for python

I just found today dynaconf. It has a cli tool to initialise a
configuration file with `dynaconf init -f toml` initialising a toml
based config file. When the tool initialises all you need to do is
import settings from config and you have access to all your
configurations in your application. The great thing about this design is
you don't need to pass around your configs into each function.

