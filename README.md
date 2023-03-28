# Getting Started with Salesforce Development (using Salesforce CLI)

## Table of Contents
1. [Introduction](#introduction)
2. [Sign Up for a Salesforce Developer Edition Account](#step-1-sign-up-for-a-salesforce-developer-edition-account)
3. [Enable Dev Hub in Your Developer Edition Account](#step-2-enable-dev-hub-in-your-developer-edition-account)
4. [Install the Salesforce CLI](#step-3-install-the-salesforce-cli)
5. [Authenticate with Your Salesforce Developer Edition Account](#step-4-authenticate-with-your-salesforce-developer-edition-account)
6. [Create a New Salesforce Project](#step-5-create-a-new-salesforce-project)
7. [Update the config/project-scratch-def.json File](#step-6-update-the-configproject-scratch-defjson-file)
8. [Create a Scratch Org with Enabled Features](#step-7-create-a-scratch-org-with-enabled-features)
9. [Create the Event Custom Object](#step-8-create-the-event-custom-object)
10. [Deploy the Event Custom Object to Your Sandbox](#step-9-deploy-the-event-custom-object-to-your-sandbox)
11. [Conclusion](#conclusion)

## Introduction

## Introduction

Welcome to the Getting Started with Salesforce Development Tutorial! This is my very first tutorial about Salesforce Development, and it will help you set up a Salesforce Developer Edition account and get started with the Salesforce CLI to create a sandbox. The sandbox environment will allow you to experiment and develop your components without affecting your organization's live data.

This tutorial is a prerequisite for my Salesforce NPSP Donation Management Tutorial.

As part of this tutorial, we will install the Nonprofit Success Pack (NPSP) package, a set of pre-built Salesforce components tailored specifically for nonprofit organizations. This package will provide the foundation for our donation management system.

Additionally, we will create a custom object and deploy it to our sandbox using Salesforce CLI. This custom object will help nonprofits manage and track their fundraising and engagement events.

**Prerequisites:**
- A basic understanding of what the Salesforce platform and CRM are.
- A computer with a stable internet connection


## Step 1: Sign Up for a Salesforce Developer Edition Account

A Salesforce Developer Edition account is a free, full-featured Salesforce environment specifically designed for developers. It provides the necessary tools and resources to build, test, and experiment with Salesforce applications and features without affecting your organization's live data.

To sign up for a Salesforce Developer Edition account, follow these steps:

1. Visit the Salesforce Developer Edition signup page at [https://developer.salesforce.com/signup](https://developer.salesforce.com/signup).
2. Fill in the registration form with your details, ensuring that you select "Developer Edition" as the account type.
3. Complete the registration process and verify your email address.
4. Once your account is verified, log in to your Salesforce Developer Edition account.

With your Developer Edition account set up, you now have access to a dedicated environment for developing and testing your Salesforce components. In the following sections, we will walk you through enabling Dev Hub, installing Salesforce CLI, and creating a sandbox project.


## Step 2: Enable Dev Hub in Your Developer Edition Account

Dev Hub is a Salesforce feature that simplifies the management of development tasks across your entire organization. It allows you to manage and track your development resources, such as sandboxes, scratch orgs, and packages, from a central location. Enabling Dev Hub in your Developer Edition account is essential for working with the Salesforce CLI and creating a sandbox for your NPSP Donation Management system.

To enable Dev Hub in your Developer Edition account, follow these steps:

1. Log in to your Salesforce Developer Edition account.
2. Click the gear icon in the upper right corner, and then click "Setup".
3. In the Quick Find box, type "Dev Hub" and press Enter.
4. Click on "Dev Hub" in the search results.
5. Toggle the "Enable Dev Hub" switch to turn it on.
6. You'll also need to toggle the "Enable Source Tracking in Developer and Developer Pro Sandboxes" switch to turn that feature on as well, which is needed when we create our package a little later.

With Dev Hub enabled, you can now leverage its features to manage your development resources and create a sandbox for your NPSP Donation Management system in the upcoming steps.


## Step 3: Install the Salesforce CLI

The Salesforce CLI (Command Line Interface) is a powerful tool that simplifies various development tasks and helps automate your Salesforce development processes. It allows you to create and manage sandboxes, deploy code, and interact with your Salesforce org directly from the command line. In this step, we will install the Salesforce CLI on your computer.

To install the Salesforce CLI, follow these steps:

>
>**MacOS Users**: I'm running a Mac, and install sfdxcli using HomeBrew: `brew install sfdx`
>

1. Visit the Salesforce CLI download page at [https://developer.salesforce.com/tools/sfdxcli](https://developer.salesforce.com/tools/sfdxcli).
2. Select the appropriate installer for your operating system (Windows, macOS, or Linux) and download it.
3. Run the installer and follow the on-screen instructions to complete the installation process.
4. Once installed, open your command line (Command Prompt, Terminal, or a similar tool) and type `sfdx --version` to verify that the Salesforce CLI is installed correctly. You should see the installed version number displayed.

With the Salesforce CLI installed, you can now use it to authenticate with your Salesforce Developer Edition account, create a sandbox for your project, and perform other development tasks in the following sections.


## Step 4: Authenticate with Your Salesforce Developer Edition Account

To use the Salesforce CLI with your Developer Edition account, you must authenticate and establish a connection between the CLI and your account. Authenticating ensures secure access to your Salesforce org and enables you to perform development tasks directly from the command line.

To authenticate with your Salesforce Developer Edition account, follow these steps:

1. Open your command line (Command Prompt, Terminal, or a similar tool).
2. Enter the following command:

```
sfdx org login web --set-default-dev-hub --alias MyDevOrg
```

This command will open a new browser window, prompting you to log in to your Salesforce Developer Edition account.

3. Log in to your account using your credentials. After a successful login, you will see a message in your browser stating that you can close the window and return to the CLI.

4. Return to the command line, where you should see a confirmation message indicating that the authentication process was successful.

You have now authenticated the Salesforce CLI with your Developer Edition account and can use it to perform various development tasks, such as creating a new Salesforce project, updating the `config/project-scratch-def.json` file, and creating a scratch org with enabled features.


## Step 5: Create a New Salesforce Project

A Salesforce project is a directory structure that contains all the metadata and files required for developing and deploying components in a Salesforce org. Creating a new Salesforce project is essential for organizing and managing our project system's resources.

To create a new Salesforce project using the Salesforce CLI, follow these steps:

1. Open your command line (Command Prompt, Terminal, or a similar tool).
2. Navigate to the directory where you want to create your new Salesforce project.
3. Enter the following command:

```
sfdx project generate paws_for_cause
```

This command creates a new Salesforce project named `paws_for_cause` in the specified directory.

4. After the project is created, navigate to the project directory using the following command:

```
cd paws_for_cause
```

With your new Salesforce project created, you can now proceed to update the `config/project-scratch-def.json` file, create a scratch org with enabled features, and develop the custom Event object for our project.


## Step 6: Update the config/project-scratch-def.json File

The `config/project-scratch-def.json` file serves as a configuration template for creating scratch orgs. It allows you to define the shape of the org, including settings, features, and other configurations. In this tutorial, we'll create a self-contained application, so we'll need to update the `config/project-scratch-def.json` file to include the necessary features and settings for our NPSP Donation Management system, including enabling the NPSP package.

To update the `config/project-scratch-def.json` file, follow these steps:

1. In your project directory, open the `config/project-scratch-def.json` file in a text editor.
2. Update the file with the following configurations:

```json
{
  "orgName": "Paws for Cause",
  "edition": "Developer",
  "features": [
    "EnableSetPasswordInApi",
    "Communities",
    "PersonAccounts",
    "ServiceCloud",
    "AuthorApex"
  ],
  "settings": {
    "lightningExperienceSettings": {
      "enableS1DesktopEnabled": true
    },
    "mobileSettings": {
      "enableS1EncryptedStoragePref2": false
    },
    "orgPreferenceSettings": {
      "s1DesktopEnabled": true
    },
    "communitiesSettings": {
      "enableNetworksEnabled": true
    },
    "nameSettings": {
      "enableMiddleName": true,
      "enableNameSuffix": true
    }
  }
}
```

This configuration enables features like Communities, PersonAccounts, and ServiceCloud. Additionally, it configures various settings like enabling the Salesforce1 desktop app, Networks, and PersonAccounts. You can get a sense of all the settings available [here](https://developer.salesforce.com/docs/atlas.en-us.242.0.api_meta.meta/api_meta/meta_settings.htm).

>
> **Tip:** Click [here](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/sfdx_dev_scratch_orgs_def_file_config_values.htm) to learn more about available features.
>

3. Save the updated config/project-scratch-def.json file.
4. With the config/project-scratch-def.json file updated, you can now create a scratch org with the enabled features and settings in the next section.

## Step 7: Create a Scratch Org with Enabled Features

A scratch org is a temporary Salesforce environment that can be easily created and destroyed, making it ideal for development and testing purposes. With the `config/project-scratch-def.json` file updated to include the necessary features and settings for our NPSP Donation Management system, we can now create a scratch org using the Salesforce CLI.

To create a scratch org with the enabled features, follow these steps:

1. Open your command line (Command Prompt, Terminal, or a similar tool).
2. Navigate to your Salesforce project directory.
3. Enter the following command to create a scratch org, which we'll set as our new default org:

```
sfdx org create scratch -a PawsAndCause -f config/project-scratch-def.json -t --set-default
```

Once the above command finishes executing, you should have a new scratch org that we can work with and deploy to.

## Step 8: Create the Event Custom Object

In this step, we will create a custom object called "Event" that will help the nonprofit manage and track their fundraising and engagement events, such as galas, charity runs, or auctions. This custom object will be part of our self-contained application for the NPSP Donation Management system. We will define the necessary fields for the Event object, including Event Name, Event Date, Location, Type of Event, and Expected Attendance.

To create the Event custom object, follow these steps:

1. In your Salesforce project directory, create a new folder named "objects" inside the "force-app/main/default" folder, if it doesn't already exist.

2. Inside the "objects" folder, create a new folder named "Event__c".

3. In the "Event__c" folder, create a new file named "Event__c.object-meta.xml" with the following contents:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<CustomObject xmlns="http://soap.sforce.com/2006/04/metadata">
    <deploymentStatus>Deployed</deploymentStatus>
    <description>Manage and track fundraising and engagement events</description>
    <enableActivities>true</enableActivities>
    <enableBulkApi>true</enableBulkApi>
    <enableFeeds>true</enableFeeds>
    <enableHistory>false</enableHistory>
    <enableReports>true</enableReports>
    <enableSearch>true</enableSearch>
    <label>Event</label>
    <pluralLabel>Events</pluralLabel>
    <sharingModel>ReadWrite</sharingModel>
    <nameField>
        <label>Event Name</label>
        <type>Text</type>
    </nameField>
</CustomObject>
```
4. Inside the "Event__c" folder, create a new folder named "fields".

5. In the "fields" folder, create the necessary field files for the Event object:

- EventDate__c.field-meta.xml
- Location__c.field-meta.xml
- TypeOfEvent__c.field-meta.xml
- ExpectedAttendance__c.field-meta.xml
6. Add the appropriate XML content to each field file, defining the field's properties, such as data type, label, and description.

#### EventDate__c.field-meta.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Field xmlns="http://soap.sforce.com/2006/04/metadata">
    <fullName>EventDate__c</fullName>
    <label>Event Date</label>
    <required>true</required>
    <trackTrending>false</trackTrending>
    <type>Date</type>
    <unique>false</unique>
</Field>
```

Location__c.field-meta.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Field xmlns="http://soap.sforce.com/2006/04/metadata">
    <fullName>Location__c</fullName>
    <label>Location</label>
    <required>true</required>
    <trackTrending>false</trackTrending>
    <type>Text</type>
    <unique>false</unique>
    <length>255</length>
</Field>
```

TypeOfEvent__c.field-meta.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Field xmlns="http://soap.sforce.com/2006/04/metadata">
    <fullName>TypeOfEvent__c</fullName>
    <label>Type of Event</label>
    <required>true</required>
    <trackTrending>false</trackTrending>
    <type>Picklist</type>
    <unique>false</unique>
    <valueSet>
        <restricted>false</restricted>
        <valueSetDefinition>
            <sorted>false</sorted>
            <value>
                <fullName>Auction</fullName>
                <default>false</default>
            </value>
            <value>
                <fullName>Charity Run</fullName>
                <default>false</default>
            </value>
            <value>
                <fullName>Gala</fullName>
                <default>false</default>
            </value>
            <value>
                <fullName>Other</fullName>
                <default>false</default>
            </value>
        </valueSetDefinition>
    </valueSet>
</Field>
```

ExpectedAttendance__c.field-meta.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Field xmlns="http://soap.sforce.com/2006/04/metadata">
    <fullName>ExpectedAttendance__c</fullName>
    <label>Expected Attendance</label>
    <required>true</required>
    <trackTrending>false</trackTrending>
    <type>Number</type>
    <unique>false</unique>
    <precision>18</precision>
    <scale>0</scale>
</Field>
```


With the Event custom object and its fields created, you can now deploy the custom object to your scratch org using the Salesforce CLI in the next section.


## Step 9: Deploy the Event Custom Object to Your Sandbox

Now that you've created the custom object and its fields, you'll need to deploy it to your PawsAndCause scratch org using the Salesforce CLI.

To deploy the custom object, we will be creating a package, which is a container for a collection of metadata components in Salesforce, such as custom objects, fields, and Apex classes. Packages can be used to organize and distribute your customizations across multiple Salesforce orgs.

By using a package, we can easily deploy the custom object we created in the previous step to our scratch org environment. We can also version our package, which allows us to track changes to our customizations over time and manage their dependencies.

Follow these steps to deploy the custom object:

1. Open your command prompt or terminal and navigate to your project directory.
2. Execute the following command to create a package for our custom objects:

```
sfdx package create --name PawsForCause --path force-app -e --package-type Unlocked    
```

3. Create a new package version to deploy by executing the following command:

```
sfdx package create version --installation-key-bypass
```

4. Install our package in our PawsForCause scratch:

_TODO_
