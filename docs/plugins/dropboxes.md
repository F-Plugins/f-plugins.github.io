# <img src="/assets/images/plugins/dropboxes/logo.png" width="45" style="vertical-align: bottom;"/> Drop Boxes

Platforms: **OpenMod**  
Price: **$15 USD**  
**[Buy on Imperial Plugins](https://imperialplugins.com/Unturned/Products/DropBoxes)**

**Add loot boxes to your server!**

Using this plugin, players can find or be given loot boxes which contain rewards you configure.

**UI support coming soon!**

***

## Usage

Players can naturally find these loot boxes by doing a range of normal activities in the game. Check out the [Configuration](#configuration) section for more details.

Loot boxes can also be directly given to players for use in donation systems and other custom applications.

***

## Commands

- `/unbox <box>` - Unbox a loot box.
  Requires the `DropBoxes:commands.unbox` permission.

- `/boxes` - View your loot boxes.
  Requires the `DropBoxes:commands.boxes` permission.

- `/givebox <player> <box>` - Give an online player a loot box.
  Requires the `DropBoxes:commands.givebox` permission.

- `/giveboxbyid <steam id> <box>` - Give the player with the steam ID a loot box.
  Requires the `DropBoxes:commands.giveboxbyid` permission.

***

## Permissions

### Basic User Permissions

Grant access to the `/unbox` command:
```
DropBoxes:commands.unbox
```

Grant access to the `/boxes` command:
```
DropBoxes:commands.boxes
```

### Administrative Permissions

Grant access to the `/givebox` command:
```
DropBoxes:commands.givebox
```

Grant access to the `/giveboxbyid` command:
```
DropBoxes:commands.giveboxbyid
```

***

## Configuration

??? note "Click to reveal default configuration"
    ```yaml
    # Each loot box has a configuration.
    # BoxId - The unique id for this loot box. Used for storing in the database.
    # Name - The display name for this loot box. This is displayed to the user.
    # Permission - The permission needed for naturally receiving this loot box. Naturally refers
    #   to receiving via one of the chances below. Players without this permission can still
    #   receive via the /givebox command and can open previously acquired loot boxes.
    #   ** This setting is optional, you can remove this line in the config.
    # Chances - The chances related to finding this loot box.
    #   PlayerKill - The chance a player will receive this loot box when killing a player.
    #   ZombieKill - The chance a player will receive this loot box when killing a zombie.
    #   MegaZombieKill - The chance a player will receive this loot box when killing a mega zombie.
    #   AnimalKill - The chance a player will receive this loot box when killing an animal.
    #   HarvestPlant - The chance a player will receive this loot box when harvesting a plant.
    #   HarvestResource - The chance a player will receive this loot box when finishing harvesting a resource.
    # Rewards - The rewards possibly given when finding this loot box.
    #   Only one reward will be given to the player. The reward is chosen based on the
    #   configured weights of each reward. Three items with weights of 2, 4, and 8 all
    #   have the same chances as if their weights were 20, 40, and 80 instead.
    #   Item - The id or name of the reward item. If this is a number, it will search for the id first.
    #   Weight - The weighting this reward has as described above.

    database:
      ConnectionStrings:
        default: "Server=127.0.0.1; Port=3306; Database=openmod; User=unturned; Password=password"

    LootBoxes:
    - BoxId: common
      Name: Common Box
      Chances:
        PlayerKill: 40 # 40% chance to get this loot box on player kill
        ZombieKill: 20 # 20% chance to get this loot box on zombie kill
        MegaZombieKill: 70 # 70% chance to get this loot box on mega zombie kill
        AnimalKill: 20 # 20% chance to get this loot box on animal kill
        HarvestPlant: 0 # 0% chance to get this loot box on plant harvest
                        # You can also omit this line for a 0% chance
        HarvestResource: 5 # 5% chance to get this loot box when harvesting
      Rewards: # One item will always drop as a reward
      - Item: Canned Beans # You can also specify the id of the item instead of the name
        Weight: 5
      - Item: Glue
        Weight: 10 # As Canned Beans has a weight of 5 and Glue has a weight of 10,
                  # Glue has twice the chance as Canned Beans to be the reward.
      - Item: 16 # Camp Axe
        Weight: 2

    - BoxId: rarebox
      Name: Rare Box
      # When setting a permission, the player must have this permission
      # in order to naturally receive this loot box. The loot box can still
      # be opened if they already own it, or if granted with /givebox.
      Permission: boxes.rarebox # The actual permission will be DropBoxes:boxes.rarebox
      Chances:
        PlayerKill: 15 # 15% chance
        MegaZombieKill: 10 # 10% chance
      Rewards:
      - Item: Cobra
        Weight: 10
      - Item: Colt
        Weight: 20 # Again, as the weight of the Colt is double that of the Cobra,
                  # it has twice the chance as the Cobra to be the reward

    # Here's a loot box config without any comments
    - BoxId: epicbox
      Name: Epic Box
      Permission: boxes.epicbox
      Chances:
        PlayerKill: 10
        ZombieKill: 2
        MegaZombieKill: 5
        AnimalKill: 2
        HarvestPlant: 0
        HarvestResource: 0.5
      Rewards:
      - Item: Grizzly
        Weight: 2
      - Item: Maplestrike
        Weight: 4
      - Item: Eaglefire
        Weight: 8
    ```

***

## Translations

??? note "Click to reveal default translations"
    ```yaml
    Natural:
      FoundLootBox: "You have found a {LootBox.Name}!"

    Commands:
      Success:
        LootBoxes: "Available loot boxes: {LootBoxes:x{Amount} {Name}|, |, and }"
        Unbox: "You have unboxed a {Item.Asset.ItemName} from your {LootBox.Name}!"
        GiveBox: "You have given {User.DisplayName} a {LootBox.Name}."
        GiveBoxById: "You have given {SteamId} a {LootBox.Name}."
        ReceivedBox: "You have been given a {LootBox.Name}!"
      Errors:
        UnknownLootBox: "Unknown loot box: {Input}"
        NoLootBox: "You do not have a {LootBox.Name}."
    ```

***

## Installation

1. Run the following commands to install necessary libraries:
  ```
  openmod install OpenMod.EntityFrameworkCore.MySql
  ```
  ```
  openmod install SilK.Unturned.Extras
  ```

2. Specify the `openmod` branch in your Imperial Plugins config.

3. Change the connection string in your new `DropBoxes/config.yaml` file to allow DropBoxes to connect to your MySQL server.