# FSO Tombola Frontend

This repository contains the static frontend for the FSO Tombola app. It is served with GitHub Pages and uses a Google Apps Script Web App as its backend.

## Updating the backend URL

The frontend fetches data from the backend via a secret called `WEBAPP_URL`. When you redeploy the Apps Script backend and get a new Web App URL, follow these steps:

1. Navigate to **Settings → Secrets and variables → Actions** for this repository.
2. Edit the secret named `WEBAPP_URL` and paste the new Apps Script Web App URL. Save the changes.
3. Trigger a redeploy by pushing a commit to the `main` branch (you can update any file or create an empty commit). The GitHub Actions workflow will replace the placeholder in `web/index.html` and deploy the updated site.

## Troubleshooting

- Verify that the Apps Script Web App is deployed with **Execute as: Me** and **Who has access: Anyone**. Otherwise, anonymous users will not be able to call the API.
- Ensure the `WEBAPP_URL` secret is correct and includes the trailing `/exec`; without this the frontend will fail to fetch prizes or post draws.
- Prize stock and visibility are controlled in the Google Sheet. You can edit quantities or deactivate a prize by setting `isActive` to `FALSE` in the `Prizes` sheet.
- If the wheel shows “No prizes found,” check that the `Prizes` tab exists with the proper headers and that prizes are marked as active with remaining quantity.



