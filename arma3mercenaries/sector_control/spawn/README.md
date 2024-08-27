---

# Dynamic Sector Control Unit Spawning Script

## Overview

**Script Name:** `arma3mercenaries_fn_spawnSectorControlUnit_1.sqf`  
**Author:** BrianV1981  
**Description:**  
This script dynamically manages the spawning and despawning of military groups based on the proximity of ALiVE-mod virtual entities to a specific waypoint marker, which serves as the waypoint for the spawned entity to move to and ultimatly take control the sector.

The script continuously monitors a 1000-meter radius centered on the waypoint marker (`waypointMarker_1`). It checks for the presence of entities from various factions (EAST, WEST, and GUER) and manages group activities accordingly. Each spawned group moves from their spawn point (`spawnMarker_1`) towards the waypoint, reacting based on the strategic importance of the location.

## Features

- **Dynamic Entity Checks:** The script uses the ALiVE mod to check for virtual entities within a specified radius around the waypoint marker.
- **Faction-Specific Spawning:** The script handles three factions—OPFOR (EAST), BLUFOR (WEST), and INDEPENDENT (GUER)—each with its own group type.
- **Automated Group Management:** Based on the presence of virtual entities, the script spawns and despawns groups dynamically, depending on which entities are present within the specified radius.
- **Waypoint-Driven Actions:** Groups spawned by the script move towards the waypoint marker.

## Installation

1. **Script Placement:**
   - Save this script in your mission folder at the following path:
     ```
     arma3mercenaries\sector_control\arma3mercenaries_fn_spawnSectorControlUnit_1.sqf
     ```

2. **Script Execution:**
   - In your mission's `init.sqf` or `serverInit.sqf`, add the following command to execute the script:
     ```sqf
     execVM "arma3mercenaries\sector_control\arma3mercenaries_fn_spawnSectorControlUnit_1.sqf";
     ```

3. **Marker Setup:**
   - Ensure that the markers `spawnMarker_1` and `waypointMarker_1` exist in your mission. The script uses `waypointMarker_1` as the focal point for checking the presence of ALiVE-mod virtual entities, influencing the dynamic control of spawning and despawning groups.

4. **Testing:**
   - Test your mission to ensure that the groups are spawning and despawning correctly based on the dynamics around the waypoint marker. Observe the group's movements to confirm they are responding effectively to the situation around the waypoint.

## How It Works

- **Proximity Checks:**
  - The script continuously checks a defined radius around the waypoint marker (`waypointMarker_1`) for virtual entities associated with each faction.
  - If entities from a faction are detected, the script spawns a corresponding group at the spawn marker (`spawnMarker_1`) and directs them to move towards the waypoint.

- **Group Management:**
  - If a group already exists for a faction but is empty (i.e., no units are alive), the script respawns the group.
  - If no virtual entities from a faction are detected, any existing group for that faction is despawned by eliminating its units.

- **Real-Time Updates:**
  - The script operates continuously with a 30-second interval, ensuring the game environment remains dynamic and responsive to ongoing tactical developments.

## Tactical Insight

This script provides a solution for using sector control in scenarios with ALiVE that spawns dynamic entities that do not trigger sectors for capture. By spawning a single unit at the sector after the virtual battle is decided, the sector can be claimed, ensuring a seamless and realistic experience in missions using ALiVE.

This approach addresses a previously overlooked challenge, offering a simple yet effective method for integrating sector control with dynamic virtual entities.

---
