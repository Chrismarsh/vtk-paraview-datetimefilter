# vtk-paraview-datetimefilter
Paraview filter to show date-time information for a timeseries of vtu data.

XML plugin
===========

With the API changes in Paraview 5.7+, this no longer compiles for Paraview >= 5.7. I'm am transitioning to a Python-based version. In the mean time, I've modified the built in XML+Python NetCDF time file to work with the below-described pvd file format.

This plugin is `AnnotateDateTime.xml` and can be added loaded as plugi. Just load the xml file directly. This works with the pre-built Paraview binaries available from Paraview.org. 


C++ plugin
==========
This is based off code from John Biddiscombe [1], as well as the Time Annotate filter that ships with Paraview.

I have modified this code to:
- compile with the newest (4.4.x) of Paraview
- support POSIX time via boost::ptime
- support output format as YYYY/MM/DD HH:MM:SS

To build this example, you need to follow the guide for building Paraview from source [2] and to install plugins [3]. On MacOS you may need to follow [4] to help cmake find qt5.

After you compile Paraview, you need to set ParaView_DIR in CMakeLists.txt to the root directory.

The last piece of the puzzle is that output meshes have to be wrapped in a pvd file with the timestamp=".." attribute set to a POSIX time. 

![](output.gif)

[1] https://hpcforge.org/plugins/scmgit/cgi-bin/gitweb.cgi?p=pv-echam/pv-echam.git;a=tree;h=5f8410b1879178a4a114a279b8bd9463825e507d;hb=5f8410b1879178a4a114a279b8bd9463825e507d

[2] http://www.paraview.org/Wiki/ParaView#Compile.2FInstall

[3] http://www.paraview.org/Wiki/ParaView/Plugin_HowTo#Using_Plugins

[4] https://github.com/Cockatrice/Cockatrice/issues/205#issuecomment-183087315