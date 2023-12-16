# Jarkom-Modul-5-E15-2023

## A. Tugas Pertama

### Pembuatan Topologi

Wilayah North Area

![img](imgs/topologi.png)

Keterangan:

- Richter adalah DNS Server
- Revolte adalah DHCP Server
- Sein dan Stark adalah Web Server
- Jumlah Host pada SchwerMountain adalah 64
- Jumlah Host pada LaubHills adalah 255
- Jumlah Host pada TurkRegion adalah 1022
- Jumlah Host pada GrobeForest adalah 512

## B. Untuk menghitung rute-rute yang diperlukan, gunakan perhitungan dengan metode VLSM. Buat juga pohonnya, dan lingkari subnet yang dilewati.

Untuk menentukan IP address and routing untuk topologi, kita akan menggunakan VLSM untuk pencarian subnet.

**Perhitungan Rute:**

![img](imgs/rute.png)

**Lingkaran subnet:**

![img](imgs/PembagianSubnet.jpg)

**Pohon VLSM:**

![img](imgs/VLSM-5.jpg)

**Sehingga didapatkan pembagian IP:**

![img](imgs/pembagianIP.png)

## C. Kemudian buatlah rute sesuai dengan pembagian IP yang kalian lakukan

Dengan range NID dan Broadcast Address, kita dapat melakukan konfigurasi node pada GNS3 sebagai berikut

#### Aura

```
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp

# Static config for eth1
auto eth1
iface eth1 inet static
	address 10.44.0.1
	netmask 255.255.255.252

# Static config for eth2
auto eth2
iface eth2 inet static
	address 10.44.0.5
	netmask 255.255.255.252
```

#### Heiter

```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.44.0.2
	netmask 255.255.255.252
	gateway 10.44.0.1

# Static config for eth1
auto eth1
iface eth1 inet static
	address 10.44.8.1
	netmask 255.255.248.0

# Static config for eth2
auto eth2
iface eth2 inet static
	address 10.44.4.1
	netmask 255.255.252.0
```

#### TurkRegion

```
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp
```

#### Sein

```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.44.4.2
	netmask 255.255.252.0
	gateway 10.44.4.1
```

#### GrobeForest

```
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp
```

#### Frieren

```
# Static config for eth0
auto eth0
iface eth0 inet static
        address 10.44.0.6
	netmask 255.255.255.252
	gateway 10.44.0.5

# Static config for eth1
auto eth1
iface eth1 inet static
	address 10.44.0.9
	netmask 255.255.255.252

# Static config for eth2
auto eth2
iface eth2 inet static
	address 10.44.0.13
	netmask 255.255.255.252
```

#### Stark

```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.44.0.10
	netmask 255.255.255.252
	gateway 10.44.0.9
```

#### Himmel

```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.44.0.14
	netmask 255.255.255.252
	gateway 10.44.0.13

# Static config for eth1
auto eth1
iface eth1 inet static
	address 10.44.2.1
	netmask 255.255.254.0

# Static config for eth2
auto eth2
iface eth2 inet static
	address 10.44.0.129
	netmask 255.255.255.128
```

#### LaubHills

```
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp
```

#### SchwerMountain

```
# DHCP config for eth0
auto eth0
iface eth0 inet dhcp
```

#### Fern

```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.44.0.130
	netmask 255.255.255.128
	gateway 10.44.0.129


# Static config for eth1
auto eth1
iface eth1 inet static
	address 10.44.0.17
	netmask 255.255.255.252

# Static config for eth2
auto eth2
iface eth2 inet static
	address 10.44.0.21
    netmask 255.255.255.252
```

#### Richter

```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.44.0.18
	netmask 255.255.255.252
	gateway 10.44.0.17
```

#### Revolte

```
# Static config for eth0
auto eth0
iface eth0 inet static
	address 10.44.0.22
	netmask 255.255.255.252
	gateway 10.44.0.21
```

Kemudian untuk konfigurasi routingnya (agar dapat mengenal subnets) sebagai berikut

#### Aura

```
route add -net 10.44.4.0 netmask 255.255.252.0 gw 10.44.0.2
route add -net 10.44.8.0 netmask 255.255.248.0 gw 10.44.0.2
route add -net 10.44.0.8 netmask 255.255.255.252 gw 10.44.0.6
route add -net 10.44.0.12 netmask 255.255.255.252 gw 10.44.0.6
route add -net 10.44.2.0 netmask 255.255.254.0 gw 10.44.0.6
route add -net 10.44.0.128 netmask 255.255.255.128 gw 10.44.0.6
route add -net 10.44.0.16 netmask 255.255.255.252 gw 10.44.0.6
route add -net 10.44.0.20 netmask 255.255.255.252 gw 10.44.0.6
```

#### Heiter

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.44.0.1
```

#### Frieren

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.44.0.5
route add -net 10.44.2.0 netmask 255.255.254.0 gw 10.44.0.14
route add -net 10.44.0.128 netmask 255.255.255.128 gw 10.44.0.14
route add -net 10.44.0.16 netmask 255.255.255.252 gw 10.44.0.14
route add -net 10.44.0.20 netmask 255.255.255.252 gw 10.44.0.14
```

