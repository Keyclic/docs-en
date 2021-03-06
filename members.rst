.. _members:

Organization members and roles
==============================

When a user is part of an organization, he may receive from none to five roles, which define a set of permissions and possibles actions.

These are five roles :

- Administrator
- Agent
- Operator
- Analytic
- Export

A user may be part of several organizations, therefore his roles among the organizations may differ and are completely independent.
A user who gets affiliated with an organization becomes a *member*. A *member* possesses the same basic functionalities as a simple user.

.. _members-admin:

Administrator
-------------

Every user can create his own organization.

The user who created the organization becomes member and admin of that organization, his role is *Admin*.

The admin has the following permissions and privileges :

- Add new members,
- Change members' roles,
- Manage the organization's categories,
- Manage the organization's places,
- Manage the organization's partners,
- Consult and manage reports received and operations linked to these reports.

See : :ref:`organizations`

See : :ref:`reports`

Note : A user can be *ORGANIZATION:ADMIN* of several organizations and an organization can have several *ORGANIZATION:ADMIN*.

.. _members-agent:

Agent
-----

« Agent » is a special role suitable to members who only make feedbacks for their organization.

An agent has the possibility to :

- Activate Pro Mode (cf :ref:`feedbacks-agent`)

**Note : A user can only be an ORGANIZATION:AGENT of one organization but an organization can have several ORGANIZATION:AGENT.**

.. _members-operator:

Operator
--------

This role adds the following possibilities :

- Receive an assignment to an operation,
- Edit an operation (if assigned to that member) : change name, add pictures, change state, etc.

All members share those rights and other may stack if the member has more roles.

Note : An *ORGANIZATION:OPERATOR* can be member of several organizations and an organization can have several *ORGANIZATION:OPERATOR*.


.. _members-analytics:

Analytics
---------

The role *Analytics* allows the member to access the organization statistics.

Note : A user can have the role *ORGANIZATION:ANALYTICS* for several organizations and an organization can have several members with the role *ORGANIZATION:ANALYTICS*.

.. _members-export:

Export
------

The role *Export* allows the member to export his organization's reports to the Excel format.

Note : A user can have the role *ORGANIZATION:EXPORT* for several organizations and an organization can have several members with the role *ORGANIZATION:EXPORT*.

.. _members-retrieving:

Retrieving users
----------------

To get all of the application's users :

.. code-block:: bash

    GET /people

To get a specific user :

.. code-block:: bash

    GET /people/{user}

To filter users by pattern in email :

.. code-block:: bash

    GET /people?search[email]=martin

To get members of an organization :

.. code-block:: bash

    GET /organizations/{organization}/members

.. _members-example:

Example
-------

Retrieving a user resource will display information about his membership(s), like the organization he is a part of, what roles he has and other miscellaneous details.

.. code-block:: bash

    GET /people/5020c6ea-ca07-42d1-994f-d90b86703b1a/memberships

.. code-block:: json

    {
        "page": 1,
        "limit": 10,
        "pages": 1,
        "total": 1,
        "_links": {
            "self": {
                "href": "/people/5020c6ea-ca07-42d1-994f-d90b86703b1a/memberships?page=1&limit=10"
            },
            "first": {
                "href": "/people/5020c6ea-ca07-42d1-994f-d90b86703b1a/memberships?page=1&limit=10"
            },
            "last": {
                "href": "/people/5020c6ea-ca07-42d1-994f-d90b86703b1a/memberships?page=1&limit=10"
            }
        },
        "_embedded": {
            "items": [
                {
                    "id": "b0e7e28f-5b91-4c73-875e-8f34aa03553a",
                    "roles": [
                        "ORGANIZATION:AGENT"
                    ],
                    "createdAt": "2018-02-27T10:00:00+02:00",
                    "_links": {
                        "self": {
                            "href": "/organizations/84d36093-b8bc-47ad-bc8a-a043b3e301a9/members/b0e7e28f-5b91-4c73-875e-8f34aa03553a",
                            "iriTemplate": {
                                "mapping": {
                                    "organization": "84d36093-b8bc-47ad-bc8a-a043b3e301a9",
                                    "member": "b0e7e28f-5b91-4c73-875e-8f34aa03553a"
                                }
                            }
                        },
                        "person": {
                            "href": "/people/5020c6ea-ca07-42d1-994f-d90b86703b1a",
                            "iriTemplate": {
                                "mapping": {
                                    "person": "5020c6ea-ca07-42d1-994f-d90b86703b1a"
                                }
                            }
                        },
                        "organization": {
                            "href": "/organizations/84d36093-b8bc-47ad-bc8a-a043b3e301a9",
                            "iriTemplate": {
                                "mapping": {
                                    "organization": "84d36093-b8bc-47ad-bc8a-a043b3e301a9"
                                }
                            }
                        }
                    },
                    "_embedded": {
                        "availableRoles": [
                            "ORGANIZATION:ADMIN",
                            "ORGANIZATION:ANALYTICS",
                            "ORGANIZATION:EXPORT",
                            "ORGANIZATION:READ_ONLY"
                        ]
                    }
                }
            ]
        }
    }

This json shows the user :

- is a member of an organization whose id is 84d36093-b8bc-47ad-bc8a-a043b3e301a9
- has the role ORGANIZATION:ADMIN : he is an admin of the organization 84d36093-b8bc-47ad-bc8a-a043b3e301a9
- has the role ORGANIZATION:AGENT : he is an agent of the organization 84d36093-b8bc-47ad-bc8a-a043b3e301a9
- is part of only one organization
- joined the organization February 27, 2018

CAUTION: The user id (5020c6ea-ca07-42d1-994f-d90b86703b1a) is not the same as the member id (b0e7e28f-5b91-4c73-875e-8f34aa03553a).
The API identifies a member and a user as two differents entities.