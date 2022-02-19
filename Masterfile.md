# Dit bestand bevat een enumeratie van de alle cli commando's

 - Op een niveau lager te gaan in je terminal kan je dit commando gebruiken
   ```
   exit
   ```

 - meestal start je in "user execution mode" mode en will ja naar 
   "privilege mode" gaan. het "enable" commando laat exact dat toe. 
   Het laat toe te switchen van user execution mode naar privilege mode
   (zie bestand van "cli_modes" om alle mogelijkheden te zien
   ```
   enable
   ```
   - switchen van privilege mode naar global configuration mode 
     ```
     configure terminal
     ```
     - creeer een vlan of ga in een bestaande vlan. 
       (mogelijk in global configuration mode van een switch)   
       ```
       vlan <number>
       ```
         - geeft de vlan waarin jij je bevind een naam
           ```
           name <vlan naam>
           ```
         - "exit" typen is niet nodig je kan meteen van de ene vlan naar de ander navigeren
           ```
           vlan <number>
           ```
    - een overview van de vlan's, namen van vlan's, statusen van de poorten en poorten laten zien 
      ```
      show vlan brief
      ```
    - voice VLAN feature enables access ports to carry IP voice traffic from an IP phone
      dit commando geeft een p
      ```
      switchport voice 
      ```

   
   
