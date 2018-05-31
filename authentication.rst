.. _authentication:

Authentication and connection
=============================

The Keyclic API uses the `JSON Web Tokens <https://jwt.io/>`_ to secure data transfer. Every request to the API is made with an access token allowing the server to verify the user's identity.
When logging in, the user "receives" the token. This page goes through the process of creating an account, modify an account, getting and using an accessToken.

For more informations on JWT standard, see : `JSON Web Tokens official website <https://jwt.io/>`_.

.. _authentication-account-creation:

Create a user account
---------------------

A new user account is created with this request :

.. code-block:: bash

    POST /security/register
.. code-block:: json

    {
        "email":"test@test.com",
        "password":"test"
    }

This user gets a unique id and the role ROLE_USER, allowing him to use the API's basic functionalities.

.. _authentication-login:

Login
-----

Login in consists in sending one's credentials to the server to get an accessToken which will be used in future requests.

The connection is done like this :

.. code-block:: bash

    POST /security/login
.. code-block:: json

    {
        "login":"test@test.com",
        "password":"test"
    }

If the credentials are known to the server, it returns an accessToken.

.. _authentication-using-token:

Use the token
-------------

Almost every single request to the API needs the user to be authentified. The token is sent with the Authorization header with the prefix Bearer.

For example, to get the list of all feedbacks of the com.keyclic.app application, a user uses the endpoint :

.. code-block:: bash

    GET /feedbacks

.. code-block:: bash

    Request headers :
        X-Keyclic-App : com.keyclic.app
        Authorization : Bearer eyJhbGciOiJSUzI1NiJ9.eyJyb2xlcyI6WyJPUkdBTklaQVRJT046QURNSU4iLCJST0xFX1VTRVIiXSwidXNlcm5hbWUiOiJ0ZXN0MjJAdGVzdC5jb20iLCJpcCI6Ijc3LjIwMy40NS40NCIsImV4cCI6MTQ4OTI0MTQ0NCwiaWF0IjoxNDg5MTU1MDQ0fQ.ZIqbBVSgJaXKj73IPYbFeEfie6FUIflv-ausUO-AAzVjPg8-jdhFv3nqsdOVJvE_AB4bXjME1CRVFI7xD2SYCA8V6E6H2-y0XZE8SN_XTpHGMxDvOP27C2VUNQfPwgeWxjXzlDopo_U9ybAEX4QdFhW14aeRgb9YWMDlzSD6VLgJO-LuprxX668Ajq5X9c8YND4D_p4WRDSQr8pqb3rTY9NQ6O34F-OpDJlAUYj0pwMehYWpywVKJHRMv9xCRRoI8HrU6H3J3wo-K2OtQVJi9XFZ8g8sohw_ZaasG7dohxrO-NtYSrOPXIXPI6kCDRuMi7sce06wfno1bC3jBoc83EhiBSBpDbWL98DSjPbF1SaCeE05aATfM5cMEXbnp8Iwh-QLxglE4M-ZISJ8VooxzJxa7cWLlFW-iu0XWVFWrMbYgmSoU0PKRQB47w_IOPxjWzDeMUTSA3esDwkxsYlNdS9SZe201EvI6zur5Ayot0PEGfAgex6Ew-eKOHAfnuDiqeLQLbWs4Y69FO2DooWUhkfVGdl-IGglDPgk2AOs3w19e7mx-Gmm8DlUUr-bK61NPPQ8dy7HPjXnU63-jbA17MAjHaRTO4eKopcZMWbpL-jgQjJltV3R5_0qNODaHCS_auZs2cyqFN0HL9Rred5g7t6Fxyk-8MyyX0GiTyHsp3c


All requests to the Keyclic API need an accessToken in the headers, except for the following endpoints :

- new account (POST /security/register)
- login (POST /security/login)
- password change request (POST /security/password/change-request)
- password change (POST /security/password/change/{changePasswordToken})

.. _authentication-password-change:

Password change
---------------

A user who wishes to modify his password performs the next steps.

First, he sends a request to change his password :

.. code-block:: bash

    POST /security/password/change-request
.. code-block:: json

    {
        "email":"test@test.com"
    }

This request sends an email to the user with a link ending with a verification token. Example :

.. code-block:: bash

    https://domain.com/#/password-reset/jrtVqBLxxoSA0c2hpsOBN-JQGQHGN3YXsKPMG1PWWWA

In the link above, jrtVqBLxxoSA0c2hpsOBN-JQGQHGN3YXsKPMG1PWWWA is the token to be sent in the next request. This part of the URL *https://domain.com/#/password-reset/* depends on the application used.

Then the user can change his password with :

.. code-block:: bash

    POST /security/password/change/jrtVqBLxxoSA0c2hpsOBN-JQGQHGN3YXsKPMG1PWWWA
.. code-block:: json

    {
        "password":"password"
    }

.. _authentication-user-edition:

Change user settings
--------------------

For settings other than password, the user will request on this endpoint :

.. code-block:: bash

    PATCH /people/{user}

For more information on PATCH request, see :ref:`technical-patch`.

For example, to modify one's name :

.. code-block:: json

    {
        "familyName": "Family name"
    }

A user can change the following settings : his *familyName*, his *givenName*, his *image*, his *job* and his *email*.
