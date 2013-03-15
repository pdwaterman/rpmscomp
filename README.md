rpmscomp
========

NAME
====
rpmscomp - compare RPMs installed on multiple systems, or compare versus previously recorded list of installed packages

SYNOPSIS
========

rpmscomp [OPTION]... [[USER]@HOST]... [FILE]...

rpmscomp --record [OPTION] [[USER]@HOST]...


DESCRIPTION
===========
Compare the RPMs installed on the specified systems and/or recorded within the
specified files.

General Options
---------------

<table>
<tr><td>-d, --diffonly</td><td>Only list differences</td><tr>
<tr><td>-h, --help</td><td> Print a help message and exit</td><tr>
<tr><td>-r, --record</td><td>Record mode (record installed RPMs for later)</td><tr>
<tr><td>-v, --verbose</td><td>Verbose mode</td><tr>
</table>

Record Mode Options
-------------------

<table>
<tr><td>-f, --force</td><td>Force overwrite of output files</td><tr>
<tr><td>-o, --output</td><td>Write a list of installed RPMs to this file name. If multiple HOSTs are specified, this specifies a prefix, and the host name will be appended.</td><tr>
</table>

SPECIFYING HOSTS
================

If one or more [USER]@HOSTs are specified, rpmcomp will ssh to each of those
hosts in order to determine what RPMs are installed on that system.

If one of more FILEs are specified, rpmcomp will read a list of installed RPMs
from those files as previously recorded by rpmcomp.

If only one [USER]@HOST or FILE is specified and record mode is not specified,
the RPMs installed on HOST will be compared with the RPMs installed on the
local host.
