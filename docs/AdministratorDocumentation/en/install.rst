After Publish
=============

After publishing a test instance of HomeWeb we need to create a log folder and grant the neccessary permissions:

.. code-block:: none
   
   mkdir x:\www\HomeWebTest\Log
   icacls x:\www\HomeWebTest\Log /inheritance:d /grant "IIS APPPOOL\www":(OI)(CI)M /grant "IIS_IUSRS":(OI)(CI)M /T