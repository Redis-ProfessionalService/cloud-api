Usage
=====

You can access and use the API endpoint URI (https://api.redislabs.com/v1) with any of the following tools:

- The Swagger user interface
- The cURL HTTP client
- An HTTP client in any programming language

The following examples use the cURL utility. You can use any REST client to work with the Redis Cloud REST API.

Manage Users
------------

You can use the Redis Enterprise Cloud REST API to update, delete and list users.

List Users
^^^^^^^^^^

Endpoint: https://api.redislabs.com/v1/users

To retrieve list of users of current account.

.. code-block:: shell

  curl -s -X GET "https://api.redislabs.com/v1/users" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

Example response:

.. code-block:: json

  {
    "account": 1001,
    "users": [
      {
        "id": 60192,
        "name": "Clifford O'neill",
        "email": "clifford.mail@gmail.com",
        "role": "Viewer",
        "userType": "Local",
        "hasApiKey": false,
        "options": {
          "billing": false,
          "emailAlerts": false,
          "operationalEmails": false,
          "mfaEnabled": false
        }
      }
    ]
  }

Get User by ID
^^^^^^^^^^^^^^

Endpoint: https://api.redislabs.com/v1/users/{userId}

To retrieve a user's detail by its ID.

.. code-block:: shell

  curl -s -X GET "https://api.redislabs.com/v1/users/60192" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

Example response:

.. code-block:: json

  {
    "id": 60192,
    "name": "Clifford O'neill",
    "email": "clifford.mail@gmail.com",
    "role": "Viewer",
    "userType": "Local",
    "hasApiKey": false,
    "options": {
      "billing": false,
      "emailAlerts": false,
      "operationalEmails": false,
      "mfaEnabled": false
    }
  }
