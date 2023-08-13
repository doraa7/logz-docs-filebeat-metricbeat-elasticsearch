---
layout: article
title: Single sign-on with Google Workspace
permalink: /user-guide/users/single-sign-on/google-workspace-sso.html
image: https://dytvr9ot2sszz.cloudfront.net/logz-docs/social-assets/docs-social.jpg
description: SSO with Google Workspace for Logz.io accounts
flags:
  admin: true
  logzio-plan: pro
tags:
  - sso
contributors:
  - hidan
---

Logz.io offers a quick integration for SSO with Google Workspace.


#### To set up single sign-on for Google Workspace

<div class="tasklist">

##### Request SSO access from Logz.io


Only account admins can request single sign-on access for their accounts.
{:.info-box.note}

To set up your Google Workspace SSO, you'll first need to email [help@logz.io](mailto:help@logz.io) and write that you want to set up Google Workspace SAML SSO for Logz.io.

Include these items in the message:

* Your Logz.io [account ID]({{site.baseurl}}/user-guide/accounts/finding-your-account-id.html)
* The last six characters of your [account token](https://app.logz.io/#/dashboard/settings/manage-accounts)

The Support team will respond with the connection information needed to set up your Google Workspace SSO.

##### SAML attribute mapping

Log into your [Google Workspace panel](https://admin.google.com/AdminHome).

In the sidebar, navigate to Apps > Web and mobile apps. Click on **Add app** and choose the **Add custom SAML** app option.







##### Set a custom SAML app in Google Workspace

Log into your [Google Workspace panel](https://admin.google.com/AdminHome).

In the sidebar, navigate to Apps > Web and mobile apps. Click on **Add app** and choose the **Add custom SAML** app option.

![Create SAML app](https://dytvr9ot2sszz.cloudfront.net/logz-docs/sso-providers/google/google-add-saml-app.png)

Name your application and click **Continue**. In the **Google Identity Provider details** screen, copy the **Entity ID** and download the certificate.

![Download certificate](https://dytvr9ot2sszz.cloudfront.net/logz-docs/sso-providers/google/download-certificate.png)

Continue to the next screen. Enter the ACS URL and Entity ID given to you by Logz.io support; change the Name ID format to **EMAIL**, and set the Name ID to **Basic Information > Primary email**.

![Set entity ID](https://dytvr9ot2sszz.cloudfront.net/logz-docs/sso-providers/google/service-provider.png)

Continue to the final screen. Edit the Google Directory attributes to **Basic Information - Primary email**, and set App attributes to **email**.

![Set entity ID](https://dytvr9ot2sszz.cloudfront.net/logz-docs/sso-providers/google/attribute-mapping.png)

Click on Finish to add the custom SAML app.

##### Send your SAML details to Logz.io

Draft a new [email to Support](mailto:help@logz.io), and include these items:

* Your zipped SAML Signing Certificate (from the previous step).
* Your SAML SIGN-IN URL.

When Support has received the information and created your Google Workspace + Logz.io connection, you’re done! You can start logging in to Logz.io through your Google Workspace account.


</div>

#### Google Workspace SSO groups


When [creating access groups for Google Workspace](https://support.google.com/a/answer/9050643?hl=en), you need to add a custom attribute to connect it to your Logz.io SAML application.

First, **[add a custom attribute](https://support.google.com/a/answer/6208725?hl=en)** and link it to your SAML app.

Open your SAML app, navigate to the **Add a new custom attribute** section, and add the following configuration:

* Name: groups
* Info type: Text
* Visibility: Visible to user and admin
* Number of values: Multi-value

![Set group SSO](https://dytvr9ot2sszz.cloudfront.net/logz-docs/sso-providers/google/add-custom-fields.png)

Next, configure the groups attribute to be sent across as part of the SAML login.

![Set group attribute](https://dytvr9ot2sszz.cloudfront.net/logz-docs/sso-providers/google/sent-group-sso.png)