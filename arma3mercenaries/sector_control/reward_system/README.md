# Arma 3 Mercenaries Sector Control Reward System

## Overview

The `arma3mercenaries_fn_sector_control_RewardSystem.sqf` script is designed to manage the reward system for players who capture and hold sectors in an Arma 3 mission. The script continuously monitors players within a defined sector and rewards them periodically if they remain in control. The script also spawns enemy groups at random intervals to challenge the players.

## Features

- **Sector Monitoring:** The script monitors players within 125 meters of a specified marker, rewarding them for holding the sector.
- **Reward Distribution:** Players are rewarded at set intervals with increasing amounts of in-game currency.
- **Enemy Spawning:** After a set number of rewards, enemy groups are spawned at a random position near the sector to challenge the players.
- **Player Blocking:** After receiving six rewards, or if they leave the sector, players are blocked from receiving further rewards for two hours.

## Installation

1. **Script Placement:**
   - Place the `arma3mercenaries_fn_sector_control_RewardSystem.sqf` script in the following path within your mission folder:
     ```
     arma3mercenaries\sector_control\arma3mercenaries_fn_sector_control_RewardSystem.sqf
     ```

2. **Execution:**
   - Add the following line to your `initServer.sqf` to execute this script on the server:
     ```sqf
     [] execVM "arma3mercenaries\sector_control\arma3mercenaries_fn_sector_control_RewardSystem.sqf";
     ```

3. **Marker Configuration:**
   - Rename `'waypointMarker_1'` to the name of the marker that you want to use as the sector.

## Script Details

### Sector Monitoring
- The script continuously checks for players within 125 meters of the specified marker.
- If a player is within the sector, they will start receiving rewards unless they have already received six rewards or are blocked.

### Reward System
- Players receive six rewards (1x every 12 minutes) if they stay within the sector. The rewards increase with each interval:
  - 1st: 5000 credits (adjust to your liking for each sector)
  - 2nd: 20000 credits
  - 3rd: 25000 credits
  - 4th: 50000 credits
  - 5th: 75000 credits
  - 6th: 100000 credits

### Enemy Spawning
- After the 2nd reward, there is a random chance for enemy groups to spawn near the sector.
- The script uses `BIS_fnc_findSafePos` to find a random, safe position within a defined radius.
- Enemy groups are selected randomly from an array of predefined groups.
- The number of groups spawned depends on a random chance:
  - 50% chance for 1 group (adjust to your liking for each sector)
  - 40% chance for 2 groups
  - 10% chance for 3 groups

### Blocking Mechanism
- After receiving six rewards, the player is blocked from receiving further rewards in that sector for two hours.
- The player will see a message indicating that they have been blocked and their payments have been halted.

## Notes

- The script runs continuously and checks every 120 seconds for players in the sector.
- The enemy groups are spawned at intervals after the 2nd reward to provide a dynamic challenge to players.

## Credits

- **Author:** BrianV1981
