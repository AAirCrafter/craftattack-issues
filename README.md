# CraftAttack-Issues

please report every bug you find and feel free to contribute every idea you have :)

----





Complete **All-In-One Plugin** for your own CraftAttack experience, just like the original.  
Features automatic map generation, Spawn Elytra, custom statuses, sitting/lying, invisible item frames, and much more.

## Installation

1. Simply place the CraftAttack plugin into the `plugins` folder on your server.
2. **Delete existing worlds** (simply delete the world folders, usually named `world`, `world_nether`, and `world_the_end`).  
   The CraftAttack spawn is only generated in a **newly created** world. If the world already exists when the server starts, it will not be modified.
3. Start the server. The plugin automatically searches for a suitable location and builds the spawn (see below).
4. Once everyone is ready, start CraftAttack with: `/start`.

## 🚀 Alternative: Get Started Instantly
Don't want to set everything up yourself? With [**NoRiskHost**](https://norisk.host/?ref=AAIR), you can jump straight in without any setup!

⚡ **Quick Setup:** Your server is automatically preconfigured – including the CraftAttack plugin and the appropriate settings.  
🌍 **No Manual Work:** No deleting worlds, editing configs, or complicated setup.  
🎮 **Just Play:** Start the server, invite your friends, and get going!

👉 **[Create your server at NoRiskHost now](https://norisk.host/?ref=AAIR)**


## Starting Phase

As long as CraftAttack has not been started:
- A **world border** surrounds the spawn.
- All players are confined to the spawn.

Use `/start` to remove the border and begin playing. The status is saved in `config.yml` (`started`).

## Map Generation

When a new world is started for the first time (with `createspawn: true`):

1. The plugin searches for a seed with an open body of water suitable for the **pre-built CraftAttack spawn**.
2. It then searches for the nearest **Mushroom Island**, where the Shopping District can be built.
3. The spawn is placed at the selected location and set as the world spawn.

If the current seed is unsuitable, the plugin automatically tests new seeds. Once it finds a suitable one, it updates the seed and a new world name in `server.properties` and **stops the server**. After restarting, the world is generated with the new seed, and the old world is automatically deleted.

> The server will not restart automatically after being stopped unless your host handles this automatically.

## Resetting the World

`/careset` resets the entire world: a new seed, a new spawn, and a return to the starting phase (players confined to the spawn).

For safety, the reset must be confirmed within 30 seconds (click **[Confirm]** or use `/careset confirm`).

After confirmation, all players are kicked, a new seed is searched for, and the server is stopped. On the next startup, the new world is generated and the old one is deleted.

Statuses are preserved.

## Status System

Players can choose a status that appears in square brackets before their name.

```
[GHG] <Player> Message
```

| Command | Description |
|---|---|
| `/status <name>` | Select a status |
| `/status none` | Remove your status |
| `/createstatus <name> <displayname>` | Create a status (Admin) |
| `/deletestatus <name>` | Delete a status (Admin) |

The DisplayName supports:
- Minecraft color codes such as `&4`, `&a`, `&l`, `&o`, `&r`
- Hex colors: `&#FF8800`
- Gradients: `<#FF0000>Text<#FFFFFF>` (gradient from the first to the second color)
- Standard MiniMessage tags, e.g. `<bold>` or `<gradient:#f00:#0f0:#00f>…</gradient>`

Example statuses:
```
/createstatus ghg <#860DC5>GHG<#B619D1>
/createstatus bambus &aBamboo
/createstatus air <#6EDCFF>AIR<#00BFFF>
```

## Sitting & Lying Down

- `/sit` – sit down
- `/lay` – lie on your back

Stand up by **sneaking** or entering the command again.  
Players who have taken damage within the last 10 seconds cannot sit or lie down.

## Spawn Protection & Extras

- Only OPs in Creative mode can build, break blocks, or interact at the spawn.
- No mobs spawn at the spawn.
- When jumping off the spawn, players automatically glide using a virtual Elytra. Press **F** (the offhand key) for a one-time boost.
- **Invisible Item Frame:** Place an item frame in the center and surround it with 8 glass panes.

## Config

`plugins/craftattack/config.yml`:

```yaml
project-name: CraftAttack # Project name shown in titles and messages, e.g. on /start
createspawn: true         # Automatically generate the spawn in new worlds
spawn-max-distance: 2000  # Max. distance of the Mushroom Island from 0/0
mushroom-min-size: 80     # Minimum size of the Mushroom Island (approx. 80x80 blocks)
started: false            # Toggled with /start; mainly controls the border and related features
```

`project-name` supports the same formatting as status display names (e.g. `&6CraftAttack` or `<#FF0000>CraftAttack<#FFFF00>`).

The smaller `spawn-max-distance` is or the larger `mushroom-min-size` is, the more often a new seed will need to be searched for.

## Permissions

| Command | Permission | Default |
|---|---|---|
| `/start` | `craftattack.start` | OP |
| `/careset` | `craftattack.careset` | OP |
| `/createstatus` | `craftattack.createstatus` | OP |
| `/deletestatus` | `craftattack.deletestatus` | OP |

All players can use `/status`, `/sit`, and `/lay`.

This is **not an official CraftAttack plugin**, but an independently developed version designed to be as accurate to the original as possible. It was programmed by AAirCrafter on behalf of NoriskHost. If you have any questions or need help, feel free to join my Discord [AirCord](https://dc.aircrafter.cloud)!
