Cancel payment refund
=====================

.. api-name:: Refunds API
   :version: 2

.. endpoint::
   :method: DELETE
   :url: https://api.mollie.com/v2/payments/*paymentId*/refunds/*id*

.. authentication::
   :api_keys: true
   :organization_access_tokens: true
   :oauth: true

For certain payment methods, like iDEAL, the underlying banking system will delay refunds until the next day. Until that
time, refunds may be canceled manually in your Mollie account, or automatically by using this endpoint.

The refund can only be canceled while the refund's ``status`` field is either ``queued`` or ``pending``. See
:doc:`Get payment refund </reference/v2/refunds-api/get-refund>` for more information.

Parameters
----------
Replace ``paymentId`` in the endpoint URL by the payment's ID, and replace ``id`` by the refund's ID. For example:
``/v2/payments/tr_7UhSN1zuXS/refunds/re_4qqhO89gsT``.

Mollie Connect/OAuth parameters
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If you're creating an app with :doc:`Mollie Connect/OAuth </oauth/overview>`, the ``testmode`` parameter is also
available.

.. list-table::
   :widths: auto

   * - ``testmode``

       .. type:: boolean
          :required: false

     - Set this to ``true`` to cancel a test mode refund.

Response
--------
``204 No Content``

Example
-------

.. code-block-selector::
   .. code-block:: bash
      :linenos:

      curl -X DELETE https://api.mollie.com/v2/payments/tr_WDqYK6vllg/refunds/re_4qqhO89gsT \
            -H "Authorization: Bearer test_dHar4XY7LxsDOtmnkVtjNVWXLSlXsM"

   .. code-block:: php
      :linenos:

      <?php
      $mollie = new \Mollie\Api\MollieApiClient();
      $mollie->setApiKey("test_dHar4XY7LxsDOtmnkVtjNVWXLSlXsM");

      $refund = $mollie->payments->get("tr_WDqYK6vllg")->getRefund("re_4qqhO89gsT");
      $canceledRefund = $refund->cancel();

   .. code-block:: python
      :linenos:

      from mollie.api.client import Client

      mollie_client = Client()
      mollie_client.set_api_key('test_dHar4XY7LxsDOtmnkVtjNVWXLSlXsM')

      payment = mollie_client.payments.get('tr_WDqYK6vllg')
      refund = mollie_client.payment_refunds.on(payment).delete('re_4qqhO89gsT')

Response
^^^^^^^^
.. code-block:: http
   :linenos:

   HTTP/1.1 204 No Content
