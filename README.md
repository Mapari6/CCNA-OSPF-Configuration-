# CCNA-OSPF-Configuration-
How to configure multi level OSPF (Open Shortest Path First) routing in cisco packet Tracer

----------------------------- R1 Commands----------------------------------------------------------------------------------------------------
R1>enable
R1#configure terminal
R1(Config)#

// Assigning Ip Address on interfaces
// ip address ip-address subnet mask

interface fa0/0
ip address 10.0.0.1 255.0.0.0
no shutdown

interface fa0/1
ip address 20.0.0.1 255.0.0.0
no shutdown
------------------------------------------------------------------------------------------------------------------------------------------

---------------------------R2 Commands----------------------------------------------------------------------------------------------------
R2>enable
R2#configure terminal
R2(Config)#

interface fa0/0
ip address 10.0.0.2 255.0.0.0
no shutdown

interface fa0/1
ip address 40.0.0.2 255.0.0.0
no shutdown
-----------------------------------------------------------------------------------

-----------------------R3 Commands-------------------------------------------------
R3>enable
R3#configure terminal
R3(Config)#

interface fa0/0
ip address 40.0.0.1 255.0.0.0
no shutdown

interface fa0/1
ip address 30.0.0.2 255.0.0.0
no shutdown
-----------------------------------------------------------------------------------

---------------------R4 Commands---------------------------------------------------
R4>enable
R4#configure terminal
R4(Config)#

interface fa0/0
ip address 30.0.0.1 255.0.0.0
no shutdown

interface fa0/1
ip address 20.0.0.2 255.0.0.0
no shutdown

interface fa1/0
ip address 20.0.0.2 255.0.0.0
no shutdown

interface fa1/1
ip address 80.0.0.2
no shutdown
-----------------------------------------------------------------------------------

------------------R5 Commands------------------------------------------------------
R5>enable
R5#configure terminal
R5(Config)#

interface fa0/0
ip address 50.0.0.2 255.0.0.0
no shutdown

interface fa0/1
ip address 60.0.0.1 255.0.0.0
no shutdown
-----------------------------------------------------------------------------------

-----------------R6 Commands-------------------------------------------------------
R6>enable
R6#configure terminal
R6(Config)#

interface fa0/0
ip address 70.0.0.1 255.0.0.0
no shutdown

interface fa0/1
ip address 60.0.0.2 255.0.0.0
no shutdown
----------------------------------------------------------------------------------

-----------------R7 Commands------------------------------------------------------
R7>enable
R7#configure terminal
R7(Config)#

interface fa0/0
ip address 00.0.0.1 255.0.0.0
no shutdown

interface fa0/1
ip address 70.0.0.2 255.0.0.0
no shutdown
----------------------------------------------------------------------------------

            // Configuring OSPF//

------------------ OSPF Configuration On R1---------------------------------------
R1(Config)#router ospf 10                                       // where 10is the process id we can choose peocess id from 1 to 65535 //
R1(router-Config)network 10.0.0.0 0.255.255.255 area 1       // 10.0.0.0 is the one network id of ip  address and 0.255.255.255 is the wildcard mask of that network
R1(router-Config)network 20.0.0.0 0.255.255.255 area 0       // configuring two areas for ospf..

// to run ospf successfully one of the interface of the router should be in the area 0 //
--------------------------------------------------------------------------------------

------------------ OSPF Configuration On R2-------------------------------------------
R2(Config)#router ospf 10
R2(router-Config)network 10.0.0.0 0.255.255.255 area 1 
R2(router-Config)network 40.0.0.0 0.255.255.255 area 1
------------------------------------------------------------------------------------

-------------- OSPF Configuration On R3---------------------------------------------
R3(Config)#router ospf 10
R3(router-Config)network 30.0.0.0 0.255.255.255 area 0
R3(router-Config)network 40.0.0.0 0.255.255.255 area 1
------------------------------------------------------------------------------------

---------------OSPF Configuration On R4---------------------------------------------
R4(Config)#router ospf 10
R4(router-Config)network 20.0.0.0 0.255.255.255 area 0
R4(router-Config)network 30.0.0.0 0.255.255.255 area 0
R4(router-Config)network 50.0.0.0 0.255.255.255 area 0
R4(router-Config)network 80.0.0.0 0.255.255.255 area 0
------------------------------------------------------------------------------------

-------------- OSPF Configuration on R5---------------------------------------------
R5(Config)#router ospf 10
R5(router-Config)network 50.0.0.0 0.255.255.255 area 0
R5(router-Config)network 60.0.0.0 0.255.255.255 area 0
----------------------------------------------------------------------------------

-------------- OSPF Configuration On R6-------------------------------------------
R6(router-Config)network 60.0.0.0 0.255.255.255 area 0
R6(router-Config)network 70.0.0.0 0.255.255.255 area 0
----------------------------------------------------------------------------------

--------------OSPF Configuration on R7--------------------------------------------
R7(router-Config)network 70.0.0.0 0.255.255.255 area 0
R7(router-Config)network 80.0.0.0 0.255.255.255 area 0
---------------------------------------------------------------------------------
