.. _members:

Membres d'organisation et rôles
===============================

Quand un utilisateur est membre d’une organisation, il peut bénéficier de  aucun, un ou plusieurs rôles définissant un ensemble de permissions et de possibilités d’actions.

Définissant un ensemble de droits, ces rôles peuvent être cumulés pour un même utilisateur et sont au nombre de cinq :

Les utilisateurs de l'application Keyclic possèdent un ou plusieurs rôles, définissant un ensemble de permissions et de possibilités d'action. Ces rôles, qui peuvent être cumulés pour un même utilisateur, sont au nombre de trois :

- Aucun rôle - Membre d’organisation
- Administrateur d’organisation
- Agent
- Statistiques
- Export

Un utilisateur pouvant être membre de plusieurs organisations, les rôles qu’il possède sont indépendants et peuvent être différent d’une organisation à une autre.

.. _members-no-roles:

Aucun rôle - Membre d’organisation
----------------------------------

Tout utilisateur nouvellement attaché à une organisation devient « Membre d’organisation ». Un « Membre d’organisation » possède les mêmes droits qu’un utilisateur de base sans attachement à une organisation.

Ce rôle permet en plus de pouvoir :

- Être listé par les administrateurs de l’organisation
- Recevoir une assignation à une intervention
- Éditer une intervention (changement des libellés, ajout de photos de constatation, etc)
- Changer le statut d’une intervention

Note : Un utilisateur peut être membre d’organisation de plusieurs organisations et une organisation peut avoir plusieurs membres d’organisation.

.. _members-organization-admin:

Administrateur d'organisation
-----------------------------

Tout utilisateur a la possibilité de créer une nouvelle organisation.

L’utilisateur qui créé une nouvelle organisation en devient automatiquement membre et administrateur, c’est-à-dire qu’il se voit attribuer le rôle « Administrateur d’organisation ».

Aux permissions et aux droits des « Membres d’organisation » s’ajoute les suivants :

- Ajouter de nouveaux membres à une organisation
- Gérer les catégories d’une organisation
- Gérer les zones de responsabilité d’une organisation
- Gérer les partenaires d’une organisation
- Consulter et gérer les rapports reçus d’une  et les opérations liées à ces rapports

Voir : :ref:`organizations`

Voir : :ref:`reports`

Note : Un utilisateur peut être « Administrateur d’organisation » de plusieurs organisations et une organisation peut avoir plusieurs « Administrateurs d’organisation ».

.. _members-agent:

Agent
-----

« Agent » est un rôle particulier adapté aux personnels de terrain qui effectuent des remontées d’observation uniquement dédiées à leur organisation.

Aux permissions et aux droits des « Membres d’organisation » s’ajoute les suivants :

- Activer le Mode Pro (cf infra: Observation postée en Mode Pro)
- De remonter par défaut des observations privées

**Note : Un utilisateur ne peut être « Agent » que d’une seule organisation et une organisation peut avoir plusieurs « Agents ».**

.. _members-stat:

Statistiques
------------

Le rôle « Statistique » permet d’accéder aux statistiques d’une organisation.

Note : Un utilisateur peut avoir le rôle « Statistique » pour plusieurs organisations et une organisation peut avoir plusieurs utilisateurs avec le rôle « Statistique ».

.. _members-export:

Export
------

Le rôle « Export » permet d’accéder aux fonctionnalités d’exportation excel des rapports qu’a reçu une organisation.

Note : Un utilisateur peut avoir le rôle « Export » pour plusieurs organisations et une organisation peut avoir plusieurs utilisateurs avec le rôle « Export ».

.. _members-example:

Exemple de ressource utilisateur
--------------------------------

*Déprécié: La section suivante doit être mise à jour pour prendre en considération la nouvelle gestion matricielle des rôles.*


La lecture d'une ressource Utilisateur permet de découvrir les rôles de cet utilisateur, et éventuellement l'organisation dont il est administrateur et/ou l'application dont il est administrateur.

.. code-block:: bash

    GET /people/{user}

.. code-block:: json

    {
      "username": "test@gmail.com",
      "email": "test@gmail.com",
      "type": "Person",
      "roles": [
        "APPLICATION:ADMIN",
        "ORGANIZATION:ADMIN",
        "ROLE_USER"
      ],
      "id": "5020c6ea-ca07-42d1-994f-d90b86703b1a",
      "createdAt": "2017-02-20T17:52:39+01:00",
      "updatedAt": "2017-02-27T14:48:39+01:00",
      "_links": {
        "self": {
          "href": "/people/5020c6ea-ca07-42d1-994f-d90b86703b1a",
          "iriTemplate": {
            "mapping": {
              "person": "5020c6ea-ca07-42d1-994f-d90b86703b1a"
            }
          }
        },
        "memberOf": {
          "href": "https://api.sandbox.keyclic.com/organizations/84d36093-b8bc-47ad-bc8a-a043b3e301a9",
          "iriTemplate": {
            "mapping": {
              "organization": "84d36093-b8bc-47ad-bc8a-a043b3e301a9"
            }
          }
        }
      }
    }

Ce retour indique que :

1. Cet utilisateur possède le rôle ROLE_USER, comme tous les utilisateurs.
2. Il est membre de l'organisation 84d36093-b8bc-47ad-bc8a-a043b3e301a9
3. Il possède le rôle ORGANIZATION:ADMIN, il est donc administrateur de l'organisation 84d36093-b8bc-47ad-bc8a-a043b3e301a9
4. Il possède le rôle APPLICATION:ADMIN, il est donc administrateur de l'application à laquelle est rattachée l'organisation 84d36093-b8bc-47ad-bc8a-a043b3e301a9

.. _members-retrieving:

Récupération des utilisateurs
-----------------------------

Pour récupérer l'ensemble des utilisateurs de l'application :

.. code-block:: bash

    GET /people

Pour récupérer un utilisateur :

.. code-block:: bash

    GET /people/{user}

Pour rechercher les membres dont l'adresse email match un mot donné :

.. code-block:: bash

    GET /people?search[email]=martin

Pour filtrer les membres d'une organisation :

.. code-block:: bash

    GET /people?organization={organization}

