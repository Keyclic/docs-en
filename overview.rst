.. _overview:

Aperçu
======

Fonctionnement général
----------------------

L'application Keyclic est librement ouverte aux inscriptions. Une fois inscrit, tout utilisateur peut créer des observations. Une observation est toujours liée à une position géographique et comporte éventuellement une ou plusieurs photos.

Certains utilisateurs peuvent également être regroupés au sein d'organisations. Une organisation est donc un groupe d'utilisateurs membres de la même entreprise, association, corporation, école, etc. Tout utilisateur est libre de créer sa propre organisation et d'inviter d'autres utilisateurs à en devenir membres.

Les administrateurs d'organisation définissent des zones de responsabilité sur lesquelles leur organisation peut intervenir, et des catégories d'intervention (exemples : voirie, animal perdu, propreté, etc...) Ainsi, quand un utilisateur crée une observation, la position géographique de cette observation permet de lui proposer les catégories et organisations qui sont en mesure de traiter son signalement et de le laisser choisir celle qui lui semble la plus adaptée.

Quand un utilisateur crée une observation, celui-ci a le choix de la rendre publique ou privée. Si publique, l'observation est visible par la communauté : ainsi, les autres utilisateurs peuvent la commenter et/ou la soutenir.

De plus, au moment où l'observation est créée, celle-ci doit tout d'abord être modérée par un administrateur de l'application, sauf dans certains cas où la modération est automatique (voir : :ref:`feedbacks-lifecyle`).
L'observation validée, un rapport est généré et transmis à l'organisation concernée.

Un administrateur d'organisation a donc accès à l'ensemble des rapports concernant son organisation, chaque rapport correspondant à une observation. Pour chaque rapport, il peut créer une ou plusieurs interventions, et affecter ces interventions aux membres de son organisation. Une autre possibilité est de déléguer ce rapport à une organisation partenaire, le patenaire aura alors la charge de créer des intervent.  Une fois que toutes les interventions ont été accomplies, il pourra considérer que le traitement est terminé et clôturer le rapport.

Liens utiles
------------

- `Spécification Swagger de l'API <https://api.keyclic.com/swagger.json>`_
- `Documentation technique de l'API <https://app.swaggerhub.com/apis/Keyclic/keyclic/>`_
- `Code source du SDK client javascript <https://github.com/Keyclic/app-sdk>`_

Vocabulaire
-----------

Observation
~~~~~~~~~~~

Remarque effectuée sur le terrain par un utilisateur, pouvant porter sur un dysfonctionnement, un problème technique, une nuisance, etc. Toute observation est forcément faite en une position géographique donnée. Elle peut éventuellement comporter des photos, et être commentée et/ou soutenue par les autres utilisateurs.

Terme technique : feedback.

Voir la page :ref:`feedbacks`.

Rapport
~~~~~~~

Toute observation, une fois validée par un administrateur de l'application, entraîne la génération d'un rapport. Un rapport reprend donc toutes les informations de l'observation dont il est issu, et n'est visible et manipulable que par l'organisation concernée. Le rapport peut donc être vu comme le pendant « professionnel » de l'observation. C'est sur ce rapport que l'organisation travaille : création d'interventions, suivi, délégation, etc.

Terme technique : report.

Voir la page :ref:`reports`

Organisation
~~~~~~~~~~~~

Groupe d'utilisateurs pouvant être une entreprise, une école, une association, un groupe de pesonnel d'un site, d'un chantier, etc.

Terme technique : organization.

Voir la page :ref:`organizations`.

Zone de responsabilité
~~~~~~~~~~~~~~~~~~~~~~

Aire géographique sur laquelle une organisation peut intervenir.

Terme technique : place.

Voir la section :ref:`organizations-places`.

Catégorie
~~~~~~~~~

Secteur d'activité d'une organisation.

Terme technique : category.

Voir la section :ref:`organizations-categories`.


Soutien
~~~~~~~

Une observation peut être soutenue par les utilisateurs de la communauté, afin de leur donner plus de poids.

Terme technique : contribution.

Voir la section :ref:`feedbacks-contributions`.

Opération
~~~~~~~~~

Une opération est une tâche créée par un administrateur d'organisation sur un rapport donné. Cette tâche est assignée à un membre de l'organisation. Un rapport ne peut être clôturé que si toutes les opérations qui lui sont liées ont été accomplies (ou refusées).

Terme technique : operation.

Voir la section :ref:`reports-operations`.

Partenaires
~~~~~~~~~~~

Un administrateur d'organisation peut définir des organisations partenaires, qui sont d'autres organisations auxquelles il pourra déléguer des rapports.

Terme technique : relationship.

Voir la section :ref:`organizations-relationships`.
