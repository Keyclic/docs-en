.. _organizations:

Organizations
=============

In the Keyclic app, an organization is an entity such as a company, a corporation, an association, a school, etc. to which feedbacks can be sent to be treated.

A :ref:`members-no-roles` is a user affiliated with an organization. One or more members can be administrators of that organization (see : :ref:`members-admin`). An organization has at least one administrator.

An :ref:`members-admin` can manage the scope of intervention of the organization by creating categories and places.
When a user creates a feedback, geographic coordinates of that feedback are always automatically given. Thus, the app can display all organizations and their category in that place.
Then the user can choose which organization he wants to take care of the problem.

.. _organizations-creation:

Creation
--------

All users can create an organization :

.. code-block:: bash

    POST /organizations

.. code-block:: json

    {
        "name":"organization name",
        "billingEmailAddress":"test@test.com",
        "notificationEmailAddress":"test@test.com"
    }

The user becomes member and admin of this new organization.

To get all organizations of an application :

.. code-block:: bash

    GET /organizations

It's possible to filter results by geographic point (see below : :ref:`organizations-places`) :

.. code-block:: bash

    GET /organizations?geo_coordinates=+44.851404209987386-0.5762618780136108

.. _organizations-members:

Manage members
--------------

To add a new member to the organization :

.. code-block:: bash

    POST /organizations/{organization}/members

.. code-block:: json

    {
        "person":"63d07fc5-f4e6-471c-a8cc-3c3f227c8c2d"
    }

This endpoint is reserved to a user who is ORGANIZATION:ADMIN and member of the organization {organization}.

To get organization's members :

.. code-block:: bash

    GET /people?organization={organization}

To remove a member from the organization, an admin will request :

.. code-block:: bash

    DELETE /organizations/{organization}/members/{member}

For more informations on the role ORGANIZATION:ADMIN and its privileges, see :ref:`members-admin`.

.. _organizations-places:

Manage places
-------------

An admin can create places, corresponding to areas where the organization can take actions :

.. code-block:: bash

    POST /organizations/{organization}/places

.. code-block:: json

    {
        "name": "Test",
        "polygon":
        {
            "rings":
            [
                {
                    "points":
                    [
                        {
                            "longitude": 2.373991012573242,
                            "latitude": 48.84088179130599
                        },
                        {
                            "longitude": 2.3763084411621094,
                            "latitude": 48.84205393836751
                        },
                        {
                            "longitude": 2.376694679260254,
                            "latitude": 48.84189859515306
                        },
                        {
                            "longitude": 2.3787975311279297,
                            "latitude": 48.84041574931067
                        },
                        {
                            "longitude": 2.376115322113037,
                            "latitude": 48.839031720249054
                        },
                        {
                            "longitude": 2.373991012573242,
                            "latitude": 48.84088179130599
                        }
                    ]
                }
            ],
            "srid": 5555
        },
        "elevation": 1
    }

To get all places of the application :

.. code-block:: bash

    GET /places

This request may be filtered by organization and/or geographic points :

.. code-block:: bash

    GET /places?geo_coordinates=+44.851404209987386-0.5762618780136108&organization={organization}

.. _organizations-categories:

Manage categories
-----------------

Categories are the business sectors of an organization. An admin can create a new category with a name, a color and an icon. The icon is chosen from `Font Awesome <http://fontawesome.io/icons/>`_.

.. code-block:: bash

    POST /organizations/{organization}/categories

.. code-block:: json

    {
        "name":"Category's name",
        "color":"#ff0000",
        "icon":"fa-bug"
    }

Those 3 properties can be edited with a PATCH request (see : :ref:`technical-patch`).

To get all categories of the application :

.. code-block:: bash

    GET /categories

This request may be filtered by organization and/or geographic points :

.. code-block:: bash

    GET /categories?geo_coordinates=+44.851404209987386-0.5762618780136108&organization={organization}

.. _organizations-relationships:

Manage partnership
------------------

An organization can have partners, i.e organizations affiliated with it. This relationship is one-sided :
an organization A is a partner of organization B, but B is not necessarily one of B.

The partnership means that an admin can delegate a report to a partner organization. In the previous example, A can delegate a report to B, but B cannot delegate to A.

To add a new partner to the organization, an admin will send the request :

.. code-block:: bash

    POST /organizations/{organization}/relationships

.. code-block:: json

    {
        "organization":"84d36093-b8bc-47ad-bc8a-a043b3e301a9"
    }

To get an organization's partners :

.. code-block:: bash

    GET /organizations/{organization}/relationships

The request is only available for admins.
