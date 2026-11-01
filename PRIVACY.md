# Privacy

Decision Guard is a Forge app. It runs on Atlassian ("Runs on Atlassian") and keeps its data in Forge storage on your own Atlassian site.

## What it stores

- **Flags:** the issue key, decision id and title, the page link, the verified quote, the reason, and who proposed, approved or dismissed it (Atlassian account IDs) with timestamps.
- **Audit log:** each check and approval for an issue: the event, the account ID of the user, a timestamp, and short details such as the search text (up to 200 characters of the issue text), the decision ids found, and checked quotes.

It reads Jira issues and Confluence pages as the signed-in user, and only stores the pieces listed above.

## What it does not do

- It sends nothing outside Atlassian. The app has no external network access.
- No analytics, no tracking, no ads.
- It writes to Jira (a comment and a link) only when a person clicks Approve.

## Logs

Forge keeps short technical logs (for example "decision pages found: 3"). Site admins can turn off log sharing with the developer in Atlassian Administration > Connected apps.

## Deletion

Uninstalling the app removes its Forge storage from your site. Comments and links that people approved stay on the Jira issue, like any other comment.

## Contact

devybuchi@gmail.com
