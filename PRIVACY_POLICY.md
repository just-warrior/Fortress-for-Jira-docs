# Privacy Policy for Jira Fortress for Jira

**Effective Date:** June 10, 2026

This Privacy Policy explains how **Jira Fortress for Jira** ("App"), provided by **JMC Labs** ("we", "us", or "our"), handles data when installed on a Jira Cloud site.

## 1. Overview

Jira Fortress for Jira is built on Atlassian Forge. We do not operate external application servers, external databases, analytics tools, or telemetry pipelines for this App. App data is processed through Atlassian Forge and Jira Cloud services.

## 2. Data We Store

The App stores the following data in Atlassian Forge storage:

- **App configuration:** allowed Jira project keys, update timestamp, and updater account identifier for the administrator project allowlist.
- **Battle state:** per-issue game status, map type, player account IDs, player display names, player HP, tank positions, turn state, wind value, recent shot data, recent emoji data, processed action IDs, spectator counts, and timestamps.
- **Game results:** winner and loser account IDs and display names, assignment result, finish reason, final HP values, and finish timestamp.
- **Cached user display data:** user account IDs and display names used to render battle participants.

## 3. Data We Process

When users interact with a battle, the App may process Jira issue context and user context needed to run the issue panel and resolve game actions. This can include:

- Jira issue ID and project key
- Atlassian account ID of the acting user
- user display name
- game action payloads such as movement direction, shot angle, shot power, action ID, emoji type, and forfeit request
- issue assignment information needed to update the assignee after a battle

The App may create Jira comments for battle events and may update the issue assignee after a battle ends.

## 4. Data We Do Not Collect

We do not intentionally collect or store:

- Atlassian account passwords
- Atlassian Personal Access Tokens
- customer API keys or shared secrets
- payment card details
- marketing analytics identifiers
- arbitrary issue content beyond what is needed for the battle and assignment workflow

Customers should not enter secrets into Jira issue comments or any app-visible fields.

## 5. Data Transmission and Third Parties

We do not transmit customer data to third-party servers. We do not use Google Analytics, Mixpanel, Segment, Sentry, or similar third-party analytics or error tracking services in the App.

Data remains within Atlassian apps and services. The App calls Atlassian APIs through Forge to perform supported Jira actions such as reading issue context, creating comments, resolving users, and updating assignees.

## 6. Logs

The App may write operational logs to the Atlassian Forge runtime for troubleshooting. These logs are intended for app diagnostics and are not used for advertising or analytics by JMC Labs.

Jira comments created by the App remain in the customer's Jira Cloud site and are managed according to the customer's Jira permissions and retention policies.

## 7. Data Retention and Deletion

- App configuration remains until changed by an administrator or until the App is uninstalled.
- Battle state and game result data remain in Forge storage for the relevant issue unless deleted by app behavior or removed according to Atlassian Forge platform behavior.
- Jira comments created by the App remain in Jira until deleted according to Jira permissions and customer retention practices.
- When the App is uninstalled, App data is handled according to Atlassian Forge storage and data retention policies.

## 8. Data Residency

The App stores data exclusively within Atlassian Forge storage and Jira Cloud services. Data residency behavior follows Atlassian Forge and Jira Cloud capabilities and is not controlled by JMC Labs through external infrastructure.

## 9. Security

Jira Fortress for Jira uses Atlassian Forge-hosted backend resolvers and Forge storage. Game actions are validated by backend resolvers before state changes are stored. The App does not expose arbitrary outbound HTTP access and does not run customer-provided code.

Project access is controlled by an administrator-managed allowlist. If a project is not included in the allowlist, battle actions for that project are blocked.

## 10. GDPR and CCPA Roles

For customer Jira data processed through the App, JMC Labs generally acts as a processor/service provider on behalf of the customer. Customers remain responsible for determining their own legal basis, user notices, and compliance obligations for Jira data processed in their Jira Cloud sites.

## 11. Changes

We may update this Privacy Policy from time to time. The effective date above will be updated when material changes are made.

## 12. Contact

For privacy or security questions, contact:

**JMC Labs**  
Email: **wjdals9058@gmail.com**
