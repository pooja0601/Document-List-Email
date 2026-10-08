# Document Request Desk

A small web app for accounting practices that writes client document request emails from a reusable checklist.

Instead of retyping the same "please send us…" email for every client, you keep one master list of documents, bundle them into groups (for example *New client* or *Rental property*), and generate a ready-to-send email in a few clicks.

## Features

- **Document library**: a master list of documents, each with a short note for the client (e.g. "Driver licence or passport, front and back"). You can reorder, edit and delete items.
- **Groups**: named bundles of documents, such as *New client* → photo ID, TFN, prior-year notice of assessment, bank details, engagement letter.
- **Combine groups**: select more than one group (e.g. *Existing client* + *Rental property*) and the checklist merges them without duplicates.
- **Per-client adjustments**: tick or untick individual items and add one-off requests for a specific client.
- **Email preview**: the subject and body are generated live and can be edited before sending.
- **One-click drafts**: opens a pre-filled draft in Gmail, Outlook (Microsoft 365 or Outlook.com), Yahoo Mail or your default mail app.
- **Templates**: the opening paragraph, upload instructions, closing and sign-off are configurable, with placeholders such as `{client}`, `{first_name}`, `{fy}` and `{due}`.
- **Sent log**: a history of who was sent which request, and when.
- **Google Drive folder reader**: paste a Drive folder link to see its full folder structure and file names as a collapsible tree, and copy it as plain text. It uses the read-only `drive.metadata.readonly` permission, so files are never opened or downloaded.

## Tech

- A single `index.html` file in vanilla HTML, CSS and JavaScript, with no build step and no dependencies.
- Data is stored in the browser's `localStorage`. The only outside calls are to Google, and only when you read a Drive folder.
- Responsive layout with light and dark themes.

## Running it

Open `index.html` in any modern browser, or host it for free with GitHub Pages:

1. Go to the repository's **Settings → Pages**.
2. Under *Build and deployment*, choose **Deploy from a branch**, then select `main` and `/ (root)`.
3. The app will be live at `https://<your-username>.github.io/document-request-desk/`.

## Google Drive setup (one-time)

The folder reader signs in with Google, so it needs a free OAuth Client ID:

1. Create a project at [console.cloud.google.com](https://console.cloud.google.com/).
2. Enable the **Google Drive API**.
3. Set up the **OAuth consent screen** (External) and add yourself as a test user.
4. Create an **OAuth client ID** of type *Web application*, and add your site's address (e.g. `https://<your-username>.github.io`) under *Authorised JavaScript origins*.
5. Paste the Client ID into the app under **Drive folder → Google setup**.

Sign-in needs the app to be served from a web address (GitHub Pages or a local server such as `python3 -m http.server`). It won't work from a file opened directly from your computer.

## Privacy note

The app never sends emails or client data anywhere itself. It only opens a draft in your own mail service, and you review it and press Send there.
