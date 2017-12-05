# vtk-paraview-datetimefilter
Paraview filter to show date-time information for a timeseries of vtu data.

This is based off code from John Biddiscombe [1], as well as the Time Annotate filter that ships with Paraview.

I have modified this code to:
- compile with the newest (4.4.x) of Paraview
- support POSIX time via boost::ptime
- support output format as YYYY/MM/DD HH:MM:SS

To build this example, you need to follow the guide for building Paraview from source [2] and to install plugins [3]. On MacOS you may need to follow [4] to help cmake find qt5.

After you compile Paraview, you need to move the ParaViewConfig.cmake file from the root of the build directory to the CMake folder. I have included the one that generated from my install as an example.

The last piece of the puzzle is that output meshes have to be wrapped in a pvd file with the timestamp=".." attribute set to a POSIX time. 

![](output.gif)

[1] https://hpcforge.org/plugins/scmgit/cgi-bin/gitweb.cgi?p=pv-echam/pv-echam.git;a=tree;h=5f8410b1879178a4a114a279b8bd9463825e507d;hb=5f8410b1879178a4a114a279b8bd9463825e507d

[2] http://www.paraview.org/Wiki/ParaView#Compile.2FInstall

[3] http://www.paraview.org/Wiki/ParaView/Plugin_HowTo#Using_Plugins

[4] https://github.com/Cockatrice/Cockatrice/issues/205#issuecomment-183087315