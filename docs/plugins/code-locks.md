# <img src="/assets/images/plugins/code-locks/logo.png" width="45" style="vertical-align: bottom;"/> Code Locks

Platforms: **OpenMod**, **RocketMod**  
Price: **$12 USD**  
**[Buy on Imperial Plugins](https://imperialplugins.com/Unturned/Products/Code-Locks)**

**Have you ever wanted to secure objects with code locks in Unturned?**

Using this plugin, players can add code locks to doors and storages - providing access to anyone who knows the code.

<div style="position:relative;padding-top:56.25%;">
    <iframe src="https://www.youtube.com/embed/gCeqEz9yU8s" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position:absolute;top:0;left:0;width:100%;height:100%;"></iframe>
</div>

![Code Locks UI](/assets/images/plugins/code-locks/ui.png)

***

## Usage

Simply lock a door/storage using the `/lock <code>` command. From here, other players can walk up to the object and attempt to use it. A keypad will pop up prompting for the code. Clicking anywhere on the screen except the keypad will close it.

By default, each incorrect attempt will deal a bit more damage each time, until the player is killed.

***

## Commands

- `/lock <code>` - Adds a code lock to an object, or changes if one already exists.
- `/unlock` - Removes the code lock from an object.

***

## Permissions

### OpenMod

Grant access to the /lock command:
```
CodeLocks:commands.lock
```

Grant access to the /unlock command:
```
CodeLocks:commands.unlock
```

Grant the ability to lock/unlock any lockable object
```
CodeLocks:bypass
```

### Rocket

Grant access to the /lock command:
```
lock
```

Grant access to the /unlock command:
```
unlock
```

Grant the ability to lock/unlock any lockable object
```
bypasslock
```

***

## Configuration

- **Effects** - Effect IDs used by the plugin. Switch success and failure to zero to disable sounds.
- **Remember Owner** - Whether or not the owner must enter the code each time.
- **Remember Users** - Whether or not other users need to enter the code every time.
- **Non-Owner Can Change Code** - Whether or not users who aren't the owner can change the lock.
- **Attempts** - Settings related to failed attempts to enter a code.
  - **Cooldown** - The time (in seconds) before an attempt is 'forgotten'.
  - **Damages** - The damage to be dealt at a certain failed attempt.
    Example: 0, 30, 50, 255
    Zero damage would be dealt on the first attempt, 30 on the next, the max damage would be dealt on the fourth attempt (and all attempts afterwards).

### OpenMod

??? note "Click to reveal default configuration"
    ```yaml
    effects:
      ui: 29123
      success: 29124
      failure: 29125

    # Whether or not the owner must enter the code each time
    rememberOwner: true

    # Whether or not other users need to enter the code every time
    rememberUsers: true

    # Whether or not users who aren't the owner can change the lock
    nonOwnerCanChangeCode: true

    attempts:
      cooldown: 60 # Cooldown in seconds
      damages:
      - 0 # Occurs on the first attempt
      - 30 # Occurs on the second attempt
      - 50
      - 255 # Max damage. Occurs on the fourth attempt, and all others
    ```

### Rocket

??? note "Click to reveal default configuration"
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <CodeLocksConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <RememberOwner>true</RememberOwner>
      <RememberUsers>true</RememberUsers>
      <NonOwnerCanChangeCode>true</NonOwnerCanChangeCode>
      <Effects>
        <UI>29123</UI>
        <Success>29124</Success>
        <Failure>29125</Failure>
      </Effects>
      <Attempts>
        <Cooldown>60</Cooldown>
        <Damages>
          <Damage>0</Damage>
          <Damage>30</Damage>
          <Damage>50</Damage>
          <Damage>255</Damage>
        </Damages>
      </Attempts>
    </CodeLocksConfiguration>
    ```

***

## Translations

### OpenMod

??? note "Click to reveal default translations"
    ```yaml
    commands:
      codelock:
        no_lockable_object: "You are not looking at a lockable object."
        invalid_code: "The given code ({Code}) is invalid. The code must be four numbers (ex. 1234)."
        code_added: "This object has been locked with the code {Code}."
        code_changed: "This object's lock has been changed to the code {Code}."
        code_removed: "This object's has been unlocked."
        no_access: "You do not have access to set this object's locks."
        no_code: "There is no code lock on this object."
    ```

### Rocket

??? note "Click to reveal default translations"
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Translations xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Translation Id="commands_codelock_help" Value="/lock &lt;code&gt; - Adds a code lock to an object, or changes if one already exists." />
      <Translation Id="invalid_parameters" Value="&lt;color=red&gt;Invalid parameters.&lt;/color=red&gt;" />
      <Translation Id="commands_codelock_no_lockable_object" Value="&lt;color=red&gt;You are not looking at a lockable object.&lt;/color&gt;" />
      <Translation Id="commands_codelock_invalid_code" Value="&lt;color=red&gt;The given code ({0}) is invalid. The code must be four numbers (ex. 1234).&lt;/color&gt;" />
      <Translation Id="commands_codelock_code_added" Value="This object has been locked with the code {0}." />
      <Translation Id="commands_codelock_code_changed" Value="This object's lock has been changed to the code {0}." />
      <Translation Id="commands_codelock_code_removed" Value="This object's has been unlocked." />
      <Translation Id="commands_codelock_no_access" Value="&lt;color=red&gt;You do not have access to set this object's locks.&lt;/color&gt;" />
      <Translation Id="commands_codelock_no_code" Value="&lt;color=red&gt;There is no code lock on this object.&lt;/color&gt;" />
    </Translations>
    ```

***

## Installation

1. Specify in your Imperial Plugins config the `openmod` branch.

2. Add the following workshop ID to your WorkshopDownloadConfig.json file:
   ```
   2407368422
   ```