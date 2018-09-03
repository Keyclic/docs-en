.. _notifications:

Notifications
=============

The Keyclic service can notify users when some actions are made.

.. _notifications-table:

Notifications sent by action
----------------------------

+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Action                         | Notification Type       | Target                                                                 |
+================================+=========================+========================================================================+
| Feedback to moderate           | Push smartphone         | Moderators                                                             |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Feedback is commented          | Push smartphone         | The user who made the feedback                                         |
|                                |                         |                                                                        |
|                                |                         | Users who commented or supported to the feedback                       |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Report is created              | Email + Push smartphone | Administrators                                                         |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Report is accepted             | Push smartphone         | The user who made the feedback                                         |
|                                |                         |                                                                        |
|                                |                         | Users who commented or supported to the feedback                       |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Report is closed               | Push smartphone         | The user who made the feedback                                         |
|                                |                         |                                                                        |
|                                |                         | Users who commented or supported to the feedback                       |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Report is refused              | Push smartphone         | The user who made the feedback                                         |
|                                |                         |                                                                        |
|                                |                         | Users who commented or supported to the feedback                       |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Delegated report is accepted   | Push smartphone         | Administrators of parent report                                        |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Delegated report is closed     | Push smartphone         | Administrators of parent report                                        |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Delegated report is refused    | Push smartphone         | Administrators of parent report                                        |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Operation assigned             | Push smartphone         | Member assigned to the operation                                       |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Operation resolved             | Push smartphone         | Administrators                                                         |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Operation is commented         | Push smartphone         | Member assigned to the operation                                       |
|                                |                         |                                                                        |
|                                |                         | Members who commented the operation                                    |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Feedback to review             | Push smartphone         | Reviewer                                                               |
+--------------------------------+-------------------------+------------------------------------------------------------------------+
| Report(s) exported             | Email                   | Administrator who sent the request                                     |
+--------------------------------+-------------------------+------------------------------------------------------------------------+

