
CHAIN   |   P2P   | RPC |   GRPC    |   API |   NODE    |   PEERS   
--------|---------|-----|-----------|-------|-----------|-----------
gaia|2010|2011|2012|2013|2011|bf8328b66dceb4987e5cd94430af66045e59899f@public-seed.cosmos.vitwit.com:26656<br />cfd785a4224c7940e9a10f6c1ab24c343e923bec@164.68.107.188:26656<br />d72b3011ed46d783e369fdf8ae2055b99a1e5074@173.249.50.25:26656<br />ba3bacc714817218562f743178228f23678b2873@public-seed-node.cosmoshub.certus.one:26656<br />3c7cad4154967a294b3ba1cc752e40e8779640ad@84.201.128.115:26656<br />366ac852255c3ac8de17e11ae9ec814b8c68bddb@51.15.94.196:26656
regen|2060|2061|2062|2063|2061|
akash|2020|2021|2022|2023|2021|
*juno|2070|2071|2072|2073|2071|
*sifnode|2110|2111|2112|2113|2111|
*anon|2100|2101|2102|2103|2101|
*starname|2050|2051|2052|2053|2051|
*chain-main|2040|2041|2042|2043|2041|
*omniflixhub|2120|2121|2122|2123|2121|
*dig|2090|2091|2092|2093|2091|
*persistencecore|2080|2081|2082|2083|2081|
*osmosis|2000|2001|2002|2003|2001|
*umee|2030|2031|2032|2033|2031|a9a84866786013f75138388fbf12cdfc425bd39c@137.184.69.184:26656<br />684dd9ce7746041d0453322808cc5b238861e386@137.184.65.210:26656<br /> c4c425c66d2941ce4d5d98185aa90d2330de5efd@143.244.166.155:26656<br /> eb42bdbd821fad7bd0048a741237625b4d954d18@143.244.165.138:26656
*ixo|2130|2131|2132|2133|2131|
sentinel|2140|2141|2142|2143|2141|152bad169bfde238d24b8e2403d72c092adc107b@54.169.185.248:26656,57dbef4a8637f4c14dc5f8a4070ff07cc3de8380@13.212.44.171:26656,cb9a308bd21b745ecd58236a08bc60046b06fec3@13.233.250.145:26656,a77f6a094578dad899e2f40e0626b4c6d4705311@3.36.165.232:26656,5f7164bbf0e74bc0b7bc624c631b559bde6d52b4@165.22.65.48:26656,647e54e22cfcdf97b42ada11fcef2f0b5bd81230@35.163.249.152:31358,387027e3b1180d3a619cbbf3462704a490785963@54.176.90.228:26656
*irisnet|2150|2151|2152|2153|2151|
*kusama|2160|2161|2162|2163|2161|
---


# Gaia
```bash
git clone https://github.com/cosmos/gaia.git
cd gaia
make install
gaiad init notional
wget https://github.com/cosmos/mainnet/raw/master/genesis.cosmoshub-4.json.gz
gzip -d genesis.cosmoshub-4.json.gz
mv genesis.cosmoshub-4.json ~/.gaia/config/genesis.json
nano ~/.gaia/config/app.toml # Change the minimum gas price to 2.025uatom
nano /etc/systemd/system/gaia.service # Make a systemd file with variables from above table
systemctl daemon-reload
systemctl enable gaia
systemctl start gaia

```
Till now, there still aren't any errors when starting `gaia`.

# Umee
```bash
git clone https://github.com/umee-network/umee.git
cd umee
make install
umeed init notional
wget -O ~/.umee/config/genesis.json https://raw.githubusercontent.com/umee-network/umee/main/networks/umee-betanet-2/genesis.json
nano /etc/systemd/system/umee.service # Make a systemd file with variables from above table
systemctl daemon-reload
systemctl enable umee
systemctl start umee
```
There is a problem with umee. It can't catch block `ADC5236719318B7E2EE971D14F3302681886A587D395BA83240D15707A2D1696` with this error:
```
panic: Failed to process committed block (2:BF8B7BE0F53486464F40EF58C2704467A8371FC64F5DDA45D46DFBE8230838B8): wrong Block.Header.AppHash.  Expected ADC5236719318B7E2EE971D14F3302681886A587D395BA83240D15707A2D1696, got 65AF964E1763F7259F76C46BFD031E7EB2A3314AE6629662252B61BE762264DE
```
It is often caused by the outdated version of umee. But in this case, umee is setted up to the newest version.

# Regen, Akash
As in the web

# Sentinel
```bash
git clone https://github.com/sentinel-official/hub.git
cd hub
git checkout v0.7.0
make install
sentinelhub init notional --chain-id sentinelhub-2
wget https://github.com/sentinel-official/networks/raw/main/sentinelhub-2/genesis.zip
unzip genesis.zip -d ~/.sentinelhub/config/
nano /etc/systemd/system/sentinel.service # Make a systemd file with variables from above table
systemctl daemon-reload
systemctl enable sentinel
systemctl start sentinel
```
Till now, there still aren't any errors when starting `gaia`.

# Irisnet
```bash
git clone https://github.com/irisnet/irishub.git
cd irishub
make install 
iris init notional --chain-id=irishub-1
curl -o ~/.iris/config/config.toml https://raw.githubusercontent.com/irisnet/mainnet/master/config/config.toml
curl -o ~/.iris/config/genesis.json https://raw.githubusercontent.com/irisnet/mainnet/master/config/genesis.json
nano /etc/systemd/system/iris.service # Make a systemd file with variables from above table
systemctl daemon-reload
systemctl enable iris
systemctl start iris
```
There is a problem with iris:
```
panic: unknown field "pending_htlcs" in types.GenesisState
```