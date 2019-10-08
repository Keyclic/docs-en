.. _notifications:

Notifications
=============

The Keyclic service can notify users when some actions are made.

.. _notifications-table:

Notifications sent by action
----------------------------

+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Action                         | Target                                                  | Push  | Wall  | Mail  |
+================================+=========================================================+=======+=======+=======+
| User register                  | The user                                                |   ⨯   |   ⨯   |   ✓   |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Password change request        | The user                                                |   ⨯   |   ⨯   |   ✓   |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Feedback is commented          | The user who made the feedback                          |   ✓   |   ✓   |   ⨯   |
|                                |                                                         |       |       |       |
|                                | Users who commented or supported to the feedback        |       |       |       |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Report is created              | Administrators                                          |   ✓   |   ✓   |   ✓   |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Report is accepted             | The user who made the feedback                          |   ✓   |   ✓   |   ⨯   |
|                                |                                                         |       |       |       |
|                                | Users who commented or supported to the feedback        |       |       |       |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Report is closed               | The user who made the feedback                          |   ✓   |   ✓   |   ⨯   |
|                                |                                                         |       |       |       |
|                                | Users who commented or supported to the feedback        |       |       |       |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Report is refused              | The user who made the feedback                          |   ✓   |   ✓   |   ⨯   |
|                                |                                                         |       |       |       |
|                                | Users who commented or supported to the feedback        |       |       |       |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Report is delegated            | Administrators                                          |   ✓   |   ✓   |   ✓   |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Add document to report         | Administrators                                          |   ✓   |   ✓   |   ⨯   |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Operation assigned             | Member assigned to the operation                        |   ✓   |   ✓   |   ✓   |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Operation resolved             | Administrator who created the operation                 |   ✓   |   ✓   |   ⨯   |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Operation remind               | Opertors                                                |   ✓   |   ✓   |   ⨯   |
|                                |                                                         |       |       |       |
|                                | The user who made the feedback                          |       |       |       |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Operation is commented         | Member assigned to the operation                        |   ✓   |   ✓   |   ⨯   |
|                                | Administrator who created the operation                 |       |       |       |
|                                |                                                         |       |       |       |
|                                | Members who commented the operation                     |       |       |       |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+
| Feedback to review             | Reviewer                                                |   ✓   |   ✓   |   ⨯   |
+--------------------------------+---------------------------------------------------------+-------+-------+-------+

When a user makes an action which triggers a notification where it would be targeted. This user doesn't receive a notification.
For example, if a member assigned to an operation leaves a comment on the operation, it doesn't receive a notification saying it commented the operation.
