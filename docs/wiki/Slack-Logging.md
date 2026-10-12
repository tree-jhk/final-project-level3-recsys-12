# Sending logs to Slack

Connecting to a server to inspect every backend, crawling or training log is inconvenient. After deployment, signup events, service usage, selected products and recommendation outputs also benefit from accessible monitoring.

The team added Slack-bot support and a helper function to send selected Python logs to a channel.

## Workflow

1. Keep the Slack token in a local repository-root `secrets.yaml`, excluded from Git.

<img src = "https://user-images.githubusercontent.com/90206705/217552525-c5235c55-b77f-48b2-b704-9db2bbefc882.png" weight=600px height=200px>

2. Load the token and define the posting function.

<img src = "https://user-images.githubusercontent.com/90206705/217552728-52ba6777-722c-49ce-854e-f7dba90dcda5.png" weight=600px height=200px>

**Code-comment translation:** 'Slack connection'. The example reads Slack configuration from `secrets.yaml`, then posts a message to the `#serverlog` channel through `chat.postMessage`; the configuration values are not shown in the image.

3. Call `post_slack_message` where a notification is useful; the text argument becomes the Slack message.

<img src = "https://user-images.githubusercontent.com/90206705/217552771-dba0191b-df79-4b1f-b7ca-dd5149804624.png" weight=600px height=200px>

**Slack UI translation:** 'App' identifies ServerLog-bot as an application; the Korean time labels mean 4:32 PM and 5:28 PM. The visible test messages demonstrate successful posting, not a record of production monitoring.

This was useful during development and service monitoring. Never expose a token or rely on automatic revocation as protection. Treat event logs as potentially sensitive and limit what is sent to shared channels.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Slack%EC%97%90-%EB%A9%94%EC%84%B8%EC%A7%80-%EB%B3%B4%EB%82%B4%EA%B8%B0)
