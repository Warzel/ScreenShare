# 💻 ScreenShare 1.0 by warzelous 💻

## ⚡ Overview
ScreenShareManager is an essential Spigot plugin to enhance and protect your Minecraft server's "Screen Share (SS) check" process. It provides advanced tools for staff to conduct extensive investigations with full control over a suspected player's actions, ensuring a balanced and optimized environment for thorough checks.

## ✨ Main features
- **Dedicated SS Check Environment:** When a player is flagged for an SS check, they are instantly put into a controlled environment where their actions are heavily restricted.
- **Configurable Action Blocking:** Prevent players undergoing an SS check from:
  - Moving
  - Interacting with blocks or entities
  - Breaking blocks
  - Placing blocks
  - Taking damage
  - Dropping/picking up items
  - Executing unauthorized commands (configurable)
- **Punishment for Evasion:** Automatically execute customizable console command(s) (e.g., a ban) if a player disconnects during an active SS check.
<br>This prevents players from deleting any illegal mods and doing similar actions.
- **Clear Player Communication:**
  - **Persistent SS Title:** Display a prominent title and subtitle on the player's screen with constant instructions.
  - **Timed Instructions:** Send an initial instructional chat message, accompanied by a sound, guiding the player to your Discord for the check.
- **Controlled Chat Sessions:** Staff can join and leave individual player SS sessions to communicate directly with the suspected player, isolating session chat from the main server.
- **Flexible Message Templates:** All player-facing messages (chat, action bar, titles, sounds) are fully customizable via a robust template system, allowing for complete localization and branding.
- **Discord Webhook Integration:** Optionally send real-time notifications to a Discord channel for SS check starts and conclusions (whether a player is released or punished), keeping your staff team informed.
- **Permissions Bypass:** Players with the screenshare.bypass permission cannot be put into an SS check.
- **Comprehensive Command Feedback:** Clear and concise messages for various scenarios like missing permissions, player not found, incorrect command usage, and more.
- **Customizable Prefix:** Define a unique chat prefix for all plugin messages, supporting Minecraft color and formatting codes.


<details>
<summary>Configuration file</summary>
## ⚙️ Configuration

