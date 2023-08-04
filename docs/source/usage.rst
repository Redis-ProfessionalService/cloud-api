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

To retrieve list of users of current account.

.. code-block:: shell

  curl -s -X GET "https://$HOST/logs" \
       -H "accept: application/json" \
       -H "x-api-key: $ACCOUNT_KEY" \
       -H "x-api-secret-key: $SECRET_KEY"


.. _installation:

Installation
------------

To use Lumache, first install it using pip:

.. code-block:: console

   (.venv) $ pip install lumache

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

