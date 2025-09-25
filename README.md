# Shelter Data Management

## Introduction

The **Shelter Data Mangement template** is a data management solution based on EspoCRM for humanitarian organizations to manage their data in hosting and rental programs.

This template should be used together with the [People Affected Management (PAM)](https://github.com/rodekruis/espocrm-template-pam/tree/main) template.

#### Why Shelter template?
Management of information is a critical aspect within a shelter program. It is essential to have a system that is **secure**, **easy to use**, **fast to set up**, and **customizable** to the needs of your organization. The shelter template is designed to meet these requirements. It offers:
* A simple yet effective **data model**, defining what data is stored in the system and how it is interlinked​
* A set of **layouts** to easily manage this data​
* Standard **user roles** to control access, down to individual records and fields​
* **Workflows** that automate operational processes​
* **Integrations** with other tools, such as Kobo, PowerBI, or Twilio

#### Why EspoCRM?
[EspoCRM](https://www.espocrm.com/) is an open-source data management system. It is highly customizable, directly from the user interface. It is free to use, lightweight, and has a large, supportive user community. For more information, visit the [EspoCRM Documentation](https://docs.espocrm.com/) and [510's EspoCRM knowledge base](https://github.com/rodekruis/EspoCRM-knowledge-base/wiki).


## Description

Shelter template consists of _Entities_, _Roles_, _Reports_ and _Flowcharts_. 
* Entities are data structures that hold information (about affected households, accommodations, etc.).
* Roles are sets of permissions that define what each user can do in the system.
* Reports are graphics that show (consilidated) information from the data in the system.
* Flowcharts are processes that happen automatically, based on a certain trigger.

#### Entities and their relationships:
* **Affected Household**: a group of people living together, affected by a disaster, e.g. the beneficiaries of a program. Linked to accommodations, a match, message template and messages. Also, it is linked to the Person Affected of the PAM template.
* **Accommodation**: an accommodation to be used by an affected household. Linked to affected households, a match, an accomodation adequacy form, message template and messages. Also, it is linked to the Person Affected of the PAM template.
* **Match**: a match between an affected household and an accommodation. Linked to an affected household, an accommodation, a bank, cash distribution, transfers and monitoring forms.
* **Accommodation adequacy**: a form reviewing an accommodation, including adequacy criteria. Linked to an accommodation.
* **Monitoring**: a monitoring form, to be used to follow up on a match. Linked to a match.
* **Message templates**: a template of a message that can be send to affected households or accommodations. Linked to affected households, accommodations and messages.
* **Messages**: a message that is sent to a specific person. Linked to an affected household or accommodation and to a message template.
* **Cash distributions**: a "template" of a transfer that can be send to a certain match, containing information on the transfer date, type, value, frequency. Linked to a match and transfers.
* **Transfers**: a transfer related to a specific person. Linked to a match and a cash distribution.
* **Banks**: list of banks. Linked to matches.

#### Roles:
* **Shelter Manager**: registers, sees and edits all information.
* **Shelter Officer**: registers and sees affected households, accommodations and matches of their team.
* **API Kobo**: registers affected households, accommodations and accommodation adequacy forms.

## Installation

> [!IMPORTANT]  
> Make sure to back up your EspoCRM instance before installing this extension.

> In order to make use of the full functionalities of this extension (automatic processes with flowcharts and reports), the [Advanced Pack](https://www.espocrm.com/extensions/advanced-pack/) of EspoCRM is needed.

1. If not done already, [install EspoCRM](https://docs.espocrm.com/administration/installation/).
2. Install [PAM](https://github.com/rodekruis/espocrm-template-pam/tree/main)
3. Download the .zip file with the extension: [extension.zip](https://github.com/rodekruis/espocrm-template-shelter/raw/refs/heads/main/extension.zip).
2. Install the extension
    * Log in EspoCRM as an administrator.
    * Go to `Administration` > `Extensions`.
    * Select the .zip file with the extension.
    * Click `Install`.

> [!WARNING]  
> If you already have entities with the same names, the installation will overwrite them.
 
3. Make the entities visible in the `Navbar`:
    * Go to `Administration` > `User Interface`.
    * Under `Navbar` > `Tab List`, add the entities `Affected Household`, `Accommodation`, `Match`, `Accommodation adequacy`, `Monitoring`, `Message templates`, `Messages`, `Cash distributions`, `Transfers` and `Banks`.
4. For every file in the [import](/import) folder, import it in EspoCRM:
    * Go to `Administration` > `Import`.
    * Under `What to Import?` > `Entity Type`, select the entity corresponding to the file name; e.g. if the file name is `Roles.csv`, select `Roles`.
    * Click `Next`.
    * Click `Run Import`.
  
### Optional steps for installation, adding more functionalities
5. Proper set up of relationships between Shelter and PAM
    * Add the following relationships:
    * XX
6. Sending of messages
In order to send messages, it is necessary to update the two flowcharts with Target Entity Type "Message". It has been set up with an integration to Twilio, so then a Twilio account is needed. For the flowcharts to work, the following needs to be done:
    * Add the Account ID in the two flowcharts: Open the flowcharts one by one, click on the task box and edit the part `$accountID = 'YOUR_ACCOUNT_ID';`, where `YOUR_ACCOUNT_ID` should be updated with the account ID of the Twilio account used.
    * Add the Authentication Key in the App Secrets: Go to Administration > App Secrets > Create Secret > The Name should be `authenticationKeyTwilio`, and the Value is the authentication key of the Twilio account used.
7. Translation of comment boxes
    * There are two flowcharts to translate the comment boxes in the Affected Household and Accommodation entities. In order to make this work:
      * Add the URL in the two flowcharts that takes care of the translation of the comment box: Open the flocwcharts one by one, click on the task box and edit the part `ADD_URL`, where `ADD_URL` is the endpoint that takes care of the translation of the comment box.

> [!WARNING]  
> If you already have records with the same names, the import will overwrite them.

## Terms of Use
* This extension is developed by [the Netherlands Red Cross' 510](https://www.510.global/) and is not officially supported by EspoCRM.
* It is free to use and modify, as specified in the [GNU AGPLv3 License](/LICENSE.md).
* It is provided as-is, without any warranty. Please ensure it works as intended before using it in a real humanitarian program.
* It is meant to be used as a starting point for organizations to build their own data management system. It is recommended to customize it to the specific needs of your organization.
* If you have any questions, please [contact us](https://www.510.global/contact/). We cannot guarantee support, but we will do our best to help you.
