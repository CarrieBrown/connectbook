[title]: - "Compiling Applications for OSG Connect"

# Compiling Applications for OSG Connect
## Introduction
If you are using software that is primarily distributed as source code
or if you need to compile your software, this page provides some tips and
guidelines for doing so.

## Building statically linked applications

When an application is statically compiled, the majority  of the libraries that 
the application uses is compiled and packaged with the application binaries.
This signficantly reduces the things that the application depends on, allowing
the application to run on a much larger proportion of systems.

You can compile code using gcc using the `-static` flag when compiling.  If you
are building an application that uses `configure`, then using the
`--enable-static` option should create a statically linked application.
Otherwise, setting `LD_FLAGS` in the environment to `--enable-static` 
(e.g. `export LD_FLAGS="--enable-static"`) make generate statically linked
binaries.

## Building dyanmically linked applications

GCC and ld dynamically link applications by default so you probably will not need
to do anything special to create a dynamically linked application.  However, you
should read the following sections in order to generate binaries that will function 
correctly.

## Compilation Server

Regardless of whether you statically or dynamically compile your application,
you should compile your application on your assigned login node.  This will ensure
that your application is built on an environment that is similar to the majority
of the compute nodes on OSG.  In addition, you will need to add the following
require to your HTCondor submit file: `(OpSysAndVer =?= "SL7") || (OpSysAndVer
=?= "RHEL7") || (OpSysAndVer =?= "Centos6")` to make sure that your binaries run 
systems that have compatible linux distributions.

## Libraries

The distributed environment modules system provides several commonly used
scientific libraries (lapack, atlas, hdf5, netcdf, etc.) that your application
may need to link to.  In order to link against a library provided by the
module system, just load the appropriate module (e.g. `hdf5/1.8.12`).  Doing so
will set the `CPATH` and `LIBRARY_PATH` so that gcc will be able to find the
includes and link files for that library.  If your build system does not pick up
the appropriate you can look at the `CPATH` and `LIBRARY_PATH` variables to find
the paths used and incorporate that into your build process or you can contact
user support for assistance.

Finally, if you do use modules from the modules system, you will need to modify
your job scripts to load the appropriate modules before running you application.

## Assistance
If you have questions or need assistance, please contact <support@osgconnect.net>.

