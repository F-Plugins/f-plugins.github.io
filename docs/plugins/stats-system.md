# <img src="/assets/images/plugins/stats-system/logo.png" width="45" style="vertical-align: bottom;"/> Stats System

Platforms: **OpenMod**  
Price: **$25 USD**  
**[Buy on Imperial Plugins](https://imperialplugins.com/Unturned/Products/Stats-System)**

**Adds Player Stats and Rankings to your server**
**Tracking of player stats such as Kills, Deaths, Accuracy, Kills Deaths Ratio and more**

**Optional customizable and localizable UI**

![UI](https://i.imgur.com/7vNgT60.png)

**Real time customizable and localizable discord leaderboard**

![Discord Leaderboard](https://i.imgur.com/bZ7EyFT.png)

***

## Commands

- `/stats` - Shows your stats.
- `/stats <player name>` - Shows other player stats.
- `/stats toggle` - Hides or Shows the UI.

***

## Permissions

Grant access to the `/stats` command:
```
StatsSystem:commands.stats
```

Grant access to the `/stats toggle` command:
```
StatsSystem:commands.stats.toggle
```

***

## Configuration
??? note "Click to reveal default configuration"
    ```yaml
    Database:
      ConnectionStrings:
        Default: "Server=127.0.0.1; Database=openmod; Port=3306; User=root; Password=admin"

    MessageIconUrl: ""

    Join:
      Message: true

    Rewards: # Type can be: Kills, Headshots and Deaths
      - Type: "Kills"
        Amount: 1
        Commands:
          - "om r add p {Id} noob"
      - Type: "Deaths"
        Amount: 100
        Commands:
          - "kick {DisplayName}" # Can be any command you want and will be executed when Amount is reached

    StatsUI:
      Enabled: true
      EffectId: 55322
      Data: # You can add up to 10 different displays. You can safely remove or add any of this the UI will only show the ones listed here in the given order
        - Type: "Rank"
          Display: "<color=cyan>Rank</color> #{Value}"
        - Type: "Kills"
          Display: "<color=red>Kills</color> {Value}"
        - Type: "Deaths"
          Display: "<color=blue>Deaths</color> {Value}"
        - Type: "KDR"
          Display: "<color=lime>KDR</color> {Value}"
        - Type: "Headshots"
          Display: "<color=yellow>Headshots</color> {Value}"
        - Type: "Accuracy"
          Display: "<color=green>Accuracy</color> {Value}%"

      # Extra Possible display types:
      # - Zombies
      # - MegaZombies
      # - Animals
      # - Fishes
      # - Plants 
      # - Resources

    DiscordLeaderboard:
      Enabled: false
      BotToken: ""
      ChannelId: 0
    ```
***

## Translations
??? note "Click to reveal default translations"
    ```yaml
    # Stats parameters:
    # - Kills
    # - Deaths
    # - KillsDeathRatio 
    # - HeadshotKills
    # - Accuracy (Based on headshot kills)
    # - Zombies
    # - MegaZombies
    # - Animals
    # - Fishes
    # - Plants
    # - Resources

    commands:
      success: 
        stats: "{DisplayName} Rank: #{Rank}\nKills: {Stats.Kills} Deaths: {Stats.Deaths} KDR: {Stats.KillsDeathRatio}" # Supports rich text
      errors:
        not_available: "UI is not available"

    events:
      join: "{DisplayName} ranked #{Rank} connected" # Supports rich text

    discord: # For title and description: {ServerName} {ServerIp} {ServerPort}
      title: "Leaderboard" 
      description: "{ServerName}"
      field: 
        name: "# {Rank} - {DisplayName} - {Id}"
        value: "{Stats.Kills} Kills | {Stats.Deaths} Deaths | {Stats.KillsDeathRatio:N2} KDR | {Accuracy}% Accuracy" # Any stat parameter
    ```
***

## Installation

1. Run the following commands to install necessary libraries:
  ```
  openmod install OpenMod.EntityFrameworkCore.MySql
  ```
  ```
  openmod install Dapper
  ```
  ```
  openmod install SilK.Unturned.Extras
  ```
  ```
  openmod install DSharpPlus.Rest
  ```

2. Specify the openmod branch in your Imperial Plugins config.

3. Add the following workshop id to your WorkshopDownloadConfig.json file:
  ```
  2948787992
  ```

4. Change the connection string in your new `StatsSystem/config.yaml` file to allow StatsSystem to connect to your MySQL server.