```yaml
#   ░██████╗███████╗████████╗████████╗██╗███╗░░██╗░██████╗░░██████╗
#    ██╔════╝██╔════╝╚══██╔══╝╚══██╔══╝██║████╗░██║██╔════╝░██╔════╝
#    ╚█████╗░█████╗░░░░░██║░░░░░░██║░░░██║██╔██╗██║██║░░██╗░╚█████╗░
#    ░╚═══██╗██╔══╝░░░░░██║░░░░░░██║░░░██║██║╚████║██║░░╚██╗░╚═══██╗
#    ██████╔╝███████╗░░░██║░░░░░░██║░░░██║██║░╚███║╚██████╔╝██████╔╝
#    ╚═════╝░╚══════╝░░░╚═╝░░░░░░╚═╝░░░╚═╝╚═╝░░╚══╝░╚═════╝░╚═════╝░
# This configuration file is for a Minecraft plugin designed to manage "Screen Share (SS) checks."

# PREFIX
# Defines a custom prefix to be prepended to chat messages.
# Use '%PREFIX%' in any configurable string to include this defined prefix.
# Supports Minecraft color and formatting codes (e.g., '§' or '&').
prefix: "§x§E§F§3§4§3§4[§x§F§0§3§6§3§3S§x§F§1§3§7§3§2c§x§F§2§3§9§3§2r§x§F§3§3§B§3§1e§x§F§4§3§C§3§0e§x§F§5§3§E§2§Fe§x§F§6§4§0§2§Fn§x§F§7§4§1§2§ES§x§F§8§4§3§2§Dh§x§F§9§4§4§2§Ca§x§F§A§4§6§2§Br§x§F§B§4§8§2§Be§x§F§C§4§9§2§A] §r§f"

# PUNISHMENT COMMANDS
# Commands to be executed by the console if a player leaves the server during an SS check.
# Multiple commands can be listed and will be executed sequentially.
# Placeholders:
# - %TARGET%: The nickname of the player who left during the SS check.
punish-commands:
  - ban %TARGET% §cLeft during SS check.

# EVENT CANCELLATIONS
# In this section, you can configure which actions are blocked for players undergoing an SS check.
# Setting a value to 'true' will prevent the action, while 'false' will allow it.
block-movement: true # Prevents players from moving.
block-interactions: true # Prevents players from interacting with blocks or entities.
block-breaking: true # Prevents players from breaking blocks.
block-placing: true # Prevents players from placing blocks.
filter-commands: true # Filters and potentially blocks certain commands for players.
block-damage: true # Prevents players from taking damage.
block-item-dropping: true # Prevents players from dropping items.
block-item-pickuping: true # Prevents players from picking up items.

# ALLOWED COMMANDS executable by trapped players
# Only one word string (command names) are expected in this list.
alowed-commands:
  - discord

# SS CHECK TITLE
# The main title and subtitle displayed on the player's screen when they are in an SS check.
# These are standard Spigot title messages and support Minecraft color and formatting codes ('§' or '&').
# This title remains visible for the entire duration of the SS check without fade effects.
ss-title:
  big: "§4§l⚠  SS check  ⚠" # The main title text.
  small: "§cPlease join the channel 'waiting room' on our Discord." # The smaller subtitle text.

# SS CHECK CHAT INSTRUCTION
# A message sent to the player approximately one second (20 ticks) after they are flagged for an SS check.
# This message is accompanied by a sound.
# Placeholders:
# - %PREFIX%: The defined message prefix.
# - %TARGET%: The nickname of the player currently in the SS check.
# - %PLAYER%: Refers to the same player as %TARGET% in this context.
ss-instruction: "%PREFIX% §fYou've been flagged for an SS check. Please join the “waiting room” channel on our Discord and wait for your transfer by our staff team. Our Discord can be found under /discord. You have 5 minutes to get here."
ss-instruction-sound: "ENTITY_GUARDIAN_ATTACK" # The ID of the sound to play. See Spigot documentation for a list of sound IDs.
ss-instruction-sound-volume: 1.0 # The volume of the sound. Recommended to stay below 10.0.
ss-instruction-sound-pitch: 1.0 # The pitch of the sound. Recommended to stay below 10.0.

# SESSION CHAT FORMAT
# The format for chat messages sent within an SS session.
# Placeholders:
# - %PREFIX%: The defined message prefix.
# - %PLR%: The nickname of the player sending the message within the session.
# - %MSG%: The content of the chat message.
session-chat-format: "%PREFIX% &8(Session) &f%PLR%&8: &f%MSG%"


#   ███╗░░░███╗███████╗░██████╗░██████╗░█████╗░░██████╗░███████╗░██████╗
#   ████╗░████║██╔════╝██╔════╝██╔════╝██╔══██╗██╔════╝░██╔════╝██╔════╝
#   ██╔████╔██║█████╗░░╚█████╗░╚█████╗░███████║██║░░██╗░█████╗░░╚█████╗░
#   ██║╚██╔╝██║██╔══╝░░░╚═══██╗░╚═══██╗██╔══██║██║░░╚██╗██╔══╝░░░╚═══██╗
#   ██║░╚═╝░██║███████╗██████╔╝██████╔╝██║░░██║╚██████╔╝███████╗██████╔╝
#   ╚═╝░░░░░╚═╝╚══════╝╚═════╝░╚═════╝░╚═╝░░╚═╝░╚═════╝░╚══════╝╚═════╝░
# MESSAGE TEMPLATES
# This section defines various standardized message templates used throughout the plugin.
# Each template is configured under a specific 'configKey' and can include chat messages, action bar messages, titles, and sounds.
#
# Structure for each 'configKey':
# <configKey>:
#   chat: "Message sent to the player's chat."
#     # Leave empty or omit to disable chat messages for this template.
#   actionbar: "Message appearing above the player's action bar."
#     # Leave empty or omit to disable action bar messages for this template.
#   title:
#     big: "The main title text."
#     small: "The smaller subtitle text."
#       # To disable title messages, set both 'big' and 'small' to "" or omit them.
#     in: <ticks> # Amount of ticks for the fade-in effect (20 ticks = 1 second).
#     hold: <ticks> # Amount of ticks the title remains fully visible.
#     out: <ticks> # Amount of ticks for the fade-out effect.
#   sound:
#     id: "SOUND_ID" # The ID of the sound to play (e.g., "BLOCK_NOTE_BLOCK_PLING").
#       # A list of Spigot sound IDs can be found here: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Sound.html
#       # Set to "" or omit to disable sound for this template.
#     volume: <value> # The volume of the sound (default: 1.0; must be > 0, recommended below 10.0).
#     pitch: <value> # The pitch of the sound (default: 1.0; must be > 0, recommended below 10.0).

# Example of a message template:
#
# helloworld:
#  chat: "%PREFIX% &aHello, %PLR%!"
#  actionbar: "&aHello there, %PLR%!"
#  title:
#    big: "&aGOOD DAY"
#    small: "&fHave a nice day, %PLR%!"
#    in: 10
#    hold: 30
#    out: 10
#  sound:
#    id: "BLOCK_NOTE_BLOCK_PLING"
#    volume: 1
#    pitch: 1.5

# ADMIN SESSION WARNING
# This message reminds an administrator that they are currently in an SS session, where chat communication with other players is disabled.
# Administrators must use '/ss .session. leave <player name>' to exit the session.
# This warning is displayed every 2 seconds.
# Placeholders:
# - %PLR%: The administrator's nickname.
# - %TARGET%: The nickname of the player being screened.
sessionwarn:
  actionbar: "&4! You are in an SS session of %TARGET% !" # Only an action bar message is supported for this warning.

# NO PERMISSION MESSAGE
# Message displayed when a player attempts to use a command without the necessary permissions.
# Placeholders:
# - %PREFIX%: The defined message prefix.
noperm:
  chat: "%PREFIX% &cYou do not have permission to use this command!"

# ONLY PLAYERS MESSAGE
# Message displayed when a command can only be used by players (not console).
# Placeholders:
# - %PREFIX%: The defined message prefix.
only-players:
  chat: "%PREFIX% &cOnly players can use this command!"

# COMMAND USAGE MESSAGE
# Message providing correct command usage syntax.
# Placeholders:
# - %PREFIX%: The defined message prefix.
command-usage-two:
  chat: "%PREFIX% &cUsage: /ss .session. <join/leave> <target>" # Usage message for incorrect arguments after ".session."

# TRAP YOURSELF MESSAGE
# Message displayed when a player attempts to put themselves into an SS check.
# Placeholders:
# - %PREFIX%: The defined message prefix.
trap-yourself:
  chat: "%PREFIX% &cYou can not SS trap yourself!"

# PLAYER NOT FOUND MESSAGE
# Message displayed when the specified player cannot be found.
# Placeholders:
# - %PREFIX%: The defined message prefix.
player-not-found:
  chat: "%PREFIX% &cThis player could not be found."

# TRAP BYPASS MESSAGE
# Message displayed when an administrator attempts to SS trap a player who has the "screenshare.bypass" permission.
# Players with this permission cannot be flagged for an SS check.
# Placeholders:
# - %PREFIX%: The defined message prefix.
trap-bypass:
  chat: "%PREFIX% &cYou can not SS trap that player!"

# SET FREE MESSAGES
# Messages displayed when a player is released from an SS check.
set-free:
  admin:
    chat: "%PREFIX% &aPlayer %TARGET% was set free." # Message for the administering player.
    # Placeholders: %PREFIX%, %TARGET%
  target:
    chat: "%PREFIX% §aYou have been set free of the SS check." # Message for the released player.
    # Placeholders: %PREFIX%

# TRAP MESSAGES
# Messages displayed when a player is put into an SS check.
trap:
  admin:
    chat: "%PREFIX% &aPlayer %TARGET% has been trapped." # Message for the administering player.
    # Placeholders: %PREFIX%, %TARGET%
  target:
    chat: "%PREFIX% §cYou have been trapped for an SS check! Leaving the server in this state will be punished." # Message for the trapped player.
    # Placeholders: %PREFIX%

# PLAYER NOT IN SESSION MESSAGE
# Message displayed when an attempt is made to interact with a player who is not in an SS session.
# Placeholders:
# - %PREFIX%: The defined message prefix.
player-not-in-session:
  chat: "%PREFIX% &cThis player is not currently in an SS session."

# ALREADY IN SESSION MESSAGE
# Message displayed when an administrator attempts to join an SS session they are already monitoring.
# Placeholders:
# - %PREFIX%: The defined message prefix.
already-in-session:
  chat: "%PREFIX% &cYou are already monitoring this player's SS session."

# JOIN SESSION MESSAGES
# Messages displayed when an administrator joins a player's SS session.
join-session:
  admin:
    chat: "%PREFIX% &aYou have joined %TARGET%'s SS session." # Message for the administering player.
    # Placeholders: %PREFIX%, %TARGET%
  target:
    chat: "%PREFIX% §aAn admin '%ADMIN%' has joined your SS session." # Message for the player in the SS check.
    # Placeholders: %PREFIX%, %ADMIN% (nickname of the joining admin)

# LEAVE SESSION MESSAGES
# Messages displayed when an administrator leaves a player's SS session.
leave-session:
  admin:
    chat: "%PREFIX% &aYou have left %TARGET%'s SS session." # Message for the administering player.
    # Placeholders: %PREFIX%, %TARGET%
  target:
    chat: "%PREFIX% §aAn admin '%ADMIN%' has left your SS session." # Message for the player in the SS check.
    # Placeholders: %PREFIX%, %ADMIN% (nickname of the leaving admin)

# DISCORD INTEGRATION
# Configuration for sending messages to Discord via a webhook.
discord:
  webhook-url: "YOUR_DISCORD_WEBHOOK_URL_HERE" # Replace with your actual Discord webhook URL.
  # Set to an empty string ("") to disable Discord integration.

  messages:
    # Message sent when an SS check starts.
    ss-start:
      enabled: true
      # You can use Discord's Markdown for formatting here.
      # Placeholders: %STAFF%, %TARGET%
      content: |
        # SS Check Started!
        🕵️‍♂️ Staff: ** %STAFF% **
        🎮 Player: ** %TARGET% **
        Join session: `/ss .session. join %TARGET%`

    # Message sent when an SS check ends (player released).
    ss-end-released:
      enabled: true
      # Placeholders: %STAFF%, %TARGET%
      content: |
        # ✅ SS Check Concluded - Player Released!
        🕵️‍♂️ Staff: ** %STAFF% **
        🎮 Player: ** %TARGET% **

    # Message sent when an SS check ends (player punished, e.g., left during SS).
    ss-end-punished:
      enabled: true
      # Placeholders: %STAFF%, %TARGET%, %PUNISHMENTS%
      content: |
        # ❌ SS Check Concluded - Player Punished!
        🕵️‍♂️ Staff: ** %STAFF% **
        🎮 Player: ** %TARGET% **
        🔧 Punishments: ** %PUNISHMENTS% **
```

