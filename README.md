# carim-discord-bot-heroku

This repo is for deploying the Carim Discord Bot using Heroku

## Steps for initial setup

1. Set up a [free Heroku account](https://signup.heroku.com/signup/dc)
1. Follow [Heroku set up instructions](https://devcenter.heroku.com/articles/getting-started-with-python#set-up)
1. Clone this repository
   + `git clone https://github.com/schana/carim-discord-bot-heroku.git`
   + `cd carim-discord-bot-heroku`
1. [Configure the bot](#Configuration)
1. Commit your changes
   + `git add -A`
   + `git commit -m "Added my configuration"`
1. Create the Heroku app
   + `heroku create`
   + `git push heroku master`
   + `heroku ps:scale worker=1`
1. You can check the logs to make sure everything is running properly
   + `heroku logs`

## Steps to update configuration

1. Make your changes
1. Commit your changes
   + `git add -A`
   + `git commit -m "Updated my configuration"`
1. Update Heroku app
   + `git push heroku master`
   
## Steps to update carim-discord-bot

1. Edit `requirements.txt`
1. Replace `carim-discord-bot` with `carim-discord-bot=={version}`, where `{version}` is the version you want
   + `carim-discord-bot==2.0.0`
1. Commit your changes
   + `git add -A`
   + `git commit -m "Updated bot version"`
1. Update Heroku app
   + `git push heroku master`

## Configuration

For additional help, visit the Carim Discord at https://discord.gg/kdPnVu4

1. Create bot account
   + Follow the guide at https://discordpy.readthedocs.io/en/v1.3.3/discord.html
   + Save the token for later
   + In step 6 under "Creating a Bot Account", make sure "Public Bot" is unticked
   + Under "Inviting Your Bot", step 6 has you setup the permissions for the bot
   + Currently, the bot needs "Manage Channels", "View Channels", "Send Messages", and "Embed Links"

1. Update configuration
   + Edit config.json with your values following the [descriptions here](https://github.com/schana/carim-discord-bot/blob/master/src/carim_discord_bot/data/config_descriptions.json)

   + To get Discord Channel IDs, you need to enable developer mode in the app:
      + Settings -> Appearance -> Advanced -> Developer Mode
   + Then, you will be able to right click on a Channel and select "Copy ID"
