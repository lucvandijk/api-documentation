Changelog
~~~~~~~~~
Occasionally, we will add new resources, new fields, or new possible values to existing fields to the v2 Mollie API. All
changes are documented here.

March 2019
==========

Thursday, 21th
--------------

- Added the "Nationale Golfbon" and "Sport & Fit Cadeau" as giftcard issuers.

Tuesday, 12th
-------------

- Added the new payment method `Przelewy24 <https://www.mollie.com/en/payments/przelewy24>`_ (``przelewy24``).

February 2019
=============

Thursday, 28th
--------------

- Added profile website URL validation to the :doc:`Create profile </reference/v2/profiles-api/create-profile>`
  endpoint.
- Added profile website URL validation to the
  :doc:`Submit onboarding data </reference/v2/onboarding-api/submit-onboarding-data>` endpoint.


Monday, 25th
------------

- Updated the list of available profile :doc:`merchant category codes </reference/v2/profiles-api/create-profile>`

Thursday, 21st
--------------
- The ``changePaymentState`` link in the :doc:`Payments API </reference/v2/payments-api/get-payment>` is now available
  for paid payments in test mode. This allows you to create refunds and chargebacks for test mode payments from the
  checkout screen.

January 2019
============

Tuesday, 29th
-------------

- Added a new API for submitting onboarding data of a merchant. This data will be prefilled in the onboarding forms of
  the merchant. You will need the new OAuth scope ``onboarding.write`` to submit data. For details, see the
  :doc:`Submit onboarding data API </reference/v2/onboarding-api/submit-onboarding-data>`.

Tuesday, 22th
-------------

- It is now possible to also update the ``orderNumber`` of an order, see :doc:`Update order </reference/v2/orders-api/update-order>`.

Thursday, 17th
--------------

- It is now possible to also update the ``quantity``, ``unitPrice``, ``discountAmount``, ``totalAmount``, ``vatAmount``
  and ``vatRate`` of the order line, see :doc:`Update order line </reference/v2/orders-api/update-orderline>`.

Monday, 14th
-------------

- We've added the ``metadata`` field to the order line entity. You can now store up to 1Kb of information with your
  order line, see :doc:`Create order </reference/v2/orders-api/create-order>`.

- Added a new endpoint to retrieve all payment methods Mollie is offering to an organization.
  See :doc:`List all payment methods  </reference/v2/methods-api/list-all-methods>` for details.

Thursday, 3th
-------------

- Added a new API for getting the onboarding status of a merchant. You will need the new OAuth scope ``onboarding.read``
  to access the data. For details, see the :doc:`Onboarding API </reference/v2/onboarding-api/get-onboarding-status>`.

December 2018
=============

Thursday, 20th
--------------

- Added the ``locale`` field to organization details. This represents the locale that the merchant has set in their
  Mollie Dashboard.

Tuesday, 18th
-------------

- Added a new endpoint to update order lines. For details, see: :doc:`Update order line </reference/v2/orders-api/update-orderline>`

Friday, 14th
------------

- The expiry period for `Belfius Pay Button <https://www.mollie.com/en/payments/belfius>`_ has been decreased from 1 day to 1 hour.

Thursday, 13th
--------------

- It is now possible to create (another) payment for an order via the
  :doc:`Create order payment endpoint </reference/v2/orders-api/create-order-payment>` on the Orders API.
- We are now offering webhooks for order payments. Please note that when the status of the payment becomes ``paid`` we
  are calling your order webhook instead. See the :doc:`Orders API </reference/v2/orders-api/create-order>` for more info.

Monday, 10th
------------

- Enabling and disabling payment methods via the API is now possible via the
  :doc:`Profiles API </reference/v2/profiles-api/enable-method>`.

Friday, 7th
-----------

- Refunds for Pay Later and Slice it can now be created via the :doc:`Payments Refunds API
  </reference/v2/refunds-api/create-refund>`. This allows refunding of arbitrary amounts.

Tuesday, 4th
------------

- It is now possible to get the pricing of the payment methods that are active on the payment profile. Add the
  ``include=pricing`` parameter to the :doc:`Methods API </reference/v2/methods-api/list-methods>` to get the pricing
  object in your response.

