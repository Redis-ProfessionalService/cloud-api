Usage
=====

You can access and use the API endpoint URI (https://api.redislabs.com/v1) with any of the following tools:

- The Swagger user interface
- The cURL HTTP client
- An HTTP client in any programming language

The following examples use the cURL utility. You can use any REST client to work with the Redis Cloud REST API.

Users
-----

You can use the Redis Enterprise Cloud REST API to update, delete and list users.

List Users
^^^^^^^^^^

:guilabel:`GET` https://api.redislabs.com/v1/users

To retrieve list of users of current account.

**API call**

.. code-block:: shell

  curl -s -X GET "https://api.redislabs.com/v1/users" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

**Response body**

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

:guilabel:`GET` https://api.redislabs.com/v1/users/{userId}

To retrieve a user's detail by its ID.

**API call**

.. code-block:: shell

  curl -s -X GET "https://api.redislabs.com/v1/users/$USER_ID" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

**Response body**

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


Update User
^^^^^^^^^^^

:guilabel:`PUT` https://api.redislabs.com/v1/users/{userId}

To update a user's detail by its ID.

**Request body**

.. code-block:: json

  {
    "name": "My new user name",
    "role": "Owner"
  }

**API call**

.. code-block:: shell

  curl -s -X PUT "https://api.redislabs.com/v1/users/$USER_ID" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY" \
       -d '{
         "name": "My new user name",
         "role": "Owner"
       }'

**Response body**

.. code-block:: json

  {
    "taskId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "commandType": "string",
    "status": "initialized",
    "description": "string",
    "timestamp": "2023-08-04T13:22:06.585Z",
    "response": {
      "resourceId": 0,
      "additionalResourceId": 0,
      "resource": {},
      "error": "UNAUTHORIZED",
      "additionalInfo": "string"
    },
    "links": [
      {
        "additionalProp1": {},
        "additionalProp2": {},
        "additionalProp3": {}
      }
    ]
  }


Delete User
^^^^^^^^^^^

:guilabel:`DELETE` https://api.redislabs.com/v1/users/{userId}

To delete a user by its ID from current account.

**API call**

.. code-block:: shell

  curl -s -X DELETE "https://api.redislabs.com/v1/users/$USER_ID" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

**Response body**

.. code-block:: json

  {
    "taskId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "commandType": "string",
    "status": "initialized",
    "description": "string",
    "timestamp": "2023-08-04T13:24:06.944Z",
    "response": {
      "resourceId": 0,
      "additionalResourceId": 0,
      "resource": {},
      "error": "UNAUTHORIZED",
      "additionalInfo": "string"
    },
    "links": [
      {
        "additionalProp1": {},
        "additionalProp2": {},
        "additionalProp3": {}
      }
    ]
  }

ACL
---

Data and operations related to access control list.

Redis Rules
^^^^^^^^^^^

Information on current account's ACL users

List Redis Rules
++++++++++++++++

:guilabel:`GET` https://api.redislabs.com/v1/acl/redisRules

To retrieve list of ACL redis rules.

**API call**

.. code-block:: shell

  curl -s -X GET "https://api.redislabs.com/v1/acl/redisRules" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

**Response body**

.. code-block:: json

  {
    "accountId": 1001,
    "redisRules": [
      {
        "id": 7,
        "name": "Full-Access",
        "acl": "+@all  ~*",
        "isDefault": true,
        "status": "active"
      },
      {
        "id": 8,
        "name": "Read-Write",
        "acl": "+@all -@dangerous ~*",
        "isDefault": true,
        "status": "active"
      },
      {
        "id": 9,
        "name": "Read-Only",
        "acl": "+@read ~*",
        "isDefault": true,
        "status": "active"
      }
    ]
  }

Create Redis Rule
+++++++++++++++++

:guilabel:`POST` https://api.redislabs.com/v1/acl/redisRules

To create a redis rule ACL.

**API call**

.. code-block:: shell

  curl -s -X POST "https://api.redislabs.com/v1/acl/redisRules" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

**Response body**

.. code-block:: json

  {
    "taskId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "commandType": "string",
    "status": "initialized",
    "description": "string",
    "timestamp": "2023-08-04T14:45:17.256Z",
    "response": {
      "resourceId": 0,
      "additionalResourceId": 0,
      "resource": {},
      "error": "UNAUTHORIZED",
      "additionalInfo": "string"
    },
    "links": [
      {
        "additionalProp1": {},
        "additionalProp2": {},
        "additionalProp3": {}
      }
    ]
  }

Update Redis Rule
+++++++++++++++++

:guilabel:`PUT` https://api.redislabs.com/v1/acl/redisRules/{aclRedisRuleId}

To update an ACL redis rule.

**Request body**

.. code-block:: json

  {
    "name": "ACL-rule-example",
    "redisRule": "string"
  }

**API call**

.. code-block:: shell

  curl -s -X POST "https://api.redislabs.com/v1/acl/redisRules/$RULE_ID" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY" \
       -d '{
         "name": "ACL-rule-example",
         "redisRule": "string"
       }'

**Response body**

.. code-block:: json

  {
    "taskId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "commandType": "string",
    "status": "initialized",
    "description": "string",
    "timestamp": "2023-08-04T14:45:17.256Z",
    "response": {
      "resourceId": 0,
      "additionalResourceId": 0,
      "resource": {},
      "error": "UNAUTHORIZED",
      "additionalInfo": "string"
    },
    "links": [
      {
        "additionalProp1": {},
        "additionalProp2": {},
        "additionalProp3": {}
      }
    ]
  }


