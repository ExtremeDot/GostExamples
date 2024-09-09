### Make a Private IPV6

```
apt install curl -y && bash <(curl -Ls https://raw.githubusercontent.com/Azumi67/PrivateIP_TCP-UDP_Tunnel/main/Private.sh --ipv4)
```

#### Manual Method


```
curl -O https://raw.githubusercontent.com/Azumi67/PrivateIP_TCP-UDP_Tunnel/main/Private.sh
```
```
wget https://raw.githubusercontent.com/Azumi67/PrivateIP_TCP-UDP_Tunnel/main/Private.sh

```
### Replace vlues

```using sed
sed -i 's/fd1d:fc98:b73e:b48/1c7b:b761:c7ae:48d/g' Private.sh

```

```
nano Priavte.sh
```


```
fd1d:fc98:b73e:b48
```

```
1c7b:b761:c7ae:48d
```

### run script

```
bash Private.sh
```


```
ADDRES=https://proof.ovh.net/files/1Gb.dat
```

```
curl --socks5 socks5://localhost:40000 -L $ADDRES > /tmp/test.file
```

```
iFace=
```

```
curl --interface $iFace -L $ADDRES > /tmp/test.file
```

```
port=
```

```
curl --socks5 socks5://localhost:$port myip.wtf/json
```
