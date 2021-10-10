---
layout: post
title:  "Totara Learn's IAAA characteristics and features"
date:   2020-12-07 19:54:29 +1000
categories: elearning
---

IAAA is an acronym for Identification and Authentication, Authorization, and Accountability and concerns access control, security, and traceability in a software system. This article describes Totara Learn's IAAA characteristics and features.

Security-conscious stakeholders should check out the following Totara documentation:

- [Security overview](https://help.totaralearning.com/display/TH13/Security+overview)
- [Security settings](https://help.totaralearning.com/display/TH13/Security+settings)
- [Site policies](https://help.totaralearning.com/display/TH13/Site+policies)

## Identification

User identity is reflected in Totara Learn's User profile fields such as:

- idnumber
- username
- firstname, middlename, lastname
- email
- custom fields where configured e.g. employee number

## Authentication

Totara Learn supports a variety of authentication methods, including:

- internal authentication
- manual accounts, i.e. those created "by hand" or via [HR Import](https://help.totaralearning.com/display/TH13/HR+import), [Upload Users](https://help.totaralearning.com/display/TH13/Upload+users) or [API calls (web services)](https://help.totaralearning.com/display/TH13/Web+services)
- self-registered accounts: [email-based](https://help.totaralearning.com/display/TH13/Email-based+self-registration) or [otherwise](https://help.totaralearning.com/display/TH13/Self-registration+with+approval)
- external authentication, e.g.
  - LDAP: account details are stored on an external LDAP server
  - SSO: account details are stored on an external Client Access Server (CAS); users log in via an SSO protocol such as SAML
  - OAuth2: users log in via their existing Microsoft, Google or Facebook account

See Totara Learn's [authentication documentation](https://help.totaralearning.com/display/TH13/Authentication) for more options.

### Multiple authentication methods

Totara Learn supports multiple authentication methods in parallel, though a given learner accesses the LMS via one of the available methods. Sometimes the learners are a mixture of internal and external people, where you might desire SSO access for employees or members, but self-registration accounts for everyone else.

### Multi-factor identification

Totara Learn's internal authentication does not support multi-factor authentication (MFA). Organizations requiring MFA must implement a supported external authentication method that supports it. Consider identity providers (IdP) such as [Azure AD](https://www.manageengine.com/products/passwordmanagerpro/help/azure_ad_saml_based_sso_configuration.html) or identity management services such as [Okta](https://support.okta.com/help/s/article/What-is-Okta?language=en_US).

When an external identity provider manages authentication, Totara Learn is a service provider (SP). Totara relies on the authentication token from the IdP for user authentication and does not require additional factors.

Totara Learn cannot serve as the IdP for content providers out of the box, but some LMS vendors provide custom code to support SSO between Totara and other systems when the client doesn't otherwise have a CAS or IdP.

### Authentication types

#### Type 1 (known information)

Password

#### Type 2 (possessed identification)

- Totara Learn [session cookies](https://help.totaralearning.com/display/TH13/Cookie+Policy)
- External authentication tokens from an IdP (see above)

#### Type 3 (physical characteristics e.g. biometrics)

Totara Learn does not currently support this authentication type.

#### Type 4 (location)

- Set ranges of allowed and blocked IP addresses with Totara Learn's IP Blocker feature.
- Restrict access to a Quiz Activity (exam/test) by defining a list of allowed IP addresses. This option allows the customer to establish fixed "examination rooms" whereby the learner must be in a specific location to undertake the Quiz.
- You cannot restrict Course access via IP addresses without custom software.
- MAC addresses are only available to the firewall. Totara Learn does not currently support access control via MAC address filtering.

#### Type 5 (action e.g. pattern unlock)

Totara Learn does not currently support this authentication type.

## Authorization

Totara Learn supports fine-grained control of roles and permissions. Refer to the following Totara documentation:

- [User policies](https://help.totaralearning.com/display/TH13/User+policies)
- [Roles](https://help.totaralearning.com/display/TL12/Roles), including System Roles, User Roles, Role Contexts, Permission Levels, Capabilities, Rule Overrides, and Role Switches
- [User preferences](https://help.totaralearning.com/display/TH13/User+preferences)
- [Job assignments](https://help.totaralearning.com/display/TH13/Job+assignments)

You can assign [roles and permissions](https://help.totaralearning.com/display/TL12/Categories) to users at the Course Categories level. At the Course level, you can only [assign roles](https://help.totaralearning.com/display/TH13/Enrolling+users).

Review the capabilities for a specific user based on their role assignments by using the [Check System Permissions](https://help.totaralearning.com/display/TH13/Roles#Roles-Checksystempermissions) feature.

To change a given user's access, adjust their role, permissions, or inactivate their account.

You cannot log in to the application server or database server with Totara user credentials.

## Accountability

You can audit user actions via Totara's [Logging](https://help.totaralearning.com/display/TH13/Logging) features. You can customize the types of activities recorded and the retention period for this data.

You can rely on Totara to store the audit records or transmit them to an external log store, such as a third-party Learning Record Store (LRS). [Learning Locker](https://learningpool.com/solutions/learning-record-store-learning-locker/learning-locker-community-overview/) is popular.

LMS vendors can provide xAPI/Tin Can functionality to capture more granular information about learners' actions within Course Activities for storage in an LRS.