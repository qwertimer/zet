# Some useful makefile configurations

Using a cookiecutter go config today i found an excellent makefile with
some useful configurations. The most useful of these is configuring the
makefile to have a help setup. This is done with two commands. The first
means the help is the default call when make is run without any
subcommand. The command is 
```
.DEFAULT_GOAL := help
```

The second is to actually display help by outputting the results of each
commands comment string. A useful config is to have double # to
distinguish from normal comments and use the below setup
```
.PHONY: help
## `help`: Generates this help dialog for the Makefile
help: Makefile
  echo
  echo " Commands available in \`"$(PROJECTNAME)"\`:"
  echo
  sed -n 's/^[ \t]*##//p' $< | column -t -s ':' |  sed -e 's/^//'
  echo
```

The other two cool configurations are for undertaking linting which can
be done with 

```
.PHONY: codestyle
## :
## `codestyle`: Run code formatter(s)
codestyle:
  golangci-lint run --fix


.PHONY: lint
## `lint`: Run linters and check code-style
lint:
  golangci-lint run
```


