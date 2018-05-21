.. _notifications:

Notifications
=============

Le service Keyclic peut notifier des utilisateurs après que certaines actions sont réalisées.

.. _notifications-table:

Type des notifications émises suivant les actions
-------------------------------------------------

+------------------------------+-------------------------+------------------------------------------------------------------------+
| Action                       | Type de notification    | Destinataire                                                           |
+==============================+=========================+========================================================================+
| Création de rapport          | Email + Push smartphone | Les administrateurs de l'organisation                                  |
+------------------------------+-------------------------+------------------------------------------------------------------------+
| Clôture du rapport           | Push smartphone         | L'émetteur de l'observation (dont le rapport est issu)                 |
|                              |                         |                                                                        |
|                              |                         | Les personnes qui ont soutenu l'observation (dont le rapport est issu) |
+------------------------------+-------------------------+------------------------------------------------------------------------+
| Assignation d'une opération  | Push smartphone         | Le membre assigné à l'opération                                        |
+------------------------------+-------------------------+------------------------------------------------------------------------+
| Exportation des rapports     | Email                   | L'administrateur courant de la session                                 |
+------------------------------+-------------------------+------------------------------------------------------------------------+
| Modération d'une observation | Push smartphone         | Les administrateurs de l'application                                   |
+------------------------------+-------------------------+------------------------------------------------------------------------+


