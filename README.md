# Welcome to the FusionAuth Remix Demo!

- [Remix Docs](https://remix.run/docs)
- [Remix Auth](https://github.com/sergiodxa/remix-auth)
- [Remix-Auth-Oauth2 Docs](https://github.com/sergiodxa/remix-auth-oauth2)
- [FusionAuth OAuth Docs](https://fusionauth.io/docs/v1/tech/oauth/endpoints)

## Notes about this Demo
In this demo, sending a GET request (or navigating to) the login route should redirect you to the FusionAuth login page. If you are already logged in, it will return you to the callbackUrl defined in `auth.server.ts`. This callback url must be entered in your FusionAuth App details. The default callback route `/auth/callback` will store the token in your file based session on the server, and issue a session ID that is stored in the client in your session cookie.

You will want to choose a different [session storage method](https://remix.run/docs/en/v1/api/remix#sessions) if you do not have persistent filesystem access on your Remix Deployment target.

The files you will need to copy from this demo to any other Remix app you'd like to try FusionAuth with are:

.gitignore
env.example
package.json
app/auth.server.ts
app/session.server.ts
app/routes/*

Some of these files have the same name as files you likely already have in your Remix app, so be careful!


## Setup
Copy the `env.example` to .env file and enter in your FusionAuth credentials. You'll also need to add the auth callback for your app to the FusionAuth settings.

## Development

Start the Remix development asset server and the Express server by running:

```sh
npm run dev
```

This starts your app in development mode, which will purge the server require cache when Remix rebuilds assets so you don't need a process manager restarting the express server.

## Deployment

First, build your app for production:

```sh
npm run build
```

Then run the app in production mode:

```sh
npm start
```

Now you'll need to pick a host to deploy it to.

### DIY

If you're familiar with deploying express applications you should be right at home just make sure to deploy the output of `remix build`

- `build/`
- `public/build/`

### Using a Template for Deployment

When you ran `npx create-remix@latest` there were a few choices for hosting. You can run that again to create a new project, then copy over your `app/` folder to the new project that's pre-configured for your target server.

```sh
cd ..
# create a new project, and pick a pre-configured host
npx create-remix@latest
cd my-new-remix-app
# remove the new project's app (not the old one!)
rm -rf app
# copy your app over
cp -R ../my-old-remix-app/app app
```

## Shoutouts

Big thank you to Ben Wishovich @benwis who contributed most of this package! Also to @sergiodxa who wrote the remix-auth and remix-auth-oauth2 packages that we rely on here.
