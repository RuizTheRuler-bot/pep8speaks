https://github.com/OrkoHunter/pep8speaks/wiki/Instructions-to-deploy-a-fork
# Instructions to deploy a fork

Note : The simplest (not recommended) solution is to add the bot @RuizTheRuler-bot as a collaborator to the repositories you want this service to work for. But that does not guarantee the privacy of your code. The following instructions are hence written for maintaining the privacy.

## Step 1 : Create a GitHub account
You need to create a GitHub account for the bot. You'll later add this bot as a collaborator to the repositories you want to enable it for. Basically, it should have the access to see and comment wherever it needs to.

## Step 2 : Generate a personal access token
We need an access token of the bot to use its permissions from the command line. While logged in as the bot, go to its Settings. In the bottom left, you may see Personal access tokens menu. Click on the Generate new token. Select whatever scopes you want but we need user, repo and gist scopes for the bot to work. Once generated, keep this token safe for about a minute. We will need it while deploying the app to Heroku.

## Step 3 : Deploy !
Please click on Watch button to get notifications about new releases.

Here's my favorite button of the moment

Deploy

Pick an app name. 

There are some environment variables that you need to add over there. Use the GitHub token we generated in the GITHUB_TOKEN field. Now create a secret and set it to GITHUB_PAYLOAD_SECRET.

## Step 4 : Configure webhooks
Congratulations on deploying your new app ! The url of the app is https://{yourappname}.herokuapp.com and it's ready to receive some requests now. Now, whenever a new PR is created or updated, our app can be notified by using webhooks. Let's configure them.

Go to the settings of the repository you want the service for.
Go to Webhooks. Add a new webhook.
In the Payload URL, enter the url of the app you just deployed i.e. https://{yourappname}.herokuapp.com
Set Content type to application/json
In the Secret field, use the same secret you used while deploying the app on Heroku as the environment variable GITHUB_PAYLOAD_SECRET
In the events, Let me select individual events.
Select Pull Request and Issue Comment and deselect Push event.
Click Add webhook
You're good to go !
Now it is important to note that your pep8speaks bot must have permissions to all the repos you want the service for. In case the Pull Request is created from a secret fork of the secret repository, the bot needs to be added to the fork too as to get the diff of the PR. The process might be a little cumbersome, but hey we don't need a server maintaining any OAuth application. Plus it's free and secure all the way.

Kudos and thanks for using pep8speaks!
