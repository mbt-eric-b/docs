---
title: 'Migrating an MX Plan email address to an Email Pro or Exchange account'
slug: migration-email-address-to-exchange
excerpt: 'Find out how to migrate an MX Plan email address to an Email Pro or Exchange account'
section: 'Exchange account migration'
order: 1
---

**Last updated 23rd July 2021**

## Objective

OVHcloud offers several email solutions: MX Plan (stand-alone or included in a Web Hosting plan), Email Pro and Exchange. They have their own features, and can be adapted to suit a number of uses. Are your needs changing? OVHcloud offers a migration tool you can use to switch from one solution to another.

**Find out how to migrate an MX Plan email address to an Email Pro or Exchange account.**

## Requirements

- an MX Plan email address (via the MX Plan solution or included in an OVHcloud [Web Hosting plan](https://www.ovh.ie/web-hosting/){.external})
- an [Exchange](https://www.ovh.ie/emails/hosted-exchange/){.external} or [Email Pro](https://www.ovh.ie/emails/email-pro/){.external} service with at least one unconfigured account (which will appear as “@configureme.me”).
- **no redirections set on the MX Plan email address you want to migrate**
- access to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie){.external}

## Instructions

### Step 1: Defining your project

Email Pro and Exchange solutions have a common feature base. However, there are differences in use cases. By choosing an Exchange address, you get all the collaborative features, such as calendars and contact synchronisation. The Email Pro solution offers a few advanced features as well, but they are limited to webmail use only.

It is important to find out to which solution you would like to migrate your MX Plan email addresses to before initiating the process. To help you decide, the [OVHcloud professional email solutions page](https://www.ovh.ie/emails/){.external} offers a detailed comparison of the available services. You can also manage a mixed solution and use one or more Email Pro and Exchange accounts for the same domain name. Furthermore, if you need to migrate multiple accounts, we recommend that you set up a migration plan.

### Step 2: Ordering your Email Pro or Exchange accounts

This step is optional if you already have an Exchange or Email Pro service to which you are migrating.

Log in to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie){.external}, then click `Order`{.action} in the services bar on the left-hand side. Then select the service you want to order. You will be redirected to the order page. Follow the steps, then wait until the service is fully installed. An email will be sent to you as soon as the installation is complete.

> [!primary]
>
> Once an account has been delivered, it is essential to keep it in the “@configureme.me” state. It will be renamed during the migration.
>

### Step 3: Carrying out the migration

Before starting your migration, you will need to identify the version of the MXPlan you are migrating from.

To do this, log in to the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie){.external}, and open the `Web Cloud`{.action} section. Click `Emails`{.action} in the services bar on the left-hand side, then choose the name of the concerned plan. Please refer to the table below.

|MX Plan legacy version|MX Plan new version|
|---|---|
|![email](images/mxplan-starter-legacy-step1.png){.thumbnail}<br> Your solution is specified the "Plan" box.|![email](images/mxplan-starter-new-step1.png){.thumbnail}<br>You will find a `Server model` in the “Summary” box, starting with “mxplan-”.|
|Continue with [Legacy version of the MX Plan solution](#LegacyMxplan)|Continue with [New version of the MX Plan solution](#NewVersionMxplan)|

#### 3.1 Migrating a legacy MXPlan solution <a name="LegacyMxplan"></a>

> [!primary]
>
> Your OVHcloud account **must be** the administrative contact and technical contact for the Email Pro or Exchange service you are migrating to.
>
> For more information on editing contacts, please refer to our guide on [managing contacts for your services](../../customer/managing-contacts/).
>

You can migrate from two interfaces:<br>

- **the configuration wizard for Hosted Exchange**, only if you have just ordered a Hosted Exchange service and have not yet set up anything on it.
- **the MX Plan** solution, as soon as you have an Email Pro or Exchange service (already configured or not) and an MX Plan address that you want to migrate.

> As a reminder, before starting the migration, make sure that no **redirection** or **auto-replies** are configured on your MXplan.
> ![email](images/mxplan-legacy-redirect.png){.thumbnail}

Once you are ready, follow the steps below, depending on the interface you have selected. Please note that the migration time depends on the quantity of content to be migrated to your new account. This may vary from a few minutes to several hours.

> [!warning]
>
> Once the migration is confirmed, you will no longer be able to access your old MX Plan email address, or cancel the migration process. We strongly advise you to carry out this operation at a favourable time.
>
> Even if you can no longer access your current email address, messages that have already been received and those that have been received will not be lost. All will be immediately accessible from your new account.
>

##### **Migration with the Exchange configuration assistant**

To access it, select the relevant service in the [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie){.external} in the services bar on the left-hand side. The wizard should appear to help you configure your new Exchange service. During this process, you can select the MX Plan email accounts to migrate.

If the configuration wizard does not appear, the general information for the Exchange service will appear instead. In this case, you will need to migrate your accounts via the MX Plan interface.

##### **Migration from the MX Plan interface**

To migrate from this interface, go to the `Emails`{.action} section in the services bar on the left-hand side of the OVHcloud Control Panel. Then choose the service with the domain name of your email addresses. Click on `...`{.action} next to the relevant email account (also called the source account), then `Migrate account`{.action}.

![Exchange](images/access_the_migration_tool.png){.thumbnail}

In the window that pops up, select the destination service (the one you want to migrate the address to), then click `Next`{.action}. If the user has at least one "empty" account (i.e. one that has not yet been set up), the migration will be carried out to one of these accounts. Once you have done this, read the information listed, confirm it, then click `Next`{.action} to continue editing.

If you do not have one "empty" account, an `Order accounts`{.action} button will appear. Follow the steps, then wait until the accounts are installed to start the migration.

Finally, confirm the password for the source email address (the one you want to migrate), then click `Migrate`{.action}. You will need to repeat this process as many times as you need to for migrating other accounts.

![Exchange](images/account_migration_steps.png){.thumbnail}

#### 3.2 Migrating the new version of MXPlan <a name="NewVersionMxplan"></a>

Before you begin your migration, if you have just ordered your new email solution, first add the domain name to your [Email Pro](../../emails-pro/first-configuration-email-pro/#step-2-add-your-domain-name) or [Exchange](../../microsoft-collaborative-solutions/adding-domain-exchange/) platform.

Your MXPlan migration will be done in 3 main steps: **Renaming**, **Creating** and **Migrating**.

![Exchange](images/mxplan-migration-configure-account.gif){.thumbnail}

1\. **Rename** the MXPlan account to be migrated with a temporary name (example: to migrate the MX plan account *john.smith@mydomain.ovh*, rename it to *john.smith01@mydomain.ovh*).

In the `Email accounts`{.action} tab for your MX Plan platform, click the `...`{.action} button, then `Edit`{.action}.

![Exchange](images/mxplan-migration-configure-account01.png){.thumbnail}

> [!primary]
>
> Account modification is not immediate, please wait until the operation is complete before proceeding to the next step.

2\. **Create** your email address on the new account on your Email Pro or Exchange platform (using the previous example, you will create *john.smith@mydomain.ovh* on your new platform).

In the `Email accounts`{.action} tab for your Email Pro or Exchange platform, click the `...`{.action} button, then `Modify`{.action}.

![Exchange](images/mxplan-migration-configure-account02.png){.thumbnail}

3\. **Migrate** the MXPlan account to your new platform account using our [OMM](https://omm.ovh.net/) (OVH Mail Migrator) tool.

For more information on OMM, please read our guide on [Migrating email accounts via the OVH Mail Migrator](../exchange_email_account_migration_-_ovh_mail_migrator/).

![Exchange](images/mxplan-migration-configure-account03.png){.thumbnail}

The migration time depends on the amount of content to migrate to your new account. This may vary from a few minutes to several hours.

Check that you can find your items after the migration, by logging into OVHcloud [webmail](https://www.ovh.ie/mail/).

You can keep or delete the original account with the temporary name after this migration.

If you want to delete it, go to the `Email accounts`{.action} tab in your MX Plan, click on the `...`{.action} button, then `Disable account`{.action}.

### Step 4: Verifying your domain configuration

At this stage, your email addresses must already be migrated and functional. For security reasons, please ensure that your domain is correctly configured in your Control Panel.

To do this, select the Email Pro or Exchange service concerned in the services bar on the left-hand side, then go to the `Associated domains`{.action} tab. In the table shown, you can use the "Diagnostic" column to check if the DNS configuration is correct: a red box appears if the configuration needs to be modified.

> [!primary]
>
> If you have just migrated or modified a DNS record for your domain, it may take a few hours to be updated in your [OVHcloud Control Panel](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.ie/&ovhSubsidiary=ie){.external}.
>

To modify the configuration, click on the red box and carry out the requested operation. It can take between 4 and a maximum of 24 hours to propagate fully.

![Exchange](images/check_the_dns_records_associated_domains.png){.thumbnail}

### Step 5: Using your migrated email addresses

Now, you can start using your migrated email addresses. To do this, OVHcloud offers an online interface (_web app_), available here: <https://www.ovh.ie/mail/>. You will need to enter your email credentials.

If you have configured one of the migrated accounts on an email client (such as Outlook), you must set it up again. The login details for the OVHcloud server have changed following the migration. To help you make changes, please read the respective guides in the [Email Pro](../../emails-pro/) and [Hosted Exchange](../) guide sections. Even if you are unable to reconfigure the account immediately, access via the online application is still possible.

### Migrating manually

You can also manually migrate your email addresses to your new OVHcloud email solution using only your email software. Please refer to our guide on [Migrating your email address manually](../../emails/migrate-email-addresses-manually/). However, we recommend that you use this method only when the main methods are not possible.

## Go further

[Managing contacts for your services](../../customer/managing-contacts/){.external}.

[Email Pro guides](../../emails-pro/){.external} guides

[Exchange guides](../){.external}.

Join our community of users on ‹https://community.ovh.com/en/>.
