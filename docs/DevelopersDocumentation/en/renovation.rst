Renovation of HomeWeb
=====================

A renovation could only be done with respect to the running production system. First step would be to separate some libraries and provide them as NuGet package.

Separation of Libraries
-----------------------

Access to Videodb
~~~~~~~~~~~~~~~~~
Videodb part of HomeWeb is based on the database from the original "VideoDB".

http://www.videodb.net/blog/
VideoDB was originally developed by Andreas Gohr. In 2003, Andreas Götz took over development. He’s also the current maintainer of videoDB.

https://www.splitbrain.org/projects/videodb
https://sourceforge.net/projects/videodb/
https://github.com/andig/videodb

HomeWebs integration of videodb doesn't need the PHP version of VideoDb but is based on the MySQL DB schema of this great work.

Access to Ofdb (MovieMetaEngine)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
MovieMetaEngine is now available via nuget.org.

.. code-block:: none

   Install-Package Jaxx.MovieMetaEngine

