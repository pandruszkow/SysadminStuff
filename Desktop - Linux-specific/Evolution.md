## Email access to Office 365 with MFA

When MFA is enforced on an Office 365 account, Evolution will no longer work with standard authentication and will need to switch to OAuth2 authentication. You will have to change the account settings to receive email again.

1. Ask your email admin for the Azure Tenant ID and the Application (Client) ID under the Application Registration of Azure Active Directory. You will need these values for the next step.
2. Open Evolution, then go to `Edit -> Preferences`
3. Under the "Mail Accounts" section, select your email account and click `Edit`
4. Go to the `Receiving Email` tab
5. Under `Authentication`, select `OAuth2 (Office365)` as the authentication type.
6. Tick `Override Office365 OAuth2 settings`, and input the details from Step 1 into the corresponding boxes. Enter `https://login.microsoftonline.com/common/oauth2/nativeclient` as your `Redirect URI`.
7. Click OK. On your next login attempt, Evolution should pop up a mini-browser window with the login form. Log in as you would normally do in-browser.
8. Done. You should now be able to receive email in Evolution again.

(Instructions last tested on 2022-07-04. With thanks to Sebastian Baszcyj at Insentra - https://www.insentragroup.com/us/insights/geek-speak/professional-services/evolution-mail-agent-with-ews-and-multi-factor-authentication/)
