# <img src="/assets/images/plugins/shops-ui/logo.png" width="45" style="vertical-align: bottom;"/> Shops UI

Platforms: **OpenMod**  
Price: **$15 USD**  
**[Buy on Imperial Plugins](https://imperialplugins.com/Unturned/Products/Shops-UI)**

**Have you ever wanted your shops to be accessible through a UI?**

Using this plugin, players can buy and sell items and vehicles in your server's shop easily!

Easily migrate from your existing ZaupShops installation using the migration command. See more in the **Migration** section.

<div style="position:relative;padding-top:56.25%;">
    <iframe src="https://www.youtube.com/embed/nnrGGdkRCa4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
</div>

![Shops UI Example](/assets/images/plugins/shops-ui/ui.png)

***

## Usage

Players can simply use /shop (or /vshop to directly access the vehicle shop).
See the media on this page to view an example of the UI.

At the moment, commands must be used to configure the shop. More info on configuring the shops can be found in the **Commands** section.

Shop whitelists/blacklists are supported. The permission you specify in the commands for setup are not exact however. If you put `eaglefire` as the whitelist permission, the actual permission would be `ShopsUI:groups.eaglefire`. The permission you specify has `ShopsUI:groups.` added to the front.

***

## Migration

If you wish to migrate from ZaupShops, you can simply run the command `/shop migrate`.

If you used whitelists and blacklists with ZaupShop, you must also change some of your permissions. All existing permissions starting with `zaupgroups.` must be changed to start with `ShopsUI:groups.`.
For example, the following permissions show their original and their migrated permissions:

- `zaupgroup.epicguns` &#8594; `ShopsUI:groups.epicguns`  
- `zaupgroup.vip` &#8594; `ShopsUI:groups.vip`  
- `zaupgroup.mvp` &#8594; `ShopsUI:groups.mvp`  

***

## Commands

**Commands for UI:**

- /shop - Opens the shop UI.
- /vshop - Opens the shop UI directly to the vehicle tab.

**Commands for shop management:**

Basic commands:

- `/shop add <buy | sell> <item> <price>` - Adds the item to the shop to be bought or sold.
- `/shop remove <buy | sell> <item>` - Removes the buyable/sellable item from the shop.
- `/vshop add <vehicle> <price>` - Adds the vehicle to the shop to be bought.
- `/vshop remove <vehicle>` - Removes the buyable vehicle from the shop.
- `/shop reload` - Reloads the shops from the database.
- `/sellbox` - Opens a virtual storage for selling items.

UI-related management commands:

- `/shop order <item> <order>` - Sets the order of items in the shop UI.
- `/vshop order <vehicles> <order>` - Sets the order of vehicles in the shop UI.

Whitelist/blacklist commands:

- `/shop whitelist <add | rem> <item> <permission>` - Manage item shop whitelists.
- `/shop blacklist <add | rem> <item> <permission>` - Manage item shop blacklists.
- `/vshop whitelist <add | rem> <vehicle> <permission>` - Manage vehicle shop whitelists.
- `/vshop blacklist <add | rem> <vehicle> <permission>` - Manage vehicle shop blacklists.

The permission you specify has `ShopsUI:groups.` added to the front of it. `abc` turns into `ShopsUI:groups.abc`.

**Alternative buy/sell commands:**

- `/buy <item> [amount]` - Buys the item from the shop.
- `/sell <item> [amount]` - Sells the item to the shop.
- `/vbuy <vehicle>` - Buys the vehicle from the shop.

***

## Sellbox

The `/sellbox` command feature allows players to quickly sell items by placing them in a virtual storage.

The default sellbox size is configurable in the `config.yaml` file.

To set sell box sizes for certain permission roles, simply add the following lines below the `data` entry of a role (change width and height to what you'd like).

```yaml
sellbox:
  width: 8
  height: 12
```

??? note "Click to reveal an example using the default OpenMod permissions file"
    ```yaml
    roles:
    - id: default
      parents: []
      permissions:
      - OpenMod.Core:help
      displayName: Default
      data:
        sellbox:
          width: 6
          height: 8
      isAutoAssigned: true
    - id: vip
      priority: 1
      parents:
      - default
      permissions:
      - SomeKitsPlugin:kits.vip
      data:
        sellbox:
          width: 10
          height: 12
    ```

***

## Permissions

### Basic User Permissions

Grant access to the `/buy` command:
```
ShopsUI:commands.buy
```

Grant access to the `/cost` command:
```
ShopsUI:commands.cost
```

Grant access to the `/sell` command:
```
ShopsUI:commands.sell
```

Grant access to the `/shop` command to see the shop UI:
```
ShopsUI:commands.shop
```

Grant access to the `/vshop` command to directly navigate to vehicle shops in the UI:
```
ShopsUI:commands.vshop
```

### Administrative Permissions

Grant access to manage item shops:
```
ShopsUI:commands.shop.*
```

Grant access to manage vehicle shops:
```
ShopsUI:commands.vshop.*
```

***

## Configuration
??? note "Click to reveal default configuration"
    ```yaml
    database:
      ConnectionStrings:
        default: "Server=127.0.0.1; Database=openmod; Port=3306; User=unturned; Password=password"

    shops:
      # Blacklists allow all players to access a given shop
      # unless they have a configured blacklisted permission.
      # When this setting is set to true, shop blacklists will not be ignored.
      blacklistEnabled: false

      # Whitelists allow only the players who have a configured
      # whitelisted permission to access a given shop.
      # When this setting is set to true, shop whitelists will not be ignored.
      whitelistEnabled: false

    sellbox: # Default sellbox size. Set either to zero to disable by default.
      width: 8
      height: 6

    ui:
      logoUrl: "https://i.imgur.com/t6HbFTN.png"
      mainEffect: 29150
    ```

***

## Translations

You can change the color of both UI and command text translations by using [Unity's rich text format](https://docs.unity3d.com/560/Documentation/Manual/StyledText.html).

For example, to change the balance color to blue in the UI, change:
```yaml
Balance: {CurrencySymbol}{Balance:0.00}
```
to
```yaml
Balance: "<color=blue>{CurrencySymbol}{Balance:0.00}</color>"
```
or
```yaml
Balance: "<color=#0000FF>{CurrencySymbol}{Balance:0.00}</color>"
```

??? note "Click to reveal default translations"
    ```yaml
    commands:
      success:
        shop_reloaded: "Shops successfully reloaded."
        shop_added:
          buyable_item: "The item {ItemAsset.ItemName} can now be bought for {CurrencySymbol}{Price:0.00}."
          sellable_item: "The item {ItemAsset.ItemName} can now be sold for {CurrencySymbol}{Price:0.00}."
          buyable_vehicle: "The vehicle {VehicleAsset.VehicleName} can now be bought for {CurrencySymbol}{Price:0.00}."
        shop_removed:
          buyable_item: "The item {ItemAsset.ItemName} can no longer be bought."
          sellable_item: "The item {ItemAsset.ItemName} can no longer be sold."
          buyable_vehicle: "The vehicle {VehicleAsset.VehicleName} can no longer be sold."
        item_bought: "You have bought x{Amount} {ItemAsset.ItemName} for {CurrencySymbol}{Price:0.00}. Your balance is now {CurrencySymbol}{Balance:0.00}."
        item_sold: "You have sold x{Amount} {ItemAsset.ItemName} for {CurrencySymbol}{Price:0.00}. Your balance is now {CurrencySymbol}{Balance:0.00}."
        vehicle_bought: "You have bought a {ItemAsset.ItemName} for {CurrencySymbol}{Price:0.00}. Your balance is now {CurrencySymbol}{Balance:0.00}."
        item_cost:
          buy: "You can buy x{Amount} {ItemAsset.ItemName} for {CurrencySymbol}{BuyPrice:0.00}."
          sell: "You can sell x{Amount} {ItemAsset.ItemName} for {CurrencySymbol}{SellPrice:0.00}."
          buy_and_sell: "You can buy x{Amount} {ItemAsset.ItemName} for {CurrencySymbol}{BuyPrice:0.00} and sell for {CurrencySymbol}{SellPrice:0.00}."
        vehicle_cost:
          buy: "You can buy a {VehicleAsset.VehicleName} for {CurrencySymbol}{BuyPrice:0.00}."
        shop_order:
          item: "Successfuly set order value of {ItemAsset.ItemName} to {Order}."
          vehicle: "Successfuly set order value of {VehicleAsset.VehicleName} to {Order}."
        shop_whitelist:
          added:
            item: "Successfully added whitelist for item {ItemAsset.ItemAssetId} with permission {Permission}."
            vehicle: "Successfully added whitelist for vehicle {VehicleAsset.VehicleAssetId} with permission {Permission}."
          removed:
            item: "Successfully removed whitelist for item {ItemAsset.ItemAssetId} with permission {Permission}."
            vehicle: "Successfully removed whitelist for vehicle {VehicleAsset.VehicleAssetId} with permission {Permission}."
        shop_blacklist:
          added:
            item: "Successfully added blacklist for item {ItemAsset.ItemAssetId} with permission {Permission}."
            vehicle: "Successfully added blacklist for vehicle {VehicleAsset.VehicleAssetId} with permission {Permission}."
          removed:
            item: "Successfully removed blacklist for item {ItemAsset.ItemAssetId} with permission {Permission}."
            vehicle: "Successfully removed blacklist for vehicle {VehicleAsset.VehicleAssetId} with permission {Permission}."
        sellbox_sold: "You have sold {TotalAmount} items for {CurrencySymbol}{TotalPrice:0.00}. {ReturnedAmount} have been returned to you."

      errors:
        invalid_item_id: "Given item id ({IdOrName}) does not exist."
        invalid_vehicle_id: "Given vehicle id ({IdOrName}) does not exist."
        invalid_price: "Given price ({Price:0.00}) is not greater than or equal to zero."
        invalid_amount: "Given amount ({Amount}) is not greater than one."
        not_enough_items: "You do not have enough of this item."
        no_item_shop: "No shop for {ItemAsset.ItemName} exists."
        no_buyable_item_shop: "The item {ItemAsset.ItemName} cannot be bought."
        no_sellable_item_shop: "The item {ItemAsset.ItemName} cannot be sold."
        no_vehicle_shop: "No shop for {VehicleAsset.VehicleName} exists."
        no_buyable_vehicle_shop: "The vehicle {VehicleAsset.VehicleName} cannot be bought."
        not_permitted_item: "You are not permitted to buy/sell {ItemAsset.ItemName}."
        not_permitted_vehicle: "You are not permitted to buy {VehicleAsset.VehicleName}."
        no_sellbox: "You cannot use /sellbox."
        shop_whitelist:
          added:
            item: "A whitelist for this item could not be added. This shop may not exist or the whitelist has already been added."
            vehicle: "A whitelist for this vehicle could not be added. This shop may not exist or the whitelist has already been added."
          removed:
            item: "A whitelist for this item could not be removed. This shop may not exist or the whitelist has already been removed."
            vehicle: "A whitelist for this vehicle could not be removed. This shop may not exist or the whitelist has already been removed."
        shop_blacklist:
          added:
            item: "A blacklist for this item could not be added. This shop may not exist or the blacklist has already been added."
            vehicle: "A blacklist for this vehicle could not be added. This shop may not exist or the blacklist has already been added."
          removed:
            item: "A blacklist for this item could not be removed. This shop may not exist or the blacklist has already been removed."
            vehicle: "A blacklist for this vehicle could not be removed. This shop may not exist or the blacklist has already been removed."

    transactions:
      items:
        bought: "Purchased {Amount} {ItemAsset.ItemName} for {CurrencySymbol}{Price:0.##}"
        sold: "Sold {Amount} {ItemAsset.ItemName} for {CurrencySymbol}{Price:0.##}"
      vehicles:
        bought: "Purchased {VehicleAsset.VehicleName} for {CurrencySymbol}{Price:0.##}"

    ui:
      header: "Shops"
      balance: "Balance: {CurrencySymbol}{Balance:0.00}"
      items:
        header: "Items"
        listing:
          content: "{ItemAsset.ItemName}"
          buy: "Buy for {CurrencySymbol}{BuyPrice:0.##}"
          sell: "Sell for {CurrencySymbol}{SellPrice:0.##}"
        bought: "Successfully purchased."
        sold: "Successfully sold."
        not_permitted: "You are not permitted to do this."
      vehicles:
        header: "Vehicles"
        listing:
          content: "{VehicleAsset.VehicleName}"
          buy: "Buy for {CurrencySymbol}{BuyPrice:0.##}"
        not_permitted: "You are not permitted to do this."
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
  ```
  openmod install Silk.UnturnedImages
  ```

2. Specify the testing branch in your Imperial Plugins config.

3. Add the following workshop id to your WorkshopDownloadConfig.json file:
  ```
  2412328215
  ```

4. Change the connection string in your new `ShopsUI/config.yaml` file to allow ShopsUI to connect to your MySQL server.
