Renovation of HomeWeb
=====================

A renovation could only be done with respect to the running production system. First step would be to separate some libraries and provide them as NuGet package.

Separation of Libraries
-----------------------

Access to Videodb
~~~~~~~~~~~~~~~~~
Videodb part of HomeWeb is inspired from the original "VideoDB".

http://www.videodb.net/blog/and 
VideoDB was originally developed by Andreas Gohr. In 2003, Andreas Götz took over development. He’s also the current maintainer of videoDB.

https://www.splitbrain.org/projects/videodb
https://sourceforge.net/projects/videodb/
https://github.com/andig/videodb

HomeWebs integration of videodb doesn't need the PHP version of VideoDb but is based on the MySQL DB schema of this great work.

Today the database access to the MySQL database is deeply coupled with the MVC Controllers. There have been attempts to decouple the access but neither they have been completly finished nor is the work documented.

When the renovation idea was set I first thought about building a .NET Core WebAPI which is consumed by a Angular2 driven web page. This lead me into fiddeling with Angular2 - with which I'm not familiar - one one hand and following the .NET Core WebAPI tutorials on the other hand. Finally this brought my to the end that I'm still missing a clear data access layer to the VideoDB MySQL database.

Access to Ofdb (MovieMetaEngine)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
MovieMetaEngine is now available via nuget.org.

.. code-block:: none

   Install-Package Jaxx.MovieMetaEngine

