# Dit bestand bevat een enumeratie van de alle cli commando's die iets met VLANS te maken hebben

#### oplossing van 3.6.1 --> https://www.ccna6rs.com/3-6-1-packet-tracer-implement-vlans-and-trunking-answers/
  
  - #### Om een niveau lager te gaan in je terminal kan je dit commando gebruiken
     ```
     exit
     ```


   - ##### Meestal start je in "user execution mode" mode en wil ja naar "privilege mode" gaan. Het "enable" commando laat exact dat toe, het laat toe te switchen van user execution mode naar privilege mode (zie de foto "cli_modes" in de map images om alle mogelijkheden te zien. 
     ```
     enable
     ```
     - ### switchen van privilege mode naar global configuration mode 
       ```
       configure terminal
       ```
     ### SWITCH
       - #### creeer een vlan of ga in een bestaande vlan. 
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
       - #### een interface van een vlan configureren 
         ```
         interface vlan <number>
         ```
           - een ip address toevoegen aan deze vlan
             ```
             ip address <ipaddress> <subnetmasker>
             ```
       - #### een poort configureren 
         ```
         interface ethernetkabel/<portcombo> bv interface ethernet/0/1
         int ethernetkabel/<portcombo> bv int fastethernet/0/1
         ```
           - zegt tot welke vlan interface deze poort hoort
             ```
             switchport acces vlan <number>
             ```
           - dit commando zal er voor zorgen dat de switch zal weten wat hij hoort te doen 
             zelfs als de kabels verkeerd verbonden zijn. 
             ```
             mdix auto
             ```
           - maak van de default acces port een trunk port. Alle frames die over deze link gestuurd worden, zullen een VLAN tag krijgen.
             Hierdoor kunnen we identificeren bij welke vlan een frame hoort. Dit maakt het dus mogelijk alle data van meerdere vlan's 
             over 1 link te sturen. 
             ```
             swithport mode trunk
             ```
           - maak van een trunk poort een acces poort, dit will zeggen dat frames geen VLAN tag meer zullen krijgen over deze 
             verbinding. 
             ```
             switchport mode access
             ```
           - Dees schakelt de DTP protocol op een poort uit, want sommige netwerken devices zijn soms onjuist geconfigureert 
             en dit kan uw netwerken dan beschadigen.
             DTP: Indien er een switchport in trunk mode wordt gezet, gaat het Dynamic Trunking Protocol er voor zorgen dat de verbonden 
             poort ook een trunk poort wordt, door zijn gegevens automatisch te configuren voor hem.
             https://www.ciscopress.com/articles/article.asp?p=2181837&seqNum=8
             
             INDIEN ERROR --> voordat je dit commando kan uitvoeren moet je deze switch eerst een trunk maken "switchport mode trunk"
             ```
             switchport nonegotiate
             ```
           - Indien je het commando hierboven ongedaan wilt maken
             ```
             no switchport nonegotiate
             ```
           - Indien een buurtpoort een trunk is, zal deze poort ook een trunk worden en alle DTP settings overnemen. 
             ```
             switchport mode dynamic desirable 
             ```
           - configureert de native vlan van een switch. Op deze link moet er dus geen vlan tag meer worden meegegeven op de frame, want 
             dit wordt nu gezien als de default link. (native vlans moeten op beide poorten juist geconfigureert worden) 
             Management protocollen zoals CDP, VTP of STP kunnen nu weer functioneren over deze switches. 
             https://www.youtube.com/watch?v=Fmq1E1Qr2W4
             https://www.youtube.com/watch?v=zW_-mf6v3fs
             ```
             switchport trunk native vlan <vlan-id>
             ```
           - "mls qos" --> dit geeft de swicth quality of service opties. 
             quality of service: de mogelijkheid om pakketen te prioriteren en het behouden van de pakketen to reguleren. 
             "trust cos" in een frame (L2) zit een "cos" field hierin staan de prioriteiten van de soorten frames. 
             een telefoon frame heeft bv voorrang op een internetframe want een telefoonverbinding heeft een constante dataflow nodig
             om te functioneren. door trust "trust cos" te kiezen ga je handelen volgens die prioriteiten van de cos field ipv van de dhcp values 
             die bepaalt worden op (L3). 
             ```
             mls qos trust cos
             ```
          - voice VLAN feature enables access ports to carry IP voice traffic from an IP phone
            dit commando vertelt over welke vlan alle voice traffic gaat gaan.
             ```
             switchport voice vlan <number>
             ```
     - een overview van de vlan's, namen van vlan's, statusen van de poorten en poorten laten zien 
        ```
        show vlan brief
        ```
   ### ROUTER    
   - #### een poort configureren 
       ```
       interface ethernetkabel/<portcombo> bv interface ethernet/0/1
       int ethernetkabel/<portcombo> bv int fastethernet/0/1
       ```
        - een poort aanzetten 
          ```
          no shutdown
          ```
        - een ip address toekennen aan een poort
          ```
          ip address <address> <subnetmasker>
          ```
   - #### een interface op een poort configureren
       ```
       interface ethernetkabel/<portcombo> bv interface ethernet/0/<poort>.<interfaceid>
       int ethernetkabel/<portcombo> bv int fastethernet/<poort>/<interfaceid>
       ```
   
   
