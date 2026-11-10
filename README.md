# WEB 403 — Week 3 Day 1 OAuth exercise

This exercise runs the React Simple OAuth2 Login starter with a GitHub OAuth app. The **Auth code login** button opens GitHub's authorization prompt. After approval, the local Express server exchanges the returned code for an access token.

## Setup

1. Register a GitHub OAuth app. Set its homepage and redirect URI to `http://localhost:1234/`. Copy its client ID and generate a client secret for your local server.
2. From the repository root, install the starter and client dependencies:

   ```sh
   cd react-simple-oauth2
   npm ci --legacy-peer-deps
   cd example/client
   npm ci
   cp -n src/settings.sample.js src/settings-code.js
   cp -n src/settings.sample.js src/settings-implicit.js
   ```

   The starter's older Enzyme dependency declares a React peer version that conflicts with React 16. The first install command accommodates that legacy dependency. The demo client pins React and React DOM to 16.13.1.

3. In `example/client/src/settings-code.js`, set `authorizationUrl` to `https://github.com/login/oauth/authorize` and `clientId` to your GitHub app's client ID. Keep the sample redirect and server URLs. The implicit grant settings copy is required by the starter's imports and can stay blank for GitHub.
4. In a second terminal, open `react-simple-oauth2/example/server` from the repository root and run `cp -n .env.sample .env`. In `.env`, set:

   ```dotenv
   OAUTH_TOKEN_URL=https://github.com/login/oauth/access_token
   OAUTH_CLIENT_ID=YOUR_CLIENT_ID
   OAUTH_CLIENT_SECRET=YOUR_CLIENT_SECRET
   OAUTH_REDIRECT_URI=http://localhost:1234/
   PORT=5000
   ```

5. In the server terminal, run `npm ci` and then `npm start`. In the client terminal, run `npm start`. Open [localhost:1234](http://localhost:1234/) and select **Auth code login**.

The local settings and server `.env` are ignored by Git. Keep the client secret and any displayed access token private.
