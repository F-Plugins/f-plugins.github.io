# <img src="/assets/images/plugins/movement-modifier/logo.png" width="45" style="vertical-align: bottom;"/> Movement Modifier

Platforms: **OpenMod**, **Rocket**  
Price: **$5 USD**  
**[Buy on Imperial Plugins](https://imperialplugins.com/Unturned/Products/Movement Modifier)**

**Want players to move slower with heavy armor?**  
**How about jump higher with certain guns?**

***

## Features

With Movement Modifier, you can change players' **speeds, gravities, jump heights, and stamina costs** based on which items are in their inventory or are equipped.

This plugin is **Rocket-reloadable**, allowing on-the-fly changes to its simple configuration.

Rather than running every frame, this plugin uses events to ensure **zero lag** caused by this plugin.

***

## Configuration

The configuration has two main sections:

- Global Modifiers - applied to everyone
- Item Modifiers - applied when conditions are met

All movement modifications in the configuration are based on multipliers.
Examples:

- Specifying `2` as a jump modifier will allow the player to jump twice as high.
- Specifying `0.5` as a speed modifier will half the player's speed.

By default, all clothing items, guns, melee weapons, tools, and clouds (umbrellas) must be equipped. This can be overrided by stating `MustBeEquipped="False"`.

The ID for item modifiers can either be the item name or item ID. If the ID is a number, it will first search for a matching item ID then a name if no item is found.

**Explanation of default config:**

- When a player has a Viper equipped, they will run, jump, and fall twice as fast.
- When a player has the Tracksuit Top equipped, they will fall half as fast.
- When a player has an Ace (doesn't need to be equipped), all stamina costs are zero (infinite stamina).

### OpenMod

??? note "Click to reveal default configuration"
    ```yaml
    Global: # Global Multipliers
      Speed: 1
      Jump: 1
      Gravity: 1
      StaminaCost: 1

    # Adding a '#' before text comments it out
    # If the line starts with a '-', it's specifying a new item modifier.

    # Here is a run down of how the configuration works:

    #    The id specifies which item this should effect.
    #    This id can either be the name of the item (i.e. Viper) or the number-based id (i.e. 1027).

    # Every item id is followed by the modifiers. All modifiers are optional and are as follows:

    #    Speed - A speed multiplier (i.e. 2 will make the player move twice as fast)
    #    Jump - A jump multiplier (i.e. 5 will make the player jump five times higher)
    #    Gravity - A gravity multiplier (i.e. 0.1 will make the player have very low gravity)
    #    StaminaCost - A stamina cost multiplier (i.e. 0 will make the player use no stamina)

    # Every item modifier has the optional property 'MustBeEquipped' (true/false).
    # This property specifies whether or not the item must be equipped.

    # By default (if not explicitly set), all clothing items, guns, melee weapons, tools,
    # and clouds (umbrellas) must be equipped.

    # You can uncomment (remove the '#') features below to add them to the Viper config

    # The example with the Viper below will increase the player's speed, jump,
    # and gravity two times when a Viper is equipped.

    ItemModifiers:
    - Id: Viper
      Speed: 2
      Jump: 2
      Gravity: 2
    #  StaminaCost: 0.5
    #  MustBeEquipped: false

    - Id: Tracksuit Top
      Gravity: 0.5

    - Id: Ace
      StaminaCost: 0
      MustBeEquipped: false
    ```

### Rocket

??? note "Click to reveal default configuration"
    ```xml
    <GlobalMultipliers>
      <Speed>1</Speed>
      <Jump>1</Jump>
      <Gravity>1</Gravity>
      <StaminaCost>1</StaminaCost>
    </GlobalMultipliers>
    <ItemModifiers>
      <Item ID="Viper" Speed="2" Jump="2" Gravity="2" />
      <Item ID="Tracksuit Top" Gravity="0.5" />
      <Item ID="Ace" StaminaCost="0" MustBeEquipped="False" />
    </ItemModifiers>
    ```