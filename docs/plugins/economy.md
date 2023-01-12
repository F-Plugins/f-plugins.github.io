# <img src="/assets/images/plugins/economy/logo.png" width="45" style="vertical-align: bottom; border-radius: 50%"/> Economy

Platforms: **OpenMod**  
Price: **FREE**  
**[Download for Free](https://docs.fplugins.com/plugins/economy/#installation)**

**Unturned economy plugin that supports xp and balance**

---

## Features

- Experience is supported and optional
- MySql or LiteDB for database are supported so you don't require a MySql database to run the plugin
- Almost all the code runs async so you wont experience any freezing
- Fully localized so you can change any message to your language
- Admins can give money and/or withdraw money from other player accounts
- Its Free

---

## Configuration

??? note "Click to reveal default configuration"
    ```yaml
    economy:
      use_xp: true
      allow_setting_negative_balance: false
      initial_balance: 100
    ```

??? note Click to reveal default translations
    ```yaml
    commands:
      success: 
        balance_display: "You have {CurrencySymbol}{Balance} {CurrencyName}"
        balance_display_other: "{User.DisplayName} has {CurrencySymbol}{Balance} {CurrencyName}"
        payment: 
          sent: "Successfully payed {Target.DisplayName} {CurrencySymbol}{Amount} {CurrencyName} {Reason:cond:for {}|}"
          receive: "You got {CurrencySymbol}{Amount} {CurrencyName} from {Sender.DisplayName} {Reason:cond:for {}|}"
        withdraw:
          sent: "Successfully withdraw {CurrencySymbol}{Amount} {CurrencyName} {Reason:cond:for {} |}from {Target.DisplayName} account"
          receive: "{Sender.DisplayName} just withdrew {CurrencySymbol}{Amount} {CurrencyName} {Reason:cond:for {} |}from you"
        print: "Successfully printed {CurrencySymbol}{Amount} {CurrencyName} {PayingSelf:cond:|for {Target.DisplayName}}"
        burn: "Successfully burned {CurrencySymbol}{Amount} {CurrencyName}"
      errors:
        user_not_found: "User named {Query} was not found"
        pay_self: "There is no point on paying yourself"
        pay_negative: "There is no point on paying a negative amount"
    economy:
      currency:
        name: "coins"
        symbol: "$"
      errors:
        not_enough_balance: "You don't have enough balance to pay {CurrencySymbol}{Amount}. Balance: {CurrencySymbol}{Balance}"
    ```

## Installation

To install the plugin you have to choose between 2 database types MySql which requires a MySql server to run or LiteDB which works with BSON so you don't have to install anything else than the plugin.

Execute the command according to the database type you want.

MySql: `openmod install Feli.Economy.MySql`
LiteDB: `openmod install Feli.Economy.LiteDB`
