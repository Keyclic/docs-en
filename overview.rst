.. _overview:

Overview
========

General purpose
---------------

The Keyclic app is free and open to registration. Once registered, a user can create feedbacks. A feedback is always linked to a geographic point and may contain one or more pictures.

Users can join or create an organization. This a group of users from the same company, school, association, etc.

Administrators define places where their organization can act and categories (example: road network, lost animal, cleaning, etc).
Thus, when a user creates a feedback, the app will display organizations able to deal with the problem and their category and let him choose which organization corresponds the most.

When a user created a feedback, he may choose to make it public or private. If public, the feedback will be visible by the entire community and they can comment it or support it.

Furthermore, the moment the feedback is created, it is transmitted to a moderator to be moderated, to avoid illicit content, except in certain situations (see : :ref:`feedbacks-life-cycle`).
Once validated, a report is created and sent to the chosen organization.

A report corresponds to one and only one feedback. An admin has access to all the reports sent to its organization. For each reports, he can create has many interventions as necessary and assign them to members of his organization. Another way is to delegate the report to a partner organization that will deal with it
Once every intervention resolved, the admin will then close the report and consider the problem resolved.

Useful links
------------

- `API's Swagger <https://api.keyclic.com/swagger.json>`_
- `SDK client Javascript source code <https://github.com/Keyclic/app-sdk>`_
- `API's Technical documentation <https://app.swaggerhub.com/apis/Keyclic/keyclic/>`_

Vocabulary
-----------

Feedback
~~~~~~~~

Observation made by a user. It may be a technical problem, a malfunction, a nuisance, etc. Every feedback is made with coordinates from the geolocation. It may contain pictures, be commented and/or be supported.

See :ref:`feedbacks`.

Report
~~~~~~~

Each feedback, once moderated by a moderator, creates a report. A report contains the informations from the feedback and can only be seen and modified by the organization it was sent to.
The report is the "professional" side of the observation. The organization works from this report: creation of interventions, state, delegation, etc.

See :ref:`reports`

Organization
~~~~~~~~~~~~

Group of users. It may be a company, a school, an association, a group of worker on a construction site, etc.

See :ref:`organizations`.

Places
~~~~~~

Geographic area where an organization can take action.

See :ref:`organizations-places`.

Category
~~~~~~~~

Business sector of an organization.

See :ref:`organizations-categories`.

Contribution
~~~~~~~

A feedback may be supported by other users of the community, to give it more value.

See :ref:`feedbacks-contributions`.

Operation
~~~~~~~~~

Task created by an admin on a report. This task is assigned to a member of the organization.

See :ref:`reports-operations`.

Relationship
~~~~~~~~~~~

An admin can choose partner organizations (with mutual consent), which are other organizations he will be able to delegate reports.

See :ref:`organizations-relationships`.
