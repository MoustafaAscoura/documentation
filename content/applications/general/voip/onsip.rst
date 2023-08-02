====================================
Use VoIP services in Odoo with OnSIP
====================================

Introduction
============

Odoo VoIP can be set up to work together with `OnSIP <https://www.onsip.com/>`_. In this case, the
installation and setup of an Asterisk server is not necessary as the whole infrastructure is hosted
and managed by OnSIP.

An account is needed with OnSIP to use this service. Before doing so, make sure that the company's
home area and the areas that will be called to are covered by OnSIP services. After opening an OnSIP
account, follow the configuration procedure below to configure on an Odoo database.

Configuration
=============

First, go to Apps and install the module *VoIP OnSIP*.

.. tip::
   Clear out the search bar and type in `onsip`. The OnSIP module will appear.

.. image:: onsip/install-onsip.png
   :align: center
   :alt: View of Onsip app in the app search results.

Odoo VoIP setting
-----------------

Following the module installation, go to :menuselection:`Settings --> General Settings`. In the
:menuselection:`Integrations -- > Asterisk (VoIP)` section, fill in the 3 fields:

- :guilabel:`OnSIP Domain` is the domain that was assigned when creating an account on
  `OnSIP <https://www.onsip.com/>`_.
- :guilabel:`WebSocket` = `wss://edge.sip.onsip.com`
- :guilabel:`Mode` = :guilabel:`Production`

.. image:: onsip/asterisk-setting.png
   :align: center
   :alt: VoIP configuration settings in Odoo Settings app.

.. tip::
   To access the OnSIP domain, navigate to `OnSIP <https://www.onsip.com/>`_ and log in. An
   administrative dahsboard will appear. In the left menu, click on :guilabel:`Users` and then
   select any user. By default the user will open on the :guilabel:`User Info` tab. Click on the
   :guilabel:`Phone Settings` tab to reveal  OnSIP configuration credentials. In the first column,
   last in the list of credentials, is :guilabel:`Domain`.

   .. image:: onsip/domain-setting.png
      :align: center
      :alt: Domain setting revealed (highlighted) on administrative panel of OnSIP management
            console.

Odoo user setting
-----------------

Next, the user will need to be setup in Odoo. Every user that will be associated with an OnSIP User
must also be configured in the Odoo user's settings/preferences.

First, navigate to :menuselection:`Settings --> Manage Users --> Select the User`. Once on the user
that the OnSIP account should be configured with, click on the :guilabel:`Preferences` tab and
scroll to :guilabel:`VoIP Configuration`. In this section are the fields that need to be filled in
with On SIP credentials.

.. tip::
   To access the OnSIP credentials, navigate to `OnSIP <https://www.onsip.com/>`_ and log in. An
   administrative dashboard will appear. In the left menu, click on :guilabel:`Users` and then
   select the user. By default the user will open on the :guilabel:`User Info` tab. Click on the
   :guilabel:`Phone Settings` tab to reveal  OnSIP configuration credentials. In the first column,
   last in the list of credentials.

Fill in the following fields with the associated credentials listed below:

- :guilabel:`SIP Login` / :guilabel:`Browser's Extension` = OnSIP :guilabel:`Username`
- :guilabel:`OnSIP authorization User` = OnSIP :guilabel:`Auth Username`
- :guilabel:`SIP Password` = OnSIP :guilabel:`SIP Password`
- :guilabel:`Handset Extension` = OnSIP :guilabel:`Ext.` (extension without the `x`)

.. image:: onsip/onsip-creds.png
   :align: center
   :alt: Onsip user credentials with username, auth username, SIP password, and extension
         highlighted.

.. tip::
   The OnSIP extension can be found in the :guilabel:`User` banner line above the tabs.

Once these steps are complete, and the work is saved, Odoo users can make phone calls by clicking
:guilabel:`📞 (phone)` icon  in the top right corner of Odoo.

.. seealso::
   Additional setup and troubleshooting steps can be found on `OnSIP's knowledgebase
   <https://support.onsip.com/hc/en-us>`_.

Incoming calls
--------------

The Odoo database will also receive incoming calls that produce pop-up windows in Odoo. Click the
green :guilabel:`📞 (phone)` icon to answer the call.

   .. image:: onsip/incoming-call.png
      :align: center
      :alt: alt text

.. seealso::
   :doc:`voip_widget`

Troubleshooting
---------------

.. tip::
   If a *Missing Parameters* message apprears in the Odoo softphone, make sure to refresh the Odoo
   browserwindow and try again.

   .. image:: onsip/onsip04.png
      :align: center
      :alt: Missing parameter message in the Odoo VoIP widget.

.. tip::
   If an *Incorrect Number* message appears in the Odoo softphone, make sure to use the
   international format for the number. This means leading with the :guilabel:`+ (plus)` sign
   followed by the international country code.

   A country code is a locator code that allows access to the desired country's phone system. The
   country code is dialed first, prior to the target number. Each country in the world has its own
   specific country code.\

    E.g.: `+16506913277` (where `+1` is the international prefix for the United States).

   For a list of comprehensive country codes, visit: `https://countrycode.org
   <https://countrycode.org>`_.

   .. image:: onsip/onsip05.png
      :align: center
      :alt: Incorrect number message populated in the Odoo VoIP widget.

OnSIP on Your Cell Phone
========================

In order to make and receive phone calls when the user is not in front of Odoo on their computer, A
softphone app on a mobile phone can be used in parallel with Odoo VoIP. This is useful for
on-the-go calls, but also to make sure to hear incoming calls, or simply for convenience. Any SIP
softphone will work.

.. seealso::
   :doc:`devices_integrations`

Grandstream Wave
----------------

.. important::
   A Grandstream Wave account is necessary to utilize the following integration. This includes a
   networked PBX hardware integration from Grandstream (e.g. Grandstream UCM63XX series IP PBX).

On Android and iOS devices, OnSIP has been successfully tested with `Grandstream Wave
<https://www.grandstream.com/products/ucm6300-ecosystem/product/wave>`_. It is available on `Apple
iOS <https://apps.apple.com/us/app/grandstream-wave/id1523254549>`_ and `Android
<https://play.google.com/store/apps/details?id=com.grandstream.ucm&pcampaignid=web_share>`_
platforms. First sign into the Grandstream Wave account using the *IP address*, *extension number*,
and *password*. Then create an account, and select `OnSIP` in the list of carriers. Configure it as
follows:

- :guilabel:`Account name` = OnSIP
- :guilabel:`SIP Server` = OnSIP :guilabel:`Domain`
- :guilabel:`SIP User ID` = OnSIP :guilabel:`Username`
- :guilabel:`SIP Authentication ID` = OnSIP :guilabel:`Auth Username`
- :guilabel:`Password` = OnSIP :guilabel:`SIP Password`

Aside from initiating calls from Grandstream Wave on a mobile phone, calls can also be initiated by
clicking phone numbers in a browser on the computer. This will make Grandstream Wave ring and route
the call via the phone to the other party. This approach is useful to avoid wasting time dialing
phone numbers. In order to do so, the Chrome extension is needed `OnSIP Call Assistant
<https://chrome.google.com/webstore/detail/onsip-call-assistant/pceelmncccldedfkcgjkpemakjbapnpg>`_.

.. warning::
   The downside of using a softphone on the mobile phone is that your calls will not be logged in
   Odoo, as the softphone acts as an independent, separate app.

.. seealso::
   Additional setup and troubleshooting steps can be found on Grandstream's knowledgebase. Visit
   Grandstream's knowledgebase
   <https://www.onsip.com/voip-resources/voip-reviews/grandstream-waves>`_.


