# The `ingest` command explained

The `build` command is in fact a "shortcut" that actually runs a number of commands, which can also be run individually, in the correct order:

1. buildgroups
2. buildusers
3. buildglossary
4. buildinstalls
5. buildinsights
6. buildworkshop
7. buildblurbs

All of these can be placed in place of `build` on the command line above, like so:

```sh
$ python manage.py buildgroups
$ python manage.py users
$ python manage.py ...
```