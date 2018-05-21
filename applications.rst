.. _applications:

Applications
============

Une *application* au coeur du service Keyclic permet de cloisonner les remontées d’observation suivant des domaines applicatifs.
Cela se traduit par l’utilisation d’applications clientes ou de sites internet spécifiques à certains métiers.

Pour le client éponyme du service, l'*application* déclarée est "com.keyclic.app", toutes les applications clientes ou sites internet utilisant cette clé auront le même cloisement. (Ici : l'application iPhone Keyclic, l'application Android Keyclic et le site internet https://app.keyclic.com pour les navigateurs.)

Il existe d’autres *applications* déclarées dans le service Keyclic avec d'autres clés, notamment "Vinci Mon Autoroute" disponible sur iPhone et Android.

Par exemple depuis "Vinci Mon Autoroute":

 - il est impossible de remonter une observation à l’*application* déclarée avec la clé "com.keyclic.app" et inversement,

 - il est impossible de lister les observations dédiées à l’*application* déclarée avec la clé "com.keyclic.app" et inversement.

.. _applications-admin:

Administrateur d'application
----------------------------

L’ *administrateur d’application* est un statut particulier donné à un utilisateur du service Keyclic qui a la possibilité de **modérer** les observations d’une *application* avant que celles-ci soient transmises, sous forme de rapports, aux organisations concernées.

Cette modération permet de filtrer toutes observations avec du contenu enfreignant les règles d’utilisation d’une application cliente ou d'un site internet. Par exemple, obstruction à la législation d’un pays (contenu pédopornographique, incitation à la haine, etc).

Plusieurs *administrateurs d'application* peuvent modérer les observations d'une *application*. Cependant un *administrateur d'application* ne peut pas modérer les observations provenant de plusieurs *applications*.

Note : L' *administrateur d'application* n'est pas obligatoirement membre d'une organisation ou n'est pas obligatoirement employé par la société Keyclic.

Cas particulier
---------------

Toutes les observations ne sont pas soumises à la modération.
C'est le cas d'une observation effectuée par un acteur de confiance. (Voir :ref:`feedbacks-organization-member`.)
