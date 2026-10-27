---
title: Privacy policy – Work Type Permissions for Jira
---

# Privacy policy

Last updated: 27 October 2026

This policy covers the Work Type Permissions for Jira app ("the app")
published by Keelwright ("we", "us") on the Atlassian Marketplace.

## Summary

The app runs entirely on Atlassian's Forge platform ("Runs on Atlassian"). It
makes no connections outside Atlassian, and we do not receive, copy or store
your data on our own systems.

## What the app processes

To apply your rules, the app stores, inside your Atlassian cloud site:

- the rules you create: space IDs, work type IDs, space role IDs, group IDs
  and Atlassian account IDs of people named in a rule or on the bypass list;
- app settings (for example, whether space admins may edit rules);
- bookkeeping data (the time and result of the last automatic check, and
  when each stored account ID was last reported to Atlassian).

This data is kept in Forge storage and in a Jira space property
(`wtp.rules`) on each space that has rules. Both are hosted by Atlassian and
follow your site's Atlassian data residency settings where supported.

Once a week the app sends the account IDs it stores, and nothing else, to
Atlassian's personal data reporting service, as Atlassian requires of apps
that store account IDs. When Atlassian answers that an account was closed, the
app removes that account ID from every rule and from the bypass list. A rule
that loses its last named person does not open up: it stays limited to the
groups and roles left in it, or to the bypass list.

When someone opens the create dialog, the app reads that person's account ID,
group memberships and space roles from Jira to decide which work types to
hide. This is done at the time of the request and not stored.

The app does not read work item content such as summaries, descriptions,
comments or attachments.

## What we receive

- **No customer data.** We have no copy of your rules or of any Jira data.
- **Logs.** Atlassian may make Forge function logs available to us to fix
  errors. The app does not write personal data or work item content to logs;
  error logs may contain technical identifiers such as space or work type IDs.
- **Marketplace data.** Atlassian shares licensing and contact details with
  Marketplace partners under the Atlassian Marketplace terms (for example, the
  technical and billing contacts of a licence). We use these only to provide
  support and meet legal obligations.
- **Support requests.** If you email us, we keep the email and what you send
  for as long as needed to help you.

## Sharing

We do not sell or share personal data. We do not use analytics, tracking or
advertising in the app.

## Retention and deletion

App data stays in your site while the app is installed. When an Atlassian
account is closed, the app removes its account ID at its next weekly report to
Atlassian. When you uninstall the app, Atlassian deletes the app's Forge
storage under its retention rules; the `wtp.rules` space properties can be
removed by a Jira admin. You can ask us to delete support emails at any time.

## Your rights

Since we hold no customer data from the app, requests about data inside your
site are handled by your site's administrators and Atlassian. For anything we
hold (support emails, Marketplace contact data), contact us at
keelwright.apps@gmail.com and we will respond within 30 days.

## Changes

We will post changes to this policy on this page and update the date above.

## Contact

Keelwright · keelwright.apps@gmail.com
