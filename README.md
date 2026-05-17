# Cisco-Packer-Tracer
Cisco Packet Tracer adalah perangkat lunak simulasi jaringan komputer buatan Cisco Systems. Berfungsi sebagai laboratorium virtual, aplikasi ini memungkinkan Anda untuk mendesain topologi, mengonfigurasi perangkat (seperti router dan switch), hingga memecahkan masalah jaringan tanpa memerlukan perangkat keras fisik.

## Level 1
1. Sebuah kantor kecil memiliki:
    - 2 PC
    - 1 Switch
2. Topologi</br>
   <img width="561" height="260" alt="image" src="https://github.com/user-attachments/assets/2670bace-7332-400d-9db1-b2628a40da6a" />
3. Hasil
   - PC 1</br>
     <img width="406" height="198" alt="image" src="https://github.com/user-attachments/assets/2aff6e55-23ac-49f2-bd4f-e79d39fb9340" />
   - PC 2</br>
     <img width="477" height="200" alt="image" src="https://github.com/user-attachments/assets/1f54ff44-1b6e-48c7-95a0-a682b44ea79d" />


## Level 2
Pengertian VLAN

VLAN (Virtual Local Area Network) adalah teknologi yang digunakan untuk membagi satu jaringan fisik menjadi beberapa jaringan virtual yang berbeda.

Fungsi VLAN:

- Memisahkan jaringan
- Meningkatkan keamanan
- Mengurangi broadcast
- Mempermudah manajemen jaringan

**Topologi**

Device yang Digunakan
- 1 Switch Cisco 2960
- 4 PC
  
  <img width="750" height="258" alt="image" src="https://github.com/user-attachments/assets/66a2d13d-a17c-4cf6-84d3-5b688b2f4595" />
  <img width="921" height="496" alt="image" src="https://github.com/user-attachments/assets/81cd73ef-319e-4dd6-a4aa-6c6230a46858" />


Konfigurasi di Switch
- Untuk VLAN 10
  ```
  Switch>enable
  Switch#configuration terminal
  Enter configuration commands, one per line.  End with CNTL/Z.
  Switch(config)#vlan 10
  Switch(config-vlan)#name IT
  Switch(config-vlan)# exit
  ```
- Untuk VLAN 20
  ```
  Switch(config)#vlan 20
  Switch(config-vlan)#name HR
  Switch(config-vlan)#exit
  ```
- Assign Port VLAN 10
  ```
  interface range fa0/1-2
  switchport mode access
  switchport access vlan 10
  ```
- Assign Port VLAN 20
  ```
  interface range fa0/3-4
  switchport mode access
  switchport access vlan 20
  ```
Verifikasi VLAN
- show vlan brief
  
  <img width="738" height="245" alt="image" src="https://github.com/user-attachments/assets/eb094993-d1e6-42bf-9027-3570b5672ea3" />

Hasil
- Sesama Jaringan dari PC1 ke PC2
  ```
  C:\>ping 192.168.10.2

  Pinging 192.168.10.2 with 32 bytes of data:
  
  Reply from 192.168.10.2: bytes=32 time<1ms TTL=128
  Reply from 192.168.10.2: bytes=32 time<1ms TTL=128
  Reply from 192.168.10.2: bytes=32 time<1ms TTL=128
  Reply from 192.168.10.2: bytes=32 time<1ms TTL=128
  
  Ping statistics for 192.168.10.2:
      Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
  Approximate round trip times in milli-seconds:
      Minimum = 0ms, Maximum = 0ms, Average = 0ms
  ```
- Berbeda Jaringan dari PC1 ke PC3
  ```
  C:\>ping 192.168.20.2
  Pinging 192.168.20.2 with 32 bytes of data:
  Request timed out.
  Request timed out.
  Request timed out.
  Request timed out.
  Ping statistics for 192.168.20.2:
      Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
  ```
