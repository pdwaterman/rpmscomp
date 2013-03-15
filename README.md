rpmscomp
========

NAME
====
rpmscomp - compare RPMs installed on multiple systems, or compare versus previously recorded list of installed packages

SYNOPSIS
========

    rpmscomp [OPTION]... [[USER]@HOST]... [FILE]...
    rpmscomp --record [OPTION]... [[USER]@HOST]...


DESCRIPTION
===========
Compare the RPMs installed on the specified systems and/or recorded within the
specified files.

General Options
---------------

<table>
<tr><td nowrap>-d, --diffonly</td><td>Only list differences</td><tr>
<tr><td nowrap>-h, --help</td><td> Print a help message and exit</td><tr>
<tr><td nowrap>-r, --record</td><td>Record mode (record installed RPMs for later)</td><tr>
<tr><td nowrap>-v, --verbose</td><td>Verbose mode</td><tr>
</table>

Record Mode Options
-------------------

<table>
<tr><td nowrap>-f, --force</td><td>Force overwrite of output files</td><tr>
<tr><td nowrap>-o, --output</td><td>Write a list of installed RPMs to this file name. If multiple HOSTs are specified, this specifies a prefix, and the host name will be appended.</td><tr>
</table>

Specifying Hosts and Files
--------------------------
If you specify a host as @HOST, rpmscomp will ssh to HOST in order to determine what RPMs are installed on that host.

If you specify a host as USER@HOST, rpmscomp will ssh to HOST as USER in order to determine what RPMs are installed on that host.

If you provide an argument that doesn't begin with @, rpmscomp will assume this is a file name containing a previously recorded list of RPMs installed on some host.

If you specify no hosts in --record mode, rpmscomp will assume you want to record the RPMs installed on @localhost.

if you specify only a single host in normal (compare) mode, rpmscomp will assume you want to compare versus @localhost.

You can specify as many hosts and/or files as you want to compare (there is no hard limit other than what may be imposed by the amount of memory in your systems).

EXAMPLES
========

    rpmscomp @server1

This will ssh to server1, retrieve a list of all the RPMs installed on that host, then print out a comparison of the RPMs installed on server1 versus the local host.

    rpmscomp @server1 @server2

This will ssh to server1 and server2, retrieve a list of all the RPMs installed on each host, then print out a comparison of the RPMs installed on both hosts.

    rpmscomp --diffonly @server1 @server2

This will ssh to server1 and server2, retrieve a list of all the RPMs installed on each host, then print out a comparison of the RPMs installed on both hosts, but only
showing RPMs where the installed version, release, or architecture(s) differ between the hosts.

    rpmscomp user1@server1 user2@server2

This will ssh to server1 as user1, ssh to server2 as user2, retrieve a list of all the RPMs installed on each host, then print out a comparison of the RPMs installed on both hosts.

    rpmscomp @server1 @server2 @server3 @server4 @server5 @server6

This will ssh to server1 through server6, retrieve a list of all the RPMs installed on each host, then print out a comparison of the RPMs installed on both hosts.

    rpmscomp --record @server1 @server2

This will ssh to server1 and server2, retrieve a list of all the RPMs installed on each host, and record that information in files (server1 for the server1 list and
server2 for the server2 list). If the file that would be written to already exists, that host will be skipped.

    rpmscomp --record --force @server1 @server2

This will ssh to server1 and server2, retrieve a list of all the RPMs installed on each host, and record that information in files (server1 for the server1 list and
server2 for the server2 list). If the file that would be written to already exists, it will be overwritten.

    rpmscomp --record --output myprefix @server1 @server2

This will ssh to server1 and server2, retrieve a list of all the RPMs installed on each host, and record that information in files (myprefix.server1 for the server1 list and
server2 for the myprefix.server2 list). If the file that would be written to already exists, that host will be skipped.
.
    rpmscomp myprefix.server2 @server2
    
This will retrieve a previously stored list of RPMs installed from myprefix.server2, then ssh to server2, retrieve a list of all the RPMs installed on that host, then
print out a comparison of the RPMs lisetd in myprefix.server2 versus those currently installed on server2.


COPYRIGHT AND LICENSE
=====================
Copyright (C) 2013, Paul Waterman

This program is free software: you can redistribute it and/or modify it
under the terms of the GNU General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option)
any later version.

This program is distributed in the hope that it will be useful, but WITHOUT
ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for
more details.

You should have received a copy of the GNU General Public License along with
this program.  If not, see <http://www.gnu.org/licenses/>.
