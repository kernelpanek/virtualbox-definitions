virtualbox-definitions
======================

Box Development with Veewee
===========================

The repository contains Veewee definition files for virtual machine creation. Once the Veewee gem is installed, a new subcommand, `basebox`, should be available under `vagrant`:

```
Usage: vagrant [-v] [-h] command [<args>]

    -v, --version                    Print the version and exit.
    -h, --help                       Print this help.

Available subcommands:
     *basebox*
     box
     destroy
     gem
     halt
     init
     package
     provision
     reload
     resume
     ssh
     ssh-config
     status
     suspend
     up
```

To build new virtual machines, start with one of the many [templates](https://github.com/jedi4ever/veewee/tree/master/templates)
`vagrant basebox define 'ubuntu-12.04.4-server-amd64' 'my-ubuntu-12.04.4-server-amd64'`

This will add a new directory under `definitions/` with the beginning of your new virtual machine template.  Modify the definition.rb, postinstall.sh, preseed.cfg files as necessary. Then run:

`vagrant basebox build 'my-ubuntu-12.04.4-server-amd64'`

After your virtual image builds, you can validate your vm with:

`vagrant basebox validate 'my-ubuntu-12.04.4-server-amd64'`

Once all validations pass, you can export your vm and build the .box file with:

`vagrant basebox export 'my-ubuntu-12.04.4-server-amd64'`

Once the box is ready, publish it to an S3 bucket or other online file storage service.
