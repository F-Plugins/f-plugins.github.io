# <img src="/assets/images/plugins/player-robbing/logo.png" width="45" style="vertical-align: bottom;"/> Player Robbing

Platforms: **OpenMod**  
Price: **$9.99 USD**  
**[Buy on Imperial Plugins](https://imperialplugins.com/Unturned/Products/PlayerRobbing)**

**Simple system using one command and a virtual storage for stealing the items**
**When a player rob someone you can configure to send a message to police members**

---

## Commands

- `/rob` - Starts a rob and opens the virtual inventory for robbing.

---

## Permissions

Grant access to the `/rob` command:

```
PlayerRobbing:commands.rob
```

The permission police officers should have to get notifications

```
PlayerRobbing:police
```

---

## Configuration
??? note "Click to reveal default configuration"
    ```yaml
    requirements:
      cuffs: true # Allows robbing if the player is handcuffed
      hands_up: true # Allows robbing if the player has the hands up
    
    notify_police: true # Player with the PlayerRobbing:police permission will be notified when a player is being robbed
    ```

***

## Translations
??? note "Click to reveal default translations"
    ```yaml
    commands:
      errors:
        already_in_rob: "This player already has a rob in progress"
        requirements: "The target player has to be handcuffed or surrendering"
        player_not_found: "Target player was not found"
    
    police_notification: "{DisplayName} is being robbed near {Location}"
    ```

***

## Installation

1. Run the following commands to install necessary libraries:
  ```
  openmod install SilK.Unturned.Extras
  ```

2. Specify the openmod branch in your Imperial Plugins config.