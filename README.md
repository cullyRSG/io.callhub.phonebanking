(prelude--this code as it stands from CallHub.io doesn't work. Not tryna step on their toes by modifying this, but I want this extension working.)

CallHub Phonebanking Extension for CiviCRM
==========================================

[CallHub](https://callhub.io) is a hosted phone banking service that enables your staff to talk with your contacts over the phone banking campaign and store notes about the call. This extension integrates CallHub with CiviCRM by posting call dispositions and notes as CiviCRM activities attached to the contact record and assigned to the relevant staff person's record.

Installation
============

1. Create a CallHub account [here](https://app.callhub.io/accounts/register/)
2. CiviCRM should have set a CiviCRM Extensions Directory at Administer >> System Settings >> Directories.  This is likely "\[civicrm.files\]/ext/". 
3. CiviCRM  should have set an Extension Resource URL at Administer >> System Settings >> Resource URLs. This is very likely identical to your Extensions Directory.
4. Create a contact in CiviCRM that will be used to synchronize information.
    a. Create a new contact by going to Contacts >> New Individual. 
    b. Name the contact something like "Callhub.io API"
    c. Generate an API key. There is an extension for this, otherwise it can be done with the API Explorer.
    d. Ensure that the user has permissions for "Administer CiviCRM" and "Access AJAX API". 
5. Download this extension (unzipped) to the extensions directory.
    a. If shell is open to your Extensions Director, execute *git clone https://<INSERT_GIT_URL>.git*
6. Navigate to Administer >> System Settings >> Manage Extensions and beside CallHub Phone Banking, click Install.
7. On the [integrations page](https://app.callhub.io/dashboard/apps/) in your CallHub account, click on “Connect to your CiviCRM site”. There are 3 things you need to connect:

    a. Site URL. This should be the full path to extern/rest.php. For example, http://<YOUR_SITE_NAME>/civicrm/sites/all/modules/civicrm/extern/rest.php

    b. Site Key. The unique key that identifies your CiviCRM installation.

    c. API Key. The API key created in step 4 above.

8. After CiviCRM is connected, CallHub will import groups, events and campaigns from CiviCRM. 
9. Setup a [phone banking campaign](https://app.callhub.io/power_campaign/add/). You'll be able to choose the CiviCRM campaign and activity type that gets logged in CiviCRM.
10. The activities synced from CallHub have the following attributes:

    a. Notes: The notes include a link to audio recording, the actual notes taken by your staff and the Call Disposition.

    b. date and time: activities always happen at a certain point in time

    c. added by: the staff who added this activity

    d. with contact(s): the contacts in your database that are the subject of the activity.
