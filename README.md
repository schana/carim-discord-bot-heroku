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
   + `git commit -m "Added my configuration"`
1. Update Heroku app
   + `git push heroku master`
   
## Steps to update carim-discord-bot

1. Edit `requirements.txt`
1. Replace `carim-discord-bot` with `carim-discord-bot=={version}`, where `{version}` is the version you want
   + `carim-discord-bot==1.4.0a1`
1. Commit your changes
   + `git add -A`
   + `git commit -m "Added my configuration"`
1. Update Heroku app
   + `git push heroku master`

## Configuration

```text
+----------------------------------------------+
| Setup instructions for the Carim Discord Bot |
+----------------------------------------------+
For additional help, visit the Carim Discord at https://discord.gg/kdPnVu4

+--------------------+
| Create bot account |
+--------------------+
Follow the guide at https://discordpy.readthedocs.io/en/v1.3.3/discord.html
Save the token for later

In step 6 under "Creating a Bot Account", make sure "Public Bot" is unticked

Under "Inviting Your Bot", step 6 has you setup the permissions for the bot
Currently, the bot needs "Manage Channels", "View Channels", "Send Messages", and "Embed Links"

+----------------------+
| Update configuration |
+----------------------+
Edit config.json with your values following the descriptions below:
GLOBAL
  "token" : Discord token for your bot that you can find at https://discordapp.com/developers/applications
  "presence" : Discord presence message for the bot to display
  "presence_type" : Discord presence type from (playing, listening, watching) default: playing
  "log_player_count_updates" : Send player count update notices to admin log channel
  "debug" : Set the logging level to DEBUG for the locally running app. Equivalent to running with -v
SERVERS
  "ip" : IP address of your DayZ server
  "rcon_port" : RCon port for your DayZ server (may be different from the game port)
  "rcon_password" : RCon password, found in the BattlEye profile directory in your server files
  "steam_port" : Steam query port
  "admin_channel_id" : Discord Channel ID that can send admin RCon commands and where logs are sent
  "chat_channel_id" : Discord Channel ID where the linked DayZ to Discord chat will take place
  "chat_ignore_regex" : Pattern that, if matched, will not publish the message to the chat channel
  "chat_show_connect_disconnect_notices" : Send connect and disconnect notices to chat channel
  "player_count_channel_id" : Discord Channel ID that will have its name updated to the current player count
  "player_count_format" : Format for setting the channel name using {players} and {slots} as placeholders for the values
  "player_count_update_interval" : Time, in seconds, between player count update queries
  "log_rcon_messages" : Send all RCon messages to admin log channel
  "log_rcon_keep_alive" : Send RCon keep alive status messages to admin log channel
SCHEDULED_COMMANDS
  "command" : RCon command to run with parameters. Also accepts 'safe_shutdown'. See the template for examples
  "delay" : Only used for 'safe_shutdown'. Specifies the delay in seconds before the shutdown
  "interval" : Interval in seconds between runs of the command
  "with_clock" : Whether the interval should be aligned with the clock instead of relative
  "offset" : Delay in seconds from bot startup to running the command, or offset from midnight if with_clock is true
CUSTOM_COMMANDS
  "enabled" : Whether the command is enabled
  "channels" : List of channel ids to enable the command for. If not present or empty, command will work in every channel
  "command" : Regex pattern that, if matched, will trigger the command
  "response" : Discord embed object as described by https://discord.com/developers/docs/resources/channel#embed-object

To get Discord Channel IDs, you need to enable developer mode in the app:
  Settings -> Appearance -> Advanced -> Developer Mode
Then, you will be able to right click on a Channel and select "Copy ID"
```
