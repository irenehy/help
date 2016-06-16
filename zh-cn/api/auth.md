＃ Steedos API Authenticating

Warning: Make sure you're using HTTPS, otherwise this is insecure!

Personal Access Token

Logging In

curl https://us.steedos.com/api/setup/login -d "username=test&password=password"
And the response will look like

{ status: "success", data: {authToken: "f2KpRW7KeN9aPmjSZ", userId: fbdpsNf4oHiX79vMJ} }
You'll need to save the userId and token on the client, for subsequent authenticated requests.

Logging Out

You also have an authenticated POST /api/logout endpoint for logging a user out. If successful, the auth token that is passed in the request header will be invalidated (removed from the user account), so it will not work in any subsequent requests.

curl https://us.steedos.com/api/setup/logout -X POST -H "X-Auth-Token: f2KpRW7KeN9aPmjSZ" -H "X-User-Id: fbdpsNf4oHiX79vMJ"
Authenticated Calls

For any endpoints that require the default authentication, you must include the userId and authToken with each request under the following headers:

X-User-Id
X-Auth-Token
curl -H "X-Auth-Token: f2KpRW7KeN9aPmjSZ" -H "X-User-Id: fbdpsNf4oHiX79vMJ" https://us.steedos.com/api/organizations/