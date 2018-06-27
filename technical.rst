.. _technical:

Technical considerations
=========================

The Keyclic API is RESTful. Every operation is sent through **HTTPS** and is secured with `JSON Web Tokens <https://jwt.io/>`_. The data is sent only in **JSON** format.

The Keyclic API's domain name is :

.. code-block:: bash

    api.keyclic.com

Useful links
------------

- `API's Swagger <https://api.keyclic.com/swagger.json>`_
- `Technical API documentation <https://app.swaggerhub.com/apis/Keyclic/keyclic/>`_

.. _technical-applications:

Applications and Application's key
----------------------------------

Every client of the API must send a key identifying his application in the request header

If you are developing a client to work with an existing Keyclic application, you have to know the application's key.
Else if you wish to develop a client for a new application, please contact Keyclic. They will create the new application, configure it and send you the corresponding key.

Examples of an application's key :

- com.keyclic.app
- com.keyclic.city
- com.keyclic.highway

Then every request header has to contain a X-Keyclic-App field with a value like the examples above. Refer to this paragraph :ref:`technical-requests` for the "implementation".

However, users accounts are shared to all Keyclic applications. Therefore, login and register endpoints do not require to provide an application key (cf : :ref:`authentication`).

.. _technical-requests:

Requests
--------

In this documentation, each API's endpoint will be described by an `HTTP verb <https://tools.ietf.org/html/rfc7231#section-4>`_ and the path to access the resource.

Example :

.. code-block:: bash

    GET /feedbacks

This endpoint returns every feedback. Its actual URL is

.. code-block:: bash

    https://api.keyclic.com/feedbacks

but to avoid redundancy, in the following examples, we will show neither the protocol nor the domain name.

URL's parameters
~~~~~~~~~~~~~~~~

In this documentation, URIs variables, such as a resource identifier, a page number, etc, will be between curly brackets. For example, to retrieve a single feedback :

.. code-block:: bash

    GET /feedbacks/{feedback}

In the Keyclic API, in accordance with REST principles, the filtering parameters will always be in the query string. Example :

.. code-block:: bash

    GET /feedbacks?page={page}

Moreover, for a better visibility, URI's parameters will be written as such and not in their encoded URL form :

.. code-block:: bash

    GET /feedbacks?before=2018-04-22T01:00:00+05:00

Headers
~~~~~~~

Besides `conventional HTTP/1.1 <https://tools.ietf.org/html/rfc7231#section-5>`_ headers, Keyclic API accepts and in most cases requires, the header **X-Keyclic-App**, corresponding
to the application used (see above : :ref:`technical-applications`). For example, to get all feedbacks from the com.keyclic.app application, the request will have to contain the following header :

.. code-block:: bash

    X-Keyclic-App : com.keyclic.app

Every endpoint requires this header, except for login and password modification. (refer : :ref:`authentication`)

Also, every request (except login, register and password modification) must contain the Authorization header (see : :ref:`authentication`).

.. _technical-format:

Request and response format
---------------------------

The only type of content accepted by the Keyclic API is JSON. Requests must contain the header :

.. code-block:: bash

    Content-type: application/json

and the body will always have to in JSON format. The responses are returned to the JSON format too.

.. _technical-files:

Send files
----------

Files are sent in base 64 to the API. Here is an example of adding an image to a feedback :

.. code-block:: bash

    POST /feedbacks/{feedback}/images

.. code-block:: json

    {
        "image":"data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAIAAAACDbGyAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH4QIVDRUfvq7u+AAAABl0RVh0Q29tbWVudABDcmVhdGVkIHdpdGggR0lNUFeBDhcAAAAUSURBVAjXY3wrIcGABJgYUAGpfABZiwEnbOeFrwAAAABJRU5ErkJggg=="
    }

.. _technical-pagination:

Pagination
----------

Endpoints requesting a collection of resources can be paginated with the **page** and **limit** filters. For example, to get the second page of the feedbacks with 5 feedbacks per page :

