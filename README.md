Please note that this documentation is not complete, we are working on finishing it.

# Building a toolchain for anything OpenEmbedded supports

When you have installed bitbake and openembedded you can build the package
meta-toolchain to get a toolchain for that architecture.

# Building Erlang

Make sure to have a valid toolchain in your `$PATH`, in the `EmbErl.sh` script there
is a variable named `$HOST`. The toolchain should have its binaries named
`${HOST}-command`. Example for `HOST=arm`: gcc should be `arm-gcc` and be available
in your `$PATH`.

We have used the toolchain that is built by openembedded when building our things.

    ./EmbErl.sh -<opts>

    Available opts are:
    -s          Strip beam files and compile with the slim flag
    -S          Stip binaries with the strip-tool
    -c          Compile beams using the compress flag
    -C          Compress applications into zip's
    -o <arg>    Compile the virtual machine with the <arg> optimization flag
    -H <arg>    Compile the virtual machine for the host <arg>
    -h          Display help message 

To use another Erlang version than the one that `EmbErl.sh` uses as
default, change the `VERSION` variable (eg `VERSION=R14B01 ./EmbErl.sh
<arguments>`). One can also set the variable `TARGET_ERL_ROOT=path` to
change the location in which Erlang will be installed.


# Generate package

Please note that generating a package is intedend to be used to create a
installation package as the ones we release on embedded-erlang.com. There is no
reason to do this step if you just want erlang to be built for a different
architecture.

Use the `CreatePackage.sh` script in order to create a package. If you
did specify `TARGET_ERL_ROOT` in the build step you should do it for
the package generation as well (eg `TARGET_ERL_ROOT=path ; ./CreatePackage.sh`)