Delete Redis Rule
+++++++++++++++++

:guilabel:`DELETE` https://api.redislabs.com/v1/acl/redisRules/{aclRedisRuleId}

To update an ACL redis rule.

**API call**

.. code-block:: shell

  curl -s -X POST "https://api.redislabs.com/v1/acl/redisRules/$RULE_ID" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

**Response body**

.. code-block:: json

  {
    "taskId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "commandType": "string",
    "status": "initialized",
    "description": "string",
    "timestamp": "2023-08-04T16:13:29.868Z",
    "response": {
      "resourceId": 0,
      "additionalResourceId": 0,
      "resource": {},
      "error": "UNAUTHORIZED",
      "additionalInfo": "string"
    },
    "links": [
      {
        "additionalProp1": {},
        "additionalProp2": {},
        "additionalProp3": {}
      }
    ]
  }

Roles
^^^^^

Information on current account's ACL roles

List Roles
++++++++++

:guilabel:`GET` https://api.redislabs.com/v1/acl/roles

To retrieve list of ACL roles.

**API call**

.. code-block:: shell

  curl -s -X GET "https://api.redislabs.com/v1/acl/roles" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

**Response body**

.. code-block:: json

  {
    "accountId": 1001,
    "roles": [
      {
        "id": 395,
        "name": "role-name",
        "redisRules": [
          {
            "ruleId": 7,
            "ruleName": "Full-Access",
            "databases": [
              {
                "subscriptionId": 126,
                "databaseId": 1,
                "databaseName": "DB-RCP-2-81-7"
              }
            ]
          }
        ],
        "users": [],
        "status": "error"
      }
    ]
  }

Create Role
+++++++++++

:guilabel:`POST` https://api.redislabs.com/v1/acl/roles

To create a new ACL role.

**Request body**

.. code-block:: json

  {
    "name": "ACL-role-example",
    "redisRules": [
      {
        "ruleName": "Read-Only",
        "databases": [
          {
            "subscriptionId": 0,
            "databaseId": 0,
            "regions": []
          }
        ]
      }
    ]
  }

**API call**

.. code-block:: shell

  curl -s -X POST "https://api.redislabs.com/v1/acl/roles" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY" \
       -d '{
         "name": "ACL-role-example",
         "redisRules": [
           {
             "ruleName": "Read-Only",
             "databases": [
               {
                 "subscriptionId": 0,
                 "databaseId": 0,
                 "regions": []
               }
             ]
           }
         ]
       }'

**Response body**

.. code-block:: json

  {
    "taskId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "commandType": "string",
    "status": "initialized",
    "description": "string",
    "timestamp": "2023-08-04T16:24:12.789Z",
    "response": {
      "resourceId": 0,
      "additionalResourceId": 0,
      "resource": {},
      "error": "UNAUTHORIZED",
      "additionalInfo": "string"
    },
    "links": [
      {
        "additionalProp1": {},
        "additionalProp2": {},
        "additionalProp3": {}
      }
    ]
  }

Update Role
+++++++++++

:guilabel:`PUT` https://api.redislabs.com/v1/acl/roles/{aclRoleId}

To update an ACL role.

**Request body**

.. code-block:: json

  {
    "name": "ACL-role-example",
    "redisRules": [
      {
        "ruleName": "Read-Only",
        "databases": [
          {
            "subscriptionId": 0,
            "databaseId": 0,
            "regions": []
          }
        ]
      }
    ]
  }

**API call**

.. code-block:: shell

  curl -s -X POST "https://api.redislabs.com/v1/acl/roles/$ROLE_ID" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY" \
       -d '{
         "name": "ACL-role-example",
         "redisRules": [
           {
             "ruleName": "Read-Only",
             "databases": [
               {
                 "subscriptionId": 0,
                 "databaseId": 0,
                 "regions": []
               }
             ]
           }
         ]
       }'

**Response body**

.. code-block:: json

  {
    "taskId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "commandType": "string",
    "status": "initialized",
    "description": "string",
    "timestamp": "2023-08-04T16:32:47.628Z",
    "response": {
      "resourceId": 0,
      "additionalResourceId": 0,
      "resource": {},
      "error": "UNAUTHORIZED",
      "additionalInfo": "string"
    },
    "links": [
      {
        "additionalProp1": {},
        "additionalProp2": {},
        "additionalProp3": {}
      }
    ]
  }


Delete Redis Rule
+++++++++++++++++

:guilabel:`DELETE` https://api.redislabs.com/v1/acl/roles/{aclRoleId}

To delete an ACL role.

**API call**

.. code-block:: shell

  curl -s -X POST "https://api.redislabs.com/v1/acl/roles/$ROLE_ID" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"

**Response body**

.. code-block:: json

  {
    "taskId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "commandType": "string",
    "status": "initialized",
    "description": "string",
    "timestamp": "2023-08-04T16:34:07.530Z",
    "response": {
      "resourceId": 0,
      "additionalResourceId": 0,
      "resource": {},
      "error": "UNAUTHORIZED",
      "additionalInfo": "string"
    },
    "links": [
      {
        "additionalProp1": {},
        "additionalProp2": {},
        "additionalProp3": {}
      }
    ]
  }