.. code-block:: bash

    POST /feedbacks?page=2&limit=5

By default, *page* is equal to 1 and *limit* to 10. Thus, the endpoint

.. code-block:: bash

    POST /feedbacks

returns the first 10 feedbacks.

When a collection is returned, the response will contain informations and links to browse the pages of that collection. Below an example (partial) of a list of feedbacks.

.. code-block:: json

    {
      "page": 2,
      "limit": 10,
      "pages": 8,
      "total": 72,
      "_links": {
        "self": {
          "href": "/feedbacks?page=2&limit=10"
        },
        "first": {
          "href": "/feedbacks?page=1&limit=10"
        },
        "last": {
          "href": "/feedbacks?page=8&limit=10"
        },
        "next": {
          "href": "/feedbacks?page=3&limit=10"
        },
        "previous": {
          "href": "/feedbacks?page=1&limit=10"
        }
      }
    }

In the future, we won't precise every time that you may paginate with the *page* et *limit* filters, those are the same for every endpoint returning a collection.

.. _technical-patch:

Resource modification
---------------------

In the Keyclic API, resource modification is made with the `PATCH <https://tools.ietf.org/html/rfc5789>`_ method. Unlike the `PUT <https://tools.ietf.org/html/rfc7231#section-4.3.4>`_ method, `PATCH <https://tools.ietf.org/html/rfc5789>`_ allows to modify a single or some properties of a resource without sending every property of the modified resource.

Here is an example to change the property *billingEmailAddress* of an organization :

.. code-block:: bash

    PATCH /organizations/{organization}

.. code-block:: json

    {
		    "billingEmailAddress": "test@test.com"
	}

.. _technical-errors:

Errors
------

Every error send a code `4xx <https://tools.ietf.org/html/rfc7231#section-6.5>`_ representing the type of error.

When an code `400 <https://tools.ietf.org/html/rfc7231#section-6.5.1>`_ (Bad Request) is returned, the reasons are sent.

Errors follow the format `vdn.error <https://github.com/blongden/vnd.error>`_.

The following example displays a validation error.

.. code-block:: json

        {
           "@context":"https://github.com/blongden/vnd.error",
           "@type":"ValidationError",
           "message":"Validation failed.",
           "total":1,
           "_embedded":{
              "errors":[
                 {
                    "@context":"https://github.com/blongden/vnd.error",
                    "@type":"Error",
                    "message":"Cette valeur ne doit pas \u00eatre vide.",
                    "path":"reporter"
                 }
              ]
           }
        }

The field *path* indicates which property triggered the error (here: reporter), and the field *message* explains the error.

.. _technical-states:

State change
------------

Several resources of the API possess a life cycle and a state for a given moment. Those resources are feedbacks, reports and operations.

For these resources, the state is always indicated in the response with the field *state*, and the next possible actions to change this state are displayed in the parameter *stateTransitions*. Example :

.. code-block:: bash

    GET reports/{report}

Response (partial) :

.. code-block:: json

    {
      "type": "Report",
      "id": "cb7118b5-a821-4cf2-9475-0c0d0efdb8d0",
      "state": "NEW",
      "_embedded": {
        "stateTransitions": [
          "accept",
          "refuse"
        ]
      }
    }

In the example above, the report has a state NEW and the possible actions on its state are *accept* and *refuse*.

Actions on the state of a resource is made through the PATCH method, with the path and the new value.

For example, to accept a report :

.. code-block:: bash

    PATCH /reports/{report}/state

.. code-block:: json

    {
		    "transition": "accept"
    }

This request will send the following response :

.. code-block:: json

    {
      "type": "Report",
      "id": "32219286-528a-4f97-b81e-fe7a8cb85707",
      "state": "ACCEPTED",
      "_embedded": {
        "stateTransitions": [
          "refuse",
          "hold",
          "progress"
        ]
      }
    }

The report's state is now ACCEPTED, and the next actions are *refuse*, *hold* and *progress*.

Actions and states for each kind of resource are described in the appropriate sections of the documentation.