November 2018
=============

Wednesday, 15th
---------------

- It is now possible to pass an ``amount`` when partially shipping, canceling or refunding order lines. This is
  necessary for order lines that have a non-zero ``discountAmount``.

  Before, it was not possible to partially ship, cancel or refund such order lines.

Monday, 12th
------------

- Subscriptions in test mode will now be canceled automatically after 10 charges.

Thursday, 8th
-------------

- It's now possible to refund SEPA Direct Debit payments

Wednesday, 7th
--------------

- Moved the ``organizationName`` field in the ``shippingAddress`` and ``billingAddress`` objects.

Monday, 5th
-----------

- Added referral-functionality for Mollie Partners to the Connect API. See the :doc:`documentation </oauth/overview>`
  for more info.

Thursday, 1st
-------------

- The maximum amount for SOFORT Banking payments has been increased from €5,000 to €50,000.

October 2018
============

Monday, 29th
------------

- Added ``organizationName`` field for orders, so from now a customer can specify the organization name if they buy
  something for business purposes.

Thursday, 25th
--------------

- We now accept the use of an underscore ``_`` in Redirect- and Webhook-URLs.
- A :doc:`guide </guides/testing>` has been added explaining how to test your integration of the Mollie API.
- Added the ``changePaymentState`` link to the :doc:`Payments API </reference/v2/payments-api/get-payment>`.
  It allows you to set the final payment state for test mode recurring payments.

Wednesday, 24th
---------------

- Added the ``timesRemaining`` field to the :doc:`Subscriptions API </reference/v2/subscriptions-api/get-subscription>`
  to see how many charges are left for completing the subscription.
- Consumer IBANs of Bancontact payments will now always be shared via the API.
- Added :doc:`Organization access tokens </guides/authentication>` as an authentication method.

Friday, 19th
--------------

- PayPal refund period has been increased from 60 to 180 days.

Wednesday, 17th
---------------
- The ``method`` field on the :doc:`Create Payment </reference/v2/payments-api/create-payment>` and
  :doc:`Create Order </reference/v2/orders-api/create-order>` now also accepts an array of methods. By doing so you can
  select which methods to show on the payment method selection screen. For example, you can use this functionality to
  only show payment methods from a specific country to your customer.


Monday, 15th
------------
- It is now possible to specify a URL with a custom URI scheme as ``redirectUrl`` parameter. Previously, only the *HTTP*
  and *HTTPS* schemes were allowed. You can for example immediately redirect the customer back to your mobile app after
  completing a payment, by setting the ``redirectUrl`` to your own App Scheme, like ``my-app://payment-return``.

Friday, 12th
------------
- Added new category codes ``5533`` ``5641`` ``5651`` ``5732`` ``5735`` ``5815`` ``5944`` ``5977`` ``7999``
  to the :doc:`Create Profile </reference/v2/profiles-api/create-profile>` and
  :doc:`Update Profile </reference/v2/profiles-api/update-profile>` endpoints.

Friday, 5th
------------
- We have added the ``mandateId`` field in subscriptions. This makes it possible to sure a specific mandate for a
  subscription. For details, see the :doc:`Subscriptions API </reference/v2/subscriptions-api/create-subscription>`.

Tuesday, 2nd
------------
- We have removed the dedicated French bank account for bank transfer payments. Your customers can use our Dutch
  bank account to finish the payment.

- Added the new payment status ``authorized`` for payments that still require a capture to receive the money. Currently,
  this status is only used for payment methods `Klarna Pay later <https://www.mollie.com/payments/klarna-pay-later>`_
  and `Klarna Slice it <https://www.mollie.com/payments/klarna-slice-it>`_. Because payments with these payment methods
  can only be created with the :doc:`Orders API </reference/v2/orders-api/create-order>`, there is no change required in
  existing implementations of the Payments API.

  The new status is especially useful to give a meaningful representation when listing all payments.

September 2018
==============

Friday, 28th
------------
- Bitcoin payments can now be created in non-EUR currencies. Your account will be settled in EUR.

Tuesday, 25th
-------------
- Added the ``nextPaymentDate`` field in subscriptions to see when the next payment should be initiated. For details,
  see the :doc:`Subscriptions API </reference/v2/subscriptions-api/get-subscription>`.

