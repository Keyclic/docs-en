.. _applications:

Applications
============

An *application* in the Keyclic service limits the resources to a single domain.
It means the use of specific clients app or website.
For the eponymous client of the service, the *application* is "com.keyclic.app". Every client app and website using the key will share the same partition.
(Here: the iPhone app Keyclic, the Android app Keyclic and the website https://app.keyclic.com)

Other *applications* exist in the Keyclic service with different keys, it's the case of "Vinci Mon Autoroute" available on iPhone and Android.

For example, from "Vinci Mon Autoroute":

 - it is impossible to "send" a feedback sent to this *application* with the key "com.keyclic.app" and vice-versa,

 - it is impossible to list feedbacks sent to the *application* with the key "com.keyclic.app" and vice-versa.

.. _moderator:

Moderator
---------

The *moderator* is a specific status given by the Keyclic service, who can **moderate** feedbacks from an *application* before they are sent as reports to the chosen organization.

This moderation filters every feedback to avoid content violating general terms of use of an application or website. For example, pornographic content, racial discrimination, etc.

Several *moderators* can moderate feedbacks of one *application*. However, a *moderator* can't moderate feedbacks from more than one *application*

Note: The *moderator* may not be a member of the organization it is moderating for, nor a Keyclic employee.

Special case
------------

Not all feedbacks are moderated, those made by a trusty user are directly sent to the organization (See :ref:`feedbacks-agent`.)
