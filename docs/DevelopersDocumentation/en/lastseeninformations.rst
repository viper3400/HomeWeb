LastSeenInformations
====================

LastSeenInformations is a simple class which holds informations about the date a movie was last seen by a user:

* DateTime LastSeenDate
* int SeenCount
* int DaysSinceLastView
* string LastSeenSentence

For simpler representation in the view the string LastSeenSentence provides a prebuild string.

    "Du hast diesen Film bereits 3 Mal gesehen, zuletzt am 05.04.2013, das war vor 2054 Tagen."

While the above is just an example an the calucaltion of the day is not correct it shows the principle. So, the *LastSeenSentence* is kind of a combination of the other class members.

ILastSeenSentenceProvider
-------------------------
As long a the *DaysSinceLastView* count remain within 365 days (a year) it's okay, but when it gets greater it's getting more and more complicated to the user to get familiar with the days.

DefaultLastSeenSentenceProvider
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This provider is based on basic .NET TimeSpan functions and will return just the DaysSinceLastView in days.

NodaTimeLastSeenSentenceProvider
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
While basic .NET TimeSpan functions just offer difference in days this implementation uses `NodaTime <http://nodatime.org/>`_ to convert days into years and days.

