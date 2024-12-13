1. Resource Group
• Resource Group Name: cms

2. SQL Database
• DB name: cms1234
• Server: cms1234.database.windows.net
• DB region: us-east
• Admin login: cmsadmin
• Admin password: Cms4dmin
• Resource group: cms
• DB workload env: Development
• DB compute + storage: DTU - Basic
• Press the "Next: Networking" button, then select "Public Endpoint", and set both of the Firewall rules that appear to "Yes".
• Set everything else to default
• Run SQL queries in sql_scripts/ directory after completion, starting from the users table. Don't forget to take screenshots.

3. Storage Account
• Resource group: cms
• Storage account name: images12323 (needs to be unique)
• Advanced - Allow enabling anonymous access on individual containers: Enable
• Advanced - Access tier: Cool
• Network access: Enable public access from all networks (the default)
• Create container named "images". Set its access level to Container.
• From Security + networking > Access keys:
• Blob Storage key: Zao9mBxHkMX50XbtKiaesksW3F8JJk9Xdbu70MrpCO96I3QU+/+H6dWEs6GEdErJQ+icQZoZBxor+AStNzo4Ww==
• Blob Connection String: DefaultEndpointsProtocol=https;AccountName=images12323;AccountKey=Zao9mBxHkMX50XbtKiaesksW3F8JJk9Xdbu70MrpCO96I3QU+/+H6dWEs6GEdErJQ+icQZoZBxor+AStNzo4Ww==;EndpointSuffix=core.windows.net

4. Microsoft Entra ID
4.1. App Registration
• Name: cmsEntraID
• Who can use? "Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)"
4.2. Secret Creation
• Secret description: test
• Secret Key: 3445dd15-e735-40b6-8a1e-089f691d8228 # AKA the secret ID
• Client Secret: ibU8Q~eMTkYohSjp86zv8VygDsrj74hzYXuaubYm # AKA the Value
• Application (client) ID: c4477608-dda6-40f4-b374-7bb8dd2f2941


5. Application
5.2. OPTION 2: Web App (easier)
• Name: udacitycms.azurewebsites.net
• Runtime stack: Python 3.10
• Pricing Plan: Free F1
• If you are getting a "Validation failed for a resource" error, pick a different region.
After creation:
• Settings -> Environment variables - Add the following variables (sample values are included, replace them with your values):
• BLOB_ACCOUNT: cms1321
• BLOB_CONTAINER: images
• BLOB_STORAGE_KEY: Zao9mBxHkMX50XbtKiaesksW3F8JJk9Xdbu70MrpCO96I3QU+/+H6dWEs6GEdErJQ+icQZoZBxor+AStNzo4Ww==
• BLOB_CONNECTION_STRING: DefaultEndpointsProtocol=https;AccountName=images12323;AccountKey=Zao9mBxHkMX50XbtKiaesksW3F8JJk9Xdbu70MrpCO96I3QU+/+H6dWEs6GEdErJQ+icQZoZBxor+AStNzo4Ww==;EndpointSuffix=core.windows.net
• SQL_SERVER: cms1234.database.windows.net
• SQL_DATABASE: cms1234
• SQL_USER_NAME: cmsadmin
• SQL_PASSWORD: Cms4dmin
• CLIENT_SECRET: ibU8Q~eMTkYohSjp86zv8VygDsrj74hzYXuaubYm # AKA the Value
• SECRET_KEY: 3445dd15-e735-40b6-8a1e-089f691d8228 # AKA the secret ID
• CLIENT_ID: c4477608-dda6-40f4-b374-7bb8dd2f2941
• Deployment Center
• Source: GitHub
• Pick the repo that contains the starter files.

6. Setting up OAuth2
At this point, your application should already be running. You should already be able to log in with username admin and password pass and you can create new posts or update existing ones.
The next part is getting the OAuth2 login to work.
Go to Microsoft Entra ID > App Registrations, click on the App Registration created earlier, and then pick Authentication from the left sidebar.
6.1. Microsoft Entra ID - Authentication - Add a Platform - Web
• Redirect URIs: https://[IP ADDRESS FROM VM or WEB APP ADDRESS]/getAToken
• logout URL: https://[IP ADDRESS FROM VM or WEB APP ADDRESS]/login

    ```bash
    brew install unixodbc
    ```
- Check [here](https://docs.microsoft.com/en-us/sql/connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos?view=sql-server-ver15) to add SQL Server drivers for Mac.
