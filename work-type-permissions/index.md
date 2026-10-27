---
title: Work Type Permissions for Jira
---

# Work Type Permissions for Jira

Jira Cloud has one "Create work items" permission for every work type (issue
type) in a space. Work Type Permissions lets you decide, per space and per
work type, who can create it and who can change existing work items into it.

- [Get started](#get-started)
- [Set rules for a space](#set-rules-for-a-space)
- [Block every way of creating work](#block-every-way-of-creating-work)
- [Settings for Jira admins](#settings-for-jira-admins)
- [Check a person](#check-a-person)
- [How the rules are enforced](#how-the-rules-are-enforced)
- [Limits](#limits)
- [FAQ](#faq)
- [Uninstalling](#uninstalling)
- [Support](support.md) · [Privacy policy](privacy.md) · [Terms](terms.md) · [Data and security](security.md)

## Get started

1. Install the app from the Atlassian Marketplace (Jira admin).
2. Open a space, then **Space settings → Work type permissions**.
3. Click **Edit** next to a work type, choose who can create it, and click **Apply**.
4. Click **Save rules**. The create dialog uses the rules straight away.
5. Optional but recommended: [add the validator](#block-every-way-of-creating-work) to the Create transition.

## Set rules for a space

Each work type has two rules.

**Who can create it**

- *Everyone (no restriction)*: anyone with the Create work items permission, as today.
- *Only the roles, groups and people below*: pick any mix of space roles, groups and people. A person needs to match one of them.

If you pick "only" and leave the lists empty, nobody can create that type
except the bypass list (for example, automation). Use this for types that only
automation or integrations should create.

**Who can change existing work items into it**

- *The same people who can create it* (default).
- *Everyone*: anyone can switch work into this type.
- *Only the roles, groups and people below*: a separate list.

This rule applies when someone changes the type in the work item view, moves a
work item, or uses bulk move.

Use **Enforce these rules** to switch all rules for the space off and on
without losing them.

## Block every way of creating work

The create dialog hides restricted work types as soon as you save. Work can
also be created through the REST API, CSV imports, email and some quick-create
fields. To block those too, add the app's validator to the Create transition
of each workflow the space uses:

1. **Space settings → Workflows**, then edit the workflow.
2. Select the **Create** transition and add a rule (validator).
3. Choose **Work type permission check** and save. Publish the workflow.

The validator reads the same rules, so you only add it once per workflow. In
company-managed spaces that share a workflow, add it once and every space
using that workflow is covered (spaces without rules are never blocked).

## Settings for Jira admins

**Apps → Manage apps → Work Type Permissions → Configure** (or the app's admin
page) has the settings that apply to every space:

- **Let space admins manage the rules for their own spaces.** On by default.
  Turn it off to keep rule changes to Jira admins; space admins can still view
  the rules and check people.
- **Bypass groups and people.** Never restricted. The app adds
  `atlassian-addons-admin` when it is installed, which keeps Jira automation
  and other apps working. Remove it only if you want automation restricted too.
- **Spaces with rules** lists every space that has rules and whether they are on.
- **Health** shows the last check. The app re-checks every space once a day
  and restores rules that were changed outside the app.
- **Closed accounts.** Once a week the app asks Atlassian which of the people
  named in rules or on the bypass list have closed their Atlassian account, and
  removes them. A rule never opens up because of this: it stays limited to the
  groups and roles left in it.

## Check a person

On the space page, pick a person under **Check a person** and click **Check**.
You see, for each work type, whether they can create it and whether they can
change work into it, based on the saved rules. Use it to test a rule before
telling your team.

## How the rules are enforced

| Where | How |
| --- | --- |
| Create dialog | Restricted types are hidden for people who can't use them. If the dialog opens on a hidden type, it switches to an allowed one. |
| REST API, imports, other screens | The "Work type permission check" validator on the Create transition (see above). |
| Changing the type, moving, bulk move | Checked automatically, no workflow change needed. |

People who are not allowed see this message: "You can't create Epic work items
in this space. Ask a space admin if you need access."

## Limits

- **Jira Service Management:** requests raised by customers also go through
  the Create transition. Don't restrict a work type that a customer request
  type uses, or include customers in the rule.
- **Moving to another space** checks the rules of the space the work item
  comes from.
- The create dialog check needs the app's script to load. If it fails, the
  validator still blocks restricted creates when it is on the workflow.
- Up to 100 roles, groups and people per rule.

## FAQ

**Does this replace Jira permissions?** No. People still need the normal
"Create work items" permission. The app narrows it down by work type.

**Do rules apply to Jira admins?** Yes, unless they are on the bypass list or
in the rule. Add your admin group to the bypass list if admins should never be
restricted.

**Is the app free?** The Marketplace listing shows the current price. If a
paid subscription ends, rules stay saved but stop being enforced within a
day. They come back when the subscription is active again.

**Does any data leave Atlassian?** No. The app runs on Atlassian's Forge
platform and has no external connections ("Runs on Atlassian").

## Uninstalling

Before you uninstall, remove the **Work type permission check** validator from
your workflows. Jira treats a validator from an uninstalled app as failing,
which would stop people creating work in those workflows.
