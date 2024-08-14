
  <summary>fn_respawn_sectorControl_noAlignment_1.sqf, fn_respawn_sectorControl_independentWest_1.sqf, fn_respawn_sectorControl_independentEast_1.sqf, fn_respawn_sectorControl_1.sqf</summary>

                     __..-----')
         ,.--._ .-'_..--...-'
        '-"'. _/_ /  ..--''""'-.
        _.--""...:._:(_ ..:"::. \
     .-' ..::--""_(##)#)"':. \ \)    
    /_:-:'/  :__(##)##)    ): )   
    "  / |  :' :/""\///)  /:.'  
      / :( :( :(   (#//)  "       
     / :/|\ :\_:\   \#//\   
     |:/ | ""--':\   (#//)              
     \/  \ :|  \ :\  (#//)
          \:\   '.':. \#//\      
           ':|    "--'(#///)
                      (#///)
                      (#///)
                       \#///\
                       (##///)
                       (BV///)
                       (+#///)
                       (JL///)
                        \=#///\
                        (ANV///)
                        (IRV///)
                        (MWV////)__...-----....__
                        (#/::'''                 ""--.._
                   __..-'''                             "-._
           __..--""           By BrianV1981            	   "-..____
  ___..--""                                                    "-..____
    (_ ""---....___                                     __...--"" _)
      """--...  ___"""""-----......._______......----"""     --"""
                    """"       ---.....   ___....----

  ## Sector Control Respawn Management Scripts

  <details>
  <summary>Features</summary>

  - **Dynamic Respawn Creation:** Automatically creates a respawn point at preplaced markers when a faction takes control of the sector.
  - **Joint Respawn Logic:** Configurable logic for faction alliances:
    - **Independent and NATO (West) Alliance:** Independent and NATO share respawn points when either faction controls the sector.
    - **Independent and CSAT (East) Alliance:** Independent and CSAT share respawn points when either faction controls the sector.
    - **No Alignment:** Each faction has its own respawn point, with no shared control.
  - **Mission Status Notifications:** Displays a custom message when a sector is secured, including the capturing faction's name, map grid, and military time.
  - **Flexible Configuration:** Works with predefined markers named `respawnWest_sector_1`, `respawnIndependent_sector_1`, and `respawnEast_sector_1`.

  </details>

  <details>
  <summary>Script Descriptions</summary>

  #### 1. `fn_respawn_sectorControl_independentWest_1.sqf`

  **Description:**
  This script creates respawn points for both **Independent** and **NATO (West)** when either faction controls the sector. If **CSAT (East)** captures the sector, only CSAT will have a respawn point.

  **Logic:**
  - **Independent or NATO (West) Control:** 
    - Both Independent and NATO (West) will have respawn points.
  - **CSAT (East) Control:**
    - Only CSAT will have a respawn point.

  #### 2. `fn_respawn_sectorControl_independentEast_1.sqf`

  **Description:**
  This script creates respawn points for both **Independent** and **CSAT (East)** when either faction controls the sector. If **NATO (West)** captures the sector, only NATO will have a respawn point.

  **Logic:**
  - **Independent or CSAT (East) Control:**
    - Both Independent and CSAT (East) will have respawn points.
  - **NATO (West) Control:**
    - Only NATO will have a respawn point.

  #### 3. `fn_respawn_sectorControl_noAlignment_1.sqf`

  **Description:**
  This script treats each faction independently. Only the faction that controls the sector will have a respawn point, with no alliances or shared control.

  **Logic:**
  - **NATO (West) Control:**
    - Only NATO will have a respawn point.
  - **CSAT (East) Control:**
    - Only CSAT will have a respawn point.
  - **Independent Control:**
    - Only Independent will have a respawn point.

  #### 4. `fn_respawn_sectorControl_1.sqf`

  **Description:**
  This is the base version of the respawn control script. It dynamically manages respawn points based on sector control and serves as the foundation for all other variations.

  **Logic:**
  - **NATO (West) Control:**
    - Only NATO will have a respawn point.
  - **CSAT (East) Control:**
    - Only CSAT will have a respawn point.
  - **Independent Control:**
    - Only Independent will have a respawn point.

  </details>

  <details>
  <summary>How to Use</summary>

  1. **Place Markers in the Editor:**
     - Place markers on the map where you want respawn points to appear. Name them `respawnWest_sector_1`, `respawnIndependent_sector_1`, and `respawnEast_sector_1`.

  2. **Save the Script:**
     - Save the selected script in your mission's `scripts/sector_control/` folder.

  3. **Configure the Sector Control Module:**
     - In the Arma 3 editor, place a `ModuleSector_F`.
     - In the Expression field (found under System Specific - Sector category), enter the following line:
     
     [_this select 0, _this select 1, _this select 2] execVM 'scripts/sector_control/fn_respawn_sectorControl_noAlignment_1.sqf';

     Replace `fn_respawn_sectorControl_noAlignment_1.sqf` with the appropriate script name based on the desired logic.

  4. **Testing:**
     - Start your mission and observe how the respawn points are created or disabled based on sector control changes.

  </details>

  <details>
  <summary>Important Notes</summary>

  - **Marker Names:** Ensure that the markers in the editor match the names used in the script.
  - **Respawn ID Management:** The scripts dynamically store the respawn ID when a point is created and remove it when no longer needed, ensuring clean management of respawn points.
  - **Script Execution:** These scripts are triggered whenever the sector changes control, ensuring that only the controlling faction(s) have access to the respawn point.

  </details>

</details>