Thursday, 20th
--------------
- Added a new endpoint get all payments for a specific customer subscription. For details, see:
  :doc:`List subscription payments </reference/v2/subscriptions-api/list-subscriptions-payments>`

- Added ``amountCaptured`` and ``authorizedAt`` to the payment object.

Tuesday, 18th
-------------
- Added the ``metadata`` field to the :doc:`Subscriptions API </reference/v2/subscriptions-api/get-subscription>`. This
  makes it possible to, for example, link a plan to a subscription.

Monday, 17th
------------
- Added a new endpoint for partners to get all connected organizations. See the Reseller API Docs for more information.

Wednesday, 12th
---------------
- Added the :doc:`Orders API </reference/v2/orders-api/create-order>` and the
  :doc:`Shipments API </reference/v2/shipments-api/create-shipment>`. See the
  :doc:`Orders API overview </orders/overview>` for more details on how to use these APIs.

- Added the :doc:`Captures API </reference/v2/captures-api/get-capture>`.

- The ``amount`` field in chargebacks had the wrong sign, though it was documented correctly. The API has been changed
  to use positive values for the ``amount`` field and negative values for the ``settlementAmount`` field in the
  :doc:`/reference/v2/chargebacks-api/get-chargeback` API.

- You can now use cursors to scroll through all chargebacks of a Payment using the
  :doc:`/reference/v2/chargebacks-api/list-chargebacks` API.

Tuesday, 11th
-------------

- Added the ``mode`` field to the :doc:`Mandates API </reference/v2/mandates-api/get-mandate>`. This makes it possible
  to see in which environment the mandate is created.

Monday, 10th
------------

- Added a new endpoint for retrieving the website profile of the used API key. For details, see:
  :doc:`Get current profile </reference/v2/profiles-api/get-profile-me>`

August 2018
===========

Wednesday, 1st
--------------

- The icons returned by the :doc:`Methods API </reference/v2/methods-api/list-methods>` have been updated. Note that the
  size of the icons has changed from 40x40 to 32x24. All icons are now available in SVG as well, which we advise you to
  use where possible.

July 2018
=========

Tuesday, 31st
-------------

- Test payments are no longer cleaned up after 2 weeks. Just like live payments they will never be removed.

Thursday, 19th
--------------

- The :doc:`Get Settlement </reference/v2/settlements-api/get-settlement>` endpoint now returns the ``invoiceId`` if the
  settlement has been invoiced. The invoice is also available in the ``_link`` object.

Wednesday, 11th
---------------

- Added a new endpoint for updating Subscriptions. Now you can update a subscription when needed --
  for example when your customer switches price plans.

  For details, see: :doc:`Update Subscription </reference/v2/subscriptions-api/update-subscription>`

June 2018
=========

Monday, 25th
------------

- Added the new payment methods Giropay (``giropay``) and EPS (``eps``). Note that this method may not be available on
  your account straight away. If it is not, contact our support department to get it activated for your account.

- Passing a payment description in the form of ``Order <order number>`` will now pass the order number to PayPal in the
  *Invoice reference* field which you can search.

Friday, 1st
-----------
- Added new locales ``en_US`` ``nl_NL`` ``nl_BE`` ``fr_FR`` ``fr_BE`` ``de_DE`` ``de_AT`` ``de_CH`` ``es_ES`` ``ca_ES``
  ``pt_PT`` ``it_IT`` ``nb_NO`` ``sv_SE`` ``fi_FI`` ``da_DK`` ``is_IS`` ``hu_HU`` ``pl_PL`` ``lv_LV`` and ``lt_LT`` to
  the :doc:`Create Customer </reference/v2/customers-api/create-customer>`,
  :doc:`Create Payment </reference/v2/payments-api/create-payment>`, and
  :doc:`List Methods </reference/v2/methods-api/list-methods>` endpoints to localize translations and allow for ordering
  the payment methods in the preferred order for the country.

May 2018
========

Wednesday, 9th
--------------
- Launched `Multicurrency <https://www.mollie.com/nl/features/multicurrency>`_  and the new v2 api.