#### Himmel

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.44.0.13
route add -net 10.44.0.16 netmask 255.255.255.252 gw 10.44.0.130
route add -net 10.44.0.20 netmask 255.255.255.252 gw 10.44.0.130
```

#### Fern

```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.44.0.129
```

## D, Tugas berikutnya adalah memberikan ip pada subnet SchwerMountain, LaubHills, TurkRegion, dan GrobeForest menggunakan bantuan DHCP.

Karena 4 client itu menggunakan dhcp, maka kita perlu mengkonfigurasi melalui DHCP dari Revolte

Aturlah subnet dhcp pada /etc/dhcp/dhcpd.conf sebagai berikut dengan range dari pembagian IP sebelumnya

```
echo "
subnet 10.44.0.20 netmask 255.255.255.252 {

}


subnet 10.44.4.0 netmask 255.255.252.0 {
        range 10.44.4.3 10.44.6.2;
        option routers 10.44.4.1;
        option broadcast-address 10.44.7.255;
        option domain-name-servers 10.44.0.18;
        default-lease-time 600;
        max-lease-time 7200;
}

subnet 10.44.8.0 netmask 255.255.248.0 {
        range 10.44.8.2 10.44.11.255;
        option routers 10.44.8.1;
        option broadcast-address 10.44.15.255;
        option domain-name-servers 10.44.0.18;
        default-lease-time 600;
        max-lease-time 7200;
}

subnet 10.44.2.0 netmask 255.255.254.0 {
        range 10.44.2.2 10.44.3.0;
        option routers 10.44.2.1;
        option broadcast-address 10.44.3.255;
        option domain-name-servers 10.44.0.18;
        default-lease-time 600;
        max-lease-time 7200;
}

subnet 10.44.0.128 netmask 255.255.255.128 {
        range 10.44.0.131 10.44.0.194;
        option routers 10.44.0.129;
        option broadcast-address 10.44.0.255;
        option domain-name-servers 10.44.0.18;
        default-lease-time 600;
        max-lease-time 7200;
}

"  > /etc/dhcp/dhcpd.conf
```

Penjelasan:

1. Untuk routing dari Revolte
2. Untuk subnet GrobeForest
3. Untuk subnet TurkRegion
4. Untuk subnet LaubHills
5. Untuk subnet SchwerMountain

Dan tidak lupa untuk mengatur interface sebagai berikut (eth0):

```
echo '
# Defaults for isc-dhcp-server (sourced by /etc/init.d/isc-dhcp-server)

# Path to dhcpd'\''s config file (default: /etc/dhcp/dhcpd.conf).
#DHCPDv4_CONF=/etc/dhcp/dhcpd.conf
#DHCPDv6_CONF=/etc/dhcp/dhcpd6.conf

# Path to dhcpd'\''s PID file (default: /var/run/dhcpd.pid).
#DHCPDv4_PID=/var/run/dhcpd.pid
#DHCPDv6_PID=/var/run/dhcpd6.pid

# Additional options to start dhcpd with.
#       Don'\''t use options -cf or -pf here; use DHCPD_CONF/ DHCPD_PID instead
#OPTIONS=""

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
' > /etc/default/isc-dhcp-server
```

Jangan lupa untuk melakukan `service isc-dhcp-server restart`

Kemudian agar Clients mendapatkan IPnya, kita perlu mengatur router di dekat mereka sebagai relay yaitu Fern, Himmel, dan Heiter.

#### Fern, Himmel, dan Heiter

```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start
```

Kemudian melakukan konfigurasi untuk semua port mereka sebagai berikut

```
echo '
# Defaults for isc-dhcp-relay initscript
# sourced by /etc/init.d/isc-dhcp-relay
# installed at /etc/default/isc-dhcp-relay by the maintainer scripts

#
# This is a POSIX shell fragment
#

# What servers should the DHCP relay forward requests to?
SERVERS="10.44.0.22"

# On what interfaces should the DHCP relay (dhrelay) serve DHCP requests?
INTERFACES="eth0 eth1 eth2"

# Additional options that are passed to the DHCP relay daemon?
OPTIONS=""
' > /etc/default/isc-dhcp-relay
echo 'net.ipv4.ip_forward=1' > /etc/sysctl.conf
service isc-dhcp-relay restart
```

melakukan restart pada node clients, dan siap digunakan

### LaubHills

![img](imgs/dhcpLaubHills.png)

### GrobeForest

![img](imgs/dhcpGrobeForest.png)

### TurkRegion

![img](imgs/dhcpTurkRegion.png)

### SchwerMountain

![img](imgs/dhcpSchwerMountain.png)

Terakhir agar memanfaatkan DNS nameserver pada `/etc/resolv.conf` mereka, kita tambahkan konfigurasi pada Ritcher sebagai berikut:

```
apt-get update
apt-get install bind9 -y
echo 'options {
        directory "/var/cache/bind";

        forwarders {
                   192.168.122.1;
          };
        //dnssec-validation auto;
        allow-query{ any; };
        listen-on-v6 { any; };
};' > /etc/bind/named.conf.options

service bind9 restart
```

Penjelasan: forward dari NAT melalui IP DNS
