.. _integration:

Integration
===========

Webhooks
--------

Unlike an API that requires continuous requests, the Keyclic service offers webhooks when certain events occur (see list below).

It is an easy and efficient way to call a service or application to get notifications and break free from the constant check.

Webhooks have various uses, such as :

    - collect reports created for your data warehouse,
    - sync reports and operations with your IS (ex: CMMIS, ...),
    - send notifications

Webhook creation and configuration
----------------------------------

Webhooks can be created upon request from our service.

A webhook consists of the event for which you wish to be notified and a URL to where the notification should be sent.

Several webhooks can be created unlimitedly for each event type.

Event types
-----------

+------------------------------+-----------------------------------------------------------+
| Event                        | Description                                               |
+==============================+===========================================================+
| **reportCreated**            | New report created                                        |
+------------------------------+-----------------------------------------------------------+
| **reportStateChanged**       | Report's state changed                                    |
+------------------------------+-----------------------------------------------------------+
| **operationCreated**         | New operation created                                     |
+------------------------------+-----------------------------------------------------------+
| **operationStateChanged**    | Operation's state changed                                 |
+------------------------------+-----------------------------------------------------------+
| **operationRemoved**         | Operation removed                                         |
+------------------------------+-----------------------------------------------------------+

Receipt of webhook notification
-------------------------------

A webhook notification is sent in JSON format in the HTTP request body to the configured URL for that webhook.
It contains the event name and a payload consisting of the resource details of the event. The resource varies according to the event.

note : The resource has the same serialization when requested to the API and in a webhook notification,
it is possible to run through resources linked or embedded thanks to the HAL representation of our API.

.. code-block:: json

    {
        "event": "reportCreated",
        "payload": {
            "type": "Report",
            "id": "b0e7e28f-5b91-4c73-875e-8f34aa03553a",
            "state": "NEW",
            "createdAt": "2018-02-27T10:00:00+02:00",
            "updatedAt": "2018-02-27T10:00:00+02:00",
            "_links": {
                "feedback": "...",
                "operations": "...",
                "organization": "...",
                "tracking": "...",
            },
            "_embedded": {
                "stateTransitions": "...",
                "tracking": "..",
            }
        }
    }

*Partial example of a webhook notification received after the a new report is created.*
