---
title: Data and security – Work Type Permissions for Jira
---

# Data and security

Use this page for security reviews. The same answers appear in the Privacy &
Security tab of the app's Atlassian Marketplace listing.

## Architecture

- Built on Atlassian Forge, "Runs on Atlassian": all code runs on Atlassian's
  infrastructure, user interfaces use Forge UI, and the app declares no
  external network access (no egress, no remote back end).
- Storage: Forge key-value storage (rules, settings, bookkeeping) and one Jira
  space property per space with rules (`wtp.rules`).
- No connection to any third-party service, analytics or tracking.

## Permissions (OAuth scopes) and why

| Scope | Used for |
| --- | --- |
| `read:jira-work` | Read spaces, work types and space roles shown on the settings pages |
| `read:jira-user` | Read group names, people's display names and group memberships for rules and "Check a person" |
| `manage:jira-project` | Write the `wtp.rules` space property the validators read |
| `manage:jira-configuration` | Register the create-dialog UI modification |
| `storage:app` | Store rules and settings in Forge storage |
| `report:personal-data` | Report the stored account IDs to Atlassian's personal data reporting service once a week, and learn which accounts were closed |

## Data handled

| Data | Stored? | Where |
| --- | --- | --- |
| Space IDs, work type IDs, role IDs, group IDs | Yes | Forge storage and space property, in your site |
| Atlassian account IDs named in rules or on the bypass list | Yes | Forge storage and space property, in your site; reported weekly to Atlassian's personal data reporting service, and removed once the account is closed |
| Current user's groups and space roles | No (read per request) | — |
| Work item content (summaries, descriptions, comments, attachments) | Never accessed | — |

## Security questionnaire answers

- **Does the app store data outside Atlassian?** No.
- **Does the app process personal data?** Yes, Atlassian account IDs of people
  named in rules or on the bypass list, stored only in the customer's site.
- **Does the app follow Atlassian's user privacy guidelines?** Yes. It reports
  the account IDs it stores to Atlassian's personal data reporting API once a
  week and removes the account IDs of closed accounts from rules and the bypass
  list. It does not store names, email addresses or other profile data.
- **Does the app send data to third parties?** No.
- **Data residency:** follows Forge storage data residency for the site.
- **Data retention and deletion:** data stays while the app is installed;
  account IDs of closed accounts are removed at the next weekly report; Forge
  storage is deleted by Atlassian after uninstall; customers can remove the
  space properties.
- **Encryption:** handled by Atlassian (Forge storage and Jira are encrypted at
  rest and in transit).
- **Logging:** Forge logs; no personal data or work item content is logged.
- **Authentication:** Forge platform authentication only; no API tokens or
  Basic authentication.
- **Access by the partner:** none to customer data; Forge logs only.
- **Security contact:** keelwright.apps@gmail.com.
- **Vulnerability handling:** reports to keelwright.apps@gmail.com are acknowledged
  within 2 business days and fixed according to severity.
