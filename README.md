# jessestallsworthwebsite

## Owner editor sign-in

The editor is available only after GitHub Device Flow sign-in as `jessebstallsworth-oss`.

1. Create a GitHub OAuth App under **Settings > Developer settings > OAuth Apps**.
2. Set its homepage URL to `https://jessebstallsworth.com` and enable **Device Flow**. No client secret or callback URL is used.
3. On the website, choose **Sign in**, enter the app's client ID, then authorize the displayed device code with GitHub.

The app requests only the `read:user` scope. The client ID is saved in local storage; the access token stays in session storage and is cleared on sign-out or when the browser session ends. Editing remains local to the browser and can be exported with **Data**; it does not publish changes to the live site.