# <img src="/assets/images/plugins/hitman/logo.png" width="45" style="vertical-align: bottom;"/> Hitman

Platforms: **OpenMod**  
Price: **$12 USD**  
**[Buy on Imperial Plugins](https://imperialplugins.com/Unturned/Products/Hitman)**

**Add a sleek UI for the hitmen on your server!**

Using this plugin, players can place hits on other players and your hitmen will see the top hits with a nice UI.

![Hitman UI Example](/assets/images/plugins/hitman/ui.png)

***

## Usage

Players can simply use /hit to place hits on players.
Players with the `Hitman:ui` permission will be able to see the UI. See the media on this page to view an example of the UI.
You can choose to have the on the left or right hand side by changing the configuration.

***

## Commands

- `/hit <player> <bounty>` - Places a hit on the target player for the given amount.

- `/hitsui` - Toggles the Hitman UI.

***

## Permissions

Grant access to the `/hit` command:
```
Hitman:commands.hit
```

Grant access to receive awards for killing players with hits:
```
Hitman:hitman
```

Grant access to see the Hitman UI:
```
Hitman:ui
```

Grant access to the `/hitsui` command:
```
Hitman:commands.hitsui
```

Grant access to be exempt from hits. Hits cannot be placed on players with this permission.
```
Hitman:exempt
```

***

## Configuration
??? note "Click to reveal default configuration"
    ```yaml
    hits:
      duration: 1 day # Time until hit expires
      checkInterval: 30 seconds # Time between checks for expired hits
      canPlaceOnSelf: false # Whether or not players can place hits on themselves
      minimumBounty: 100 # Minimum bounty for a hit
      refundExpired: false # Should refund expired, unclaimed bounties

      placed:
        announce: true # Should announce in the chat when a hit is placed
        tellTarget: true # Should tell the target when a hit is placed on them

      completed:
        announce: true # Should announce in the chat when a hit is completed
        tellTarget: true # Should tell the target when a hit placed on them is completed

      expired:
        tellTarget: true # Should tell the target a hit on them has expired
        tellHirer: true # Should tell the hirer a hit they placed has expired

    ui:
      autoDisplay: true # Show to users by default
      maxHitsShown: 10 # No greater value than ten
      effectId: 29200 # 29200 - Right Side, 29201 - Left Side
    ```

***

## Translations

You can change the color of both UI and command text translations by using [Unity's rich text format](https://docs.unity3d.com/560/Documentation/Manual/StyledText.html).

For example, to change the balance color to blue in the UI, change:
```yaml
header: "Current Hits:"
```
to
```yaml
header: "<color=blue>Current Hits:</color>"
```
or
```yaml
header: "<color=#0000FF>Current Hits:</color>"
```

??? note "Click to reveal default translations"
    ```yaml
    commands:
      success:
        hit_placed:
          hirer: "You have placed a hit on {Target.DisplayName} for {CurrencySymbol}{Bounty:0.00}."
          target: "{Hirer.DisplayName} has placed a hit on you for {CurrencySymbol}{Bounty:0.00}."
          announce: "{Hirer.DisplayName} has placed a hit on {Target.DisplayName} for {CurrencySymbol}{Bounty:0.00}."
      errors:
        invalid_bounty: "The bounty must be greater than {MinimumBounty}."
        cannot_self_place: "You cannot place a bounty on yourself."
        target_hit_exempt: "{Target.DisplayName} cannot have hits placed on them."

    announcements:
      hit_completed:
        target: "{Killer.DisplayName} has claimed the bounty of {CurrencySymbol}{Bounty:0.00} on your head."
        announce: "{Killer.DisplayName} has claimed the bounty of {CurrencySymbol}{Bounty:0.00} on {Target.DisplayName}'s head."
        killer: "You have successfully claimed the bounty of {CurrencySymbol}{Bounty:0.00} on {Target.DisplayName}'s head."
      
      hit_expired:
        target: "A hit placed on your head for {CurrencySymbol}{Bounty:0.00} has expired."
        hirer: "A hit you placed for {CurrencySymbol}{Bounty:0.00} has expired."
      
    transactions:
      hit_placed: "Bounty placed on {Target.DisplayName}"
      hit_completed: "Claimed bounty for {Target.DisplayName}"
      hit_expired: "Bounty refund as hit on {Target.DisplayName} expired"

    ui:
      header: "Current Hits:"
      playerName: "{User.DisplayName}"
      bounty: "{CurrencySymbol}{Bounty:0.00}"
    ```

***

## Installation

1. Run the following command to install necessary libraries:
  ```
  openmod install SilK.Unturned.Extras
  ```

2. Specify the openmod branch in your Imperial Plugins config.

3. Add the following workshop id to your WorkshopDownloadConfig.json file:
  ```
  2419939859
  ```

4. Change the connection string in your new `Hitman/config.yaml` file to allow Hitman to connect to your MySQL server.

***

## Credits

Original inspiration for this plugin comes from Teesxm of Game Ghost Servers.