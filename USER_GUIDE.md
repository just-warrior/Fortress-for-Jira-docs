# Jira Fortress for Jira - User Guide

**Last Updated:** June 10, 2026

Jira Fortress for Jira is a Forge-native Jira Cloud app that adds a lightweight turn-based fortress battle to Jira issues. Teams can use the battle as a fun way to decide who becomes the assignee of an issue.

The app runs inside Jira Cloud using Atlassian Forge. Jira administrators control which Jira projects can use the app through an allowlist configuration page.

## 1. Installation

1. Install **Jira Fortress for Jira** from the Atlassian Marketplace.
2. Approve the requested Jira scopes.
3. Open Jira as a Jira administrator.
4. Go to **Apps -> Manage apps -> Jira Fortress for Jira -> Configure**.
5. Add the Jira project keys where the app should be enabled.

By default, Jira Fortress is disabled for all projects until an administrator adds project keys to the allowlist.

## 2. Core Concepts

| Concept | Description |
|---|---|
| Allowed project | A Jira project whose project key is included in the app configuration allowlist. |
| Issue panel | The Jira issue panel where users open the battle window. |
| Battle window | A modal battle arena where players join, aim, move, fire, send emoji, and forfeit. |
| Player | A user participating in the battle for an issue. |
| Spectator | A user viewing an existing battle without participating. |
| Game result | The final state of the battle, including winner, loser, finish reason, and assignment result. |

## 3. Administrator Configuration

Only Jira administrators should configure the app.

1. Open Jira administration.
2. Go to **Apps -> Manage apps**.
3. Find **Jira Fortress for Jira**.
4. Click **Configure**.
5. Enter allowed Jira project keys separated by commas or new lines.
6. Click **Save configuration**.

Project keys are normalized by the app:

- leading and trailing spaces are removed
- keys are converted to uppercase
- duplicate keys are removed

Example:

```text
DEV, QA
OPS
```

This enables Jira Fortress only for projects with keys `DEV`, `QA`, and `OPS`.

Leaving the allowlist empty disables Jira Fortress everywhere.

## 4. Starting a Battle

1. Open an issue in an allowed Jira project.
2. Open the **Assignee Battle** issue panel.
3. Click **Open battle window**.
4. The first player joins or creates the game.
5. A second player opens the same issue and joins the game.
6. Once both players have entered, the game starts after a short countdown.

If the issue belongs to a project that is not in the allowlist, the panel shows a disabled message and the battle cannot be opened or continued.

## 5. Gameplay

During a battle, each player takes turns using the controls in the battle window.

Available actions:

- adjust shot angle
- adjust shot power
- move the tank before firing
- fire a shot
- end the turn after moving
- send a quick emoji reaction
- forfeit the game

The game uses server-resolved state for multiplayer sync. Shots, movement, turn changes, timeout handling, and final assignment are validated by the Forge backend.

## 6. Winning and Assignment

A battle can finish in three ways:

- **Knockout:** a player wins by reducing the opponent's HP to zero.
- **Timeout:** a player loses when their turn times out.
- **Forfeit:** a player loses by forfeiting.

When the battle ends, Jira Fortress attempts to set the issue assignee according to the battle result. The app also creates Jira comments for battle events where applicable.

Assignment can fail if Jira permissions, workflow rules, issue security, or project configuration prevent the assignee update. If assignment fails, the battle result still remains visible in the game result.

## 7. Permissions

Jira Fortress requests these Atlassian scopes:

| Scope | Purpose |
|---|---|
| `read:jira-work` | Read Jira issue context needed to run the issue panel and process battle state. |
| `write:jira-work` | Add Jira comments and update the issue assignee after a battle. |
| `read:jira-user` | Resolve player display names and user information for battle state and result display. |
| `storage:app` | Store app configuration, per-issue game state, action IDs, and related battle metadata in Forge storage. |

## 8. Privacy and Security

- The app is hosted on Atlassian Forge.
- JMC Labs does not operate external app servers or external databases for Jira Fortress.
- The app does not use Google Analytics, Segment, Mixpanel, Sentry, or similar third-party tracking tools.
- App configuration and battle state are stored in Atlassian Forge storage.
- The app uses Jira APIs only for supported app behavior, such as reading issue context, creating battle comments, resolving users, and updating assignees.

## 9. Limitations

- Jira Fortress is available only in projects added to the administrator allowlist.
- The app does not hide the issue panel dynamically for disabled projects; it shows a disabled message instead.
- A battle is tied to a single Jira issue.
- Assignment updates depend on Jira permissions and project configuration.
- The app is designed for lightweight team engagement and should not be used as the sole control for critical operational assignment workflows.
- Forge platform limits apply to storage, resolver execution, and UI rendering.

## 10. Troubleshooting

### The issue panel says Jira Fortress is not enabled

Ask a Jira administrator to open the app configuration page and add the current Jira project key to the allowlist.

### The battle window does not open

Confirm that:

- the issue is in an allowed project
- the app has been upgraded after any scope or manifest changes
- the browser allows Jira modals to open
- the user has access to the issue

### A user cannot join as a player

The game may already have two players. Additional users can view the battle as spectators.

### The game result did not update the assignee

Check Jira project permissions, issue security, assignable user settings, and workflow rules. The app must be allowed to update the issue assignee.

### The battle stopped after project configuration changed

If an administrator removes a project key from the allowlist, further battle actions in that project are blocked. Add the project key again to continue using Jira Fortress in that project.

## 11. Support

For support or security questions, contact:

**JMC Labs**  
Email: **wjdals9058@gmail.com**
