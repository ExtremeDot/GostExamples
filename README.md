# GostExamples

--------------
### Gost V3 - In Development

[Source Page](https://github.com/go-gost/gost/blob/master/README_en.md)

###### Install Gost V3
```
(https://github.com/go-gost/gost/releases)

```

```
bash <(curl -fsSL https://github.com/go-gost/gost/raw/master/install.sh) --install
```

```
unalias gost
```

-----
### Gost V2

[Source Page](https://github.com/ginuerzh/gost/blob/master/README_en.md)

###### Install Gost V2


* Download Binary file

[Gost V2 - Download Binary Files](https://github.com/ginuerzh/gost/releases)

###### Install V 2.11.5
```
wget https://github.com/ginuerzh/gost/releases/download/v2.11.5/gost-linux-amd64-2.11.5.gz

gunzip gost-linux-amd64-2.11.5.gz && chmod +x gost-linux-amd64-2.11.5

sudo mv gost-linux-amd64-2.11.5 /usr/local/bin/gost

unalias gost

```

  * Build From Source 
```
git clone https://github.com/ginuerzh/gost.git
cd gost/cmd/gost
go build
```
