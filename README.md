# carim-discord-bot-heroku

This repo is for deploying the Carim Discord Bot using Heroku

## Steps

1. Set up a [free Heroku account](https://signup.heroku.com/signup/dc)
1. Follow [Heroku set up instructions](https://devcenter.heroku.com/articles/getting-started-with-python#set-up)
1. Clone this repository
   + `git clone https://github.com/schana/carim-discord-bot-heroku.git`
1. [Configure the bot](#Configuration)
1. Commit your changes
   + `git add -A`
   + `git commit -m "Added my configuration`
1. Create the Heroku app
   + `heroku create`
   + `git push heroku master`
   + `heroku ps:scale worker=1`
1. You can check the logs to make sure everything is running properly
   + `heroku logs`

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
REQUIRED
  "token" : Discord token for your bot that you can find at https://discordapp.com/developers/applications
  "rcon_ip" : IP address of your DayZ server
  "rcon_port" : RCon port for your DayZ server (may be different from the game port)
  "rcon_password" : RCon password, found in the BattlEye profile directory in your server files
  "steam_port" : Steam query port
OPTIONAL
  Note: if you don't want any of these features, remove the entry from the config.json
  "bot_presence" : Discord presence message for the bot to display
  "bot_presence_type" : Discord presence type from (playing, listening, watching) default: playing
  "rcon_admin_log_channel" : Discord Channel ID to publish admin events to. This will include sensitive info like player IPs
  "rcon_chat_channel" : Discord Channel ID where the linked DayZ to Discord chat will take place
  "rcon_chat_ignore_regex" : Pattern that, if matched, will not publish the message to the chat channel
  "rcon_admin_channels" : List of Discord Channel IDs that can send admin RCon commands
  "rcon_count_channel" : Discord Channel ID that will have its name updated to the current player count
  "update_player_count_interval" : Time, in seconds, between player count update queries
  "rcon_keep_alive_interval" : Time, in seconds, between RCon keep alive messages. The connection times out at around 45 seconds
  "debug" : Set the logging level to DEBUG for the locally running app. Equivalent to running with -v
LOG_EVENTS_IN_DISCORD
  "connect_disconnect_notices" : Send connect and disconnect notices to chat channel
  "player_count_updates" : Send player count update notices to admin log channel
  "rcon_messages" : Send all RCon messages to admin log channel
  "rcon_keep_alive" : Send RCon keep alive status messages to admin log channel
  "include_timestamp" : Include timestamp on all messages from the bot
SCHEDULED_COMMANDS
  "command" : RCon command to run with parameters. Also accepts 'safe_shutdown'. See the template for examples
  "delay" : Only used for 'safe_shutdown'. Specifies the delay in seconds before the shutdown
  "interval" : Interval in seconds between runs of the command
  "with_clock" : Whether the interval should be aligned with the clock instead of relative
  "offset" : Delay in seconds from bot startup to running the command, or offset from midnight if with_clock is true

To get Discord Channel IDs, you need to enable developer mode in the app:
  Settings -> Appearance -> Advanced -> Developer Mode
Then, you will be able to right click on a Channel and select "Copy ID"
```
