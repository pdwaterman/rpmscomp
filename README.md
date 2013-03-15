rpmscomp
========

NAME
----
rpmscomp - compare RPMs installed on multiple systems, or compare versus previously recorded list of installed packages

SYNOPSIS
--------
rpmscomp [OPTION]... [[USER]@HOST]... [FILE]...
rpmscomp --record [OPTION] [[USER]@HOST]...

DESCRIPTION
-----------
Compare the RPMs installed on the specified systems and/or recorded within the
specified files.

  -h, --help         Print this help message and exit

  -d, --diffonly     Only list differences
  -r, --record       Record mode (record installed RPMs for later)
  -v, --verbose      Verbose mode

Record mode options:

  -f, --force        Force overwrite of output files
  -o, --output       Write a list of installed RPMs to this file name. If
                     multiple HOSTs are specified, this specifies a prefix,
                     and the host name will be appended.

If one or more [USER]@HOSTs are specified, rpmcomp will ssh to each of those
hosts in order to determine what RPMs are installed on that system.

If one of more FILEs are specified, rpmcomp will read a list of installed RPMs
from those files as previously recorded by rpmcomp.

If only one [USER]@HOST or FILE is specified and record mode is not specified,
the RPMs installed on HOST will be compared with the RPMs installed on the
local host.
