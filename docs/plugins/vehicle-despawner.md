# <img src="/assets/images/plugins/vehicle-despawner/logo.png" width="45" style="vertical-align: bottom;"/> Vehicle Despawner

Platforms: **OpenMod**, **RocketMod**  
Price: **$5 USD**  
**[Buy on Imperial Plugins](https://imperialplugins.com/Unturned/Products/Vehicle-Despawner)**

**Tired of too many vehicles being hidden away and unused?**

Vehicle Despawner will automatically despawn vehicles after they haven't been used for a set duration. The despawning of these unused vehicles will allow new vehicles to spawn for players to use.

***

## Configuration

- CheckInterval - Time (in seconds) between checks to despawn unused vehicles.  
  *Default: 30 seconds*
- UnusedDuration - Time (in seconds) which must pass without interaction for a vehicle to be considered unused and be despawned.  
  *Default: 172800 seconds (2 days)*

### OpenMod

??? note "Click to reveal default configuration"
    ```yaml
    # Time (in seconds) between checks to despawn unused vehicles.
    # (Default: 30 seconds)
    CheckInterval: 30

    # Time (in seconds) which must pass without interaction for a vehicle to
    # be considered unused and be despawned. (Default: 2 days = 172800 seconds)
    UnusedDuration: 172800
    ```

### Rocket

??? note "Click to reveal default configuration"
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VehicleDespawnerConfiguration xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <CheckInterval>30</CheckInterval>
      <UnusedDuration>172800</UnusedDuration>
    </VehicleDespawnerConfiguration>
    ```