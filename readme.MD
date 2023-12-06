# Modul 4 Jarkom IT14
* Moh. Sulthan Arief Rahmatullah
* Fransiskus Benyamin

### Pembagian IP Subneting dengan VLSM
Pertama kita lakukan pembagian subneting nya berikut gambar saya
![WhatsApp Image 2023-12-02 at 9 54 21 PM](https://github.com/ramasedang/Jarkom-Modul-3-IT14-2023/assets/76695790/cadc5cf5-cbdb-454b-854a-833384faec49)

Setelah menentukan pembagian subnetnya lalu lakukan membuat tabel

| Nama Subnet                                | Rute                                              | Jumlah IP | Jumlah IP | Netmask |
|--------------------------------------------|---------------------------------------------------|-----------|-----------|---------|
| A1                                         | Aura-Cloud0                                       | 2         | 2         | /30     |
| A2                                         | Aura-Denken                                       | 2         | 2         | /30     |
| A3                                         | Aura-Frieren                                      | 2         | 2         | /30     |
| A4                                         | Aura-Eisen                                        | 2         | 2         | /30     |
| A5                                         | Frieren-Switch3-LakeKorridor                      | 24+1=25   | 25        | /27     |
| A6                                         | Denken-Switch2-WiliRegion-Switch2-RoyalCapital    | 63+63+1=127| 127       | /24     |
| A7                                         | Eisen-Switch0-Stark                               | 2         | 2         | /30     |
| A8                                         | Eisen-Lugner                                      | 2         | 2         | /30     |
| A9                                         | Eisen-Linie                                       | 2         | 2         | /30     |
| A10                                        | Eisen-Switch1-Richter-Switch1-Revolte             | 3         | 3         | /29     |
| A11                                        | Lugner-Switch10-TurkRegion                        | 1000+1=1001| 1001      | /22     |
| A12                                        | Lugner-Switch9-GrobeForest                        | 250+1=251  | 251       | /24     |
| A13                                        | Linie-Switch11-GranzChannel                       | 254+1=255  | 255       | /23     |
| A14                                        | Linie-Lawine                                      | 2         | 2         | /30     |
| A15                                        | Lawine-Switch7-BredtRegion-switch7-Heiter         | 29+1+1=31  | 31        | /27     |
| A16                                        | Heiter-Switch8-RiegelCanyon-Switch8-Sein          | 510+1+1=512| 512       | /22     |
| A17                                        | Frieren-Flamme                                    | 2         | 2         | /30     |
| A18                                        | Flamme-fern                                       | 2         | 2         | /30     |
| A19                                        | Flamme-Switch5-RohrRoad                           | 1000+1=1001| 1001      | /22     |
| A20                                        | Flamme-Himmel                                     | 2         | 2         | /30     |
| A21                                        | Himmel-Switch6-SchwerMountains                    | 5+1=6     | 6         | /29     |
| A22                                        | Fern-Switch4-LaubHills-Switch4-AppetitRegion      | 625+397+1=1023| 1023    | /21     |
| Total                                      |                                                   | 4257      |           | /19     |




Lalu setelah mengetahui pemabagian nya lakukan, sorting dengan host terbanyak, lakukan gunakan perhitungan gunakan 2^n, yang mana ip pertama adalah network id dan ip terakhir adalah broadcast id


| Subnet | Network ID    | Netmask        | Broadcast       |
|--------|---------------|----------------|-----------------|
| A22    | 192.240.0.0   | 255.255.248.0  | 192.240.7.255   |
| A11    | 192.240.8.0   | 255.255.252.0  | 192.240.11.255  |
| A19    | 192.240.12.0  | 255.255.252.0  | 192.240.15.255  |
| A16    | 192.240.16.0  | 255.255.252.0  | 192.240.19.255  |
| A13    | 192.240.20.0  | 255.255.254.0  | 192.240.21.255  |
| A12    | 192.240.22.0  | 255.255.255.0  | 192.240.22.255  |
| A6     | 192.240.23.0  | 255.255.255.0  | 192.240.23.255  |
| A15    | 192.240.24.0  | 255.255.255.192| 192.240.24.63   |
| A5     | 192.240.24.64 | 255.255.255.224| 192.240.24.95   |
| A21    | 192.240.24.96 | 255.255.255.248| 192.240.24.103  |
| A10    | 192.240.24.104| 255.255.255.248| 192.240.24.111  |
| A1     | 192.240.24.112| 255.255.255.252| 192.240.24.115  |
| A2     | 192.240.24.116| 255.255.255.252| 192.240.24.119  |
| A3     | 192.240.24.120| 255.255.255.252| 192.240.24.123  |
| A4     | 192.240.24.124| 255.255.255.252| 192.240.24.127  |
| A7     | 192.240.24.128| 255.255.255.252| 192.240.24.131  |
| A8     | 192.240.24.132| 255.255.255.252| 192.240.24.135  |
| A9     | 192.240.24.136| 255.255.255.252| 192.240.24.139  |
| A14    | 192.240.24.140| 255.255.255.252| 192.240.24.143  |
| A17    | 192.240.24.144| 255.255.255.252| 192.240.24.147  |
| A18    | 192.240.24.148| 255.255.255.252| 192.240.24.151  |
| A20    | 192.240.24.152| 255.255.255.252| 192.240.24.155  |

setelah itu lakukan pemasangan IP pada GNS 3 menggunakan IP diatas

![image](https://github.com/ramasedang/Jarkom-Modul-3-IT14-2023/assets/76695790/3b3eca10-50e7-47f5-86b7-5b8814abeb8f)

Setelah membuat topologi lakukan routing seperti dibawah


#Aura
route add -net 192.240.23.0 netmask 255.255.255.0 gw 192.240.24.118
route add -net 192.240.24.128 netmask 255.255.255.252 gw 192.240.24.126
route add -net 192.240.8.0 netmask 255.255.252.0 gw 192.240.24.126
route add -net 192.240.22.0 netmask 255.255.255.0 gw 192.240.24.126
route add -net 192.240.24.104 netmask 255.255.255.248 gw 192.240.24.126
route add -net 192.240.20.0 netmask 255.255.254.0 gw 192.240.24.126
route add -net 192.240.24.0 netmask 255.255.255.192 gw 192.240.24.126
route add -net 192.240.16.0 netmask 255.255.252.0 gw 192.240.24.126
route add -net 192.240.24.64 netmask 255.255.255.224 gw 192.240.24.122
route add -net 192.240.12.0 netmask 255.255.252.0 gw 192.240.24.122 
route add -net 192.240.0.0 netmask 255.255.248.0 gw 192.240.24.122 


#Denken
route add -net 192.240.24.116 netmask 255.255.255.252 gw 192.240.24.117 

#Eisen
route add -net 192.240.24.124 netmask 255.255.255.252 gw 192.240.24.125 
route add -net 192.240.8.0 netmask 255.255.252.0 gw 192.240.24.134
route add -net 192.240.22.0 netmask 255.255.255.0 gw 192.240.24.134
route add -net 192.240.20.0 netmask 255.255.254.0 gw 192.240.24.138
route add -net 192.240.24.0 netmask 255.255.255.192 gw 192.240.24.138
route add -net 192.240.16.0 netmask 255.255.252.0 gw 192.240.24.138

#Lugner
route add -net 192.240.24.132 netmask 255.255.255.252 gw 192.240.24.133

#Linie
route add -net 192.240.24.136 netmask 255.255.255.252 gw 192.240.24.137
route add -net 192.240.24.0 netmask 255.255.255.192 gw 192.240.24.142
route add -net 192.240.16.0 netmask 255.255.252.0 gw 192.240.24.142

#Lawine
route add -net 192.240.24.140 netmask 255.255.255.252 gw 192.240.24.141 
route add -net 192.240.16.0 netmask 255.255.252.0 gw 192.240.24.2

#Heiter
route add -net 192.240.24.0 netmask 255.255.255.192 gw 192.240.24.1 

#Frieren
route add -net  192.240.24.120 netmask 255.255.255.252 gw 192.240.24.121
route add -net 192.240.12.0 netmask 255.255.252.0 gw 192.240.24.146 
route add -net 192.240.0.0 netmask 255.255.248.0 gw 192.240.24.146


#Fern 
route add -net 192.240.24.148 netmask 255.255.255.252 gw 192.240.24.149 

#Flamme
route add -net 192.240.24.144 netmask 255.255.255.252 gw 192.240.24.145 
route add -net 192.240.0.0 netmask 255.255.248.0 gw 192.240.24.150


#Himmel
route add -net 192.240.24.152 netmask 255.255.255.248 gw 192.240.24.153 

### Pembagian IP Subneting dengan CIDR
Pertama, kita perlu menentukan subnet yang ada dalam topologi dan lakukan labelling netmask terhadap masing-masing subnet. 
![Subnet A](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/c435459a-fda4-45f6-a2e4-231d1db54177)
![Subnet B](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/d9ecb218-df12-4791-8a22-35bf04b4512f)
![Subnet C](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/45d2198d-9340-4553-ba32-d0575569e778)
![Subnet D](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/61ae02a6-33fd-4175-ad3c-6d155880a28f)
![Subnet E](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/1ec8745e-7c63-4afe-bc94-6d7b137870ca)
![Subnet F](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/b2993efe-dbe7-4d8e-9a7c-323de6a55a49)
![Subnet G](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/24d52779-c09c-4189-9ad7-46afc8aca1f8)
![Subnet H](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/e19c1d28-8209-4991-aebe-1d206778b87d)
![Subnet I](https://github.com/ramasedang/Jajarkom-Modul-4-IT14-2023/assets/73869671/4349c684-2581-49d7-a66a-dc8ef8a31342)