</details>


## 🚀 Installation
1. Download `ScreenShare-1.0.jar` file from official [spigot page](https://www.spigotmc.org/resources/screenshare.126348/). **Do not download this plugin from any other source! It might be malicious!**
2. Place the `ScreenShare-1.0.jar` file into your server's plugins/ folder.
3. Restart your Minecraft server.
4. The config.yml will be generated in plugins/ScreenShare/. Edit it to fit your server's needs.
5. Restart your server again for the configuration changes to take effect.

## ⌨️ Commands & Permissions
| Command                        | Description                                                            | Permission                                 |
|--------------------------------|------------------------------------------------------------------------|--------------------------------------------|
| `/ss <player>`                 | Traps/frees a player from an SS session.                               | `screenshare.trap` <br> `screenshare.free` |
| `/ss .session. join <player>`  | Joins a trapped player's session as an admin.                          | `screenshare.joinsession`                  |
| `/ss .session. leave <player>` | Leaves a session of a trapped player.                                  | `screenshare.leavesession`                 |
| N/A                            | Disallows to trap players with this permission in an SS check session. | `screenshare.bypass`                       |
**All these permissions are defaultly assigned to all OP players.**

## 📞 Support & Contribution
If you encounter any issues, have suggestions, or wish to contribute, please message me through Discord DMs - `@warzelous`. I will have a Discord server very soon.
