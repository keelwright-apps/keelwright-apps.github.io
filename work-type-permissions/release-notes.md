---
title: Release notes – Work Type Permissions for Jira
---

# Release notes

## First release

27 October 2026

- Rules per space and per work type: who can create it, and who can change
  existing work items into it, by space role, group or person.
- The create dialog offers people only the work types they may create.
- The "Work type permission check" validator for the Create transition covers
  the REST API, imports and other screens.
- Type changes, moves and bulk moves are checked without workflow changes.
- Space admins can manage the rules of their own spaces, unless a Jira admin
  turns this off.
- A bypass list for automation and integrations, and "Check a person".
- A daily check restores rules changed outside the app.
- Each week, people whose Atlassian account was closed are removed from rules.
