.. _v1/keys-reset:

Profiles API v1: Reset API key
==============================
``POST`` ``https://api.mollie.com/v1/profiles/*profileId*/apikeys/*mode*``

Authentication: :ref:`OAuth access tokens <oauth/overview>`

You can reset the API keys, for instance when you feel your keys may have been compromised. Please note the old API key
can no longer be used once it has been reset.

Parameters
----------
Replace ``id`` in the endpoint URL by the payment profile's ID, and replace ``mode`` by ``live`` or ``test``. For
example: ``/v1/profiles/pfl_v9hTwCvYqw/apikeys/live``.

Response
--------
``200`` ``application/json; charset=utf-8``

.. list-table::
   :widths: auto

   * - | ``resource``
       | string
     - Indicates the response contains an API key object. Will always contain ``profile_api_key`` for this endpoint.

   * - | ``id``
       | string
     - The (unchanged) API key's identifier.

       Possible values: ``live`` ``test``

   * - | ``key``
       | string
     - The newly generated API key, which immediately replaces the previous API key.

   * - | ``createdDatetime``
       | datetime
     - The API key's new date and time of creation, in `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_ format.

Example
-------

Request
^^^^^^^
.. code-block:: bash

   curl -X POST https://api.mollie.com/v1/profiles/pfl_v9hTwCvYqw/apikeys/live \
       -H "Authorization: Bearer access_Wwvu7egPcJLLJ9Kb7J632x8wJ2zMeJ"

Response
^^^^^^^^
.. code-block:: http

   HTTP/1.1 200 OK
   Content-Type: application/json; charset=utf-8

   {
       "resource": "profile_api_key",
       "id": "live",
       "key": "live_QW7fVwCKzZZkxUsVwt39R2egTEf5Db",
       "createdDatetime": "2018-03-17T01:47:49.0Z"
   }