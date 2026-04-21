MiniLab Packet Tracer : 
Objectif
Mise en place d'une infrastructure segmentée avec routage inter-VLAN, adressage dynamique et accès Internet sécurisé.
Plan d'Adressage
VLAN	Nom	IP Passerelle	Usage
1	VoIP	192.168.0.1	Téléphonie 
10	Wifi	192.168.10.1	Mobiles 
20	PC_Fixes	192.168.20.1	Postes fixes 
30	Admin	192.168.30.1	Gestion 

Configuration Essentielle (Router)
DHCP & NAT
Plaintext
! Exclusions (1-9 et 51-254)
ip dhcp excluded-address 192.168.20.1 192.168.20.9
ip dhcp excluded-address 192.168.20.51 192.168.20.254

! NAT Overload
access-list 1 permit 192.168.0.0 0.0.255.255
ip nat inside source list 1 interface g0/0 overload
ip route 0.0.0.0 0.0.0.0 g0/0
Validation des Tests
•	DHCP : Attribution fonctionnelle (ex: 192.168.20.13).
•	Routage : Ping réussi entre VLAN 20 et passerelle VLAN 10.
•	Internet : Accès au serveur externe (203.0.113.1) validé via NAT .
